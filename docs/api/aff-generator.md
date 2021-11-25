---
title: arcfutil.aff.generator
language: zh-CN
---

# `arcfutil.aff.generator`

aff片段生成函数。

## `arc_animation_assist()`

逐帧动画辅助工具。

### 原型

`arcfutil.aff.generator.arc_sample.arc_animation_assist(...) -> NoteGroup`

### 参数

|参数名|类型|说明|默认值|
|--|--|--|--|
|arc|Arc|要变换的Arc|
|start_t|int|动画开始时间点|
|stop_t|int|动画结束时间点|
|delta_x|float|x轴位移量|
|delta_y|float|y轴位移量|
|basebpm|float|基准BPM|
|easing_x|str|x轴位移缓动，可选`b|s|si|so`|s|
|easing_b_point_x|list|x轴贝塞尔缓动曲线，easing_x的值为`b`时生效|[1/3, 0, 2/3, 1]|
|easing_y|str|y轴位移缓动，可选`b|s|si|so`|s|
|easing_b_point_y|list|y轴贝塞尔缓动曲线，easing_y的值为`b`时生效|[1/3, 0, 2/3, 1]|
|infbpm|float|极大值BPM|999999|
|framerate|float|帧率|60|
|fake_note_t|float|100000|假Note时间偏移量|
|offset_t|int|动画整体时间偏移，影响物件z轴距离|0|
|delta_offset_t||动画整体时间偏移变化量，可产生z轴位移|0|
|easing_offset_t|str|z轴位移缓动，可选`b|s|si|so`|s|
|easing_b_point_offset_t|list|z轴贝塞尔缓动曲线，easing_offset_t的值为`b`时生效|[1/3, 0, 2/3, 1]|

### 返回值

`(NoteGroup)` 生成的Note。

## `arc_crease_line()`

生成折线Arc。

### 原型

`arcfutil.aff.generator.arc_sample.arc_crease_line(...) -> NoteGroup`

### 参数

|参数名|类型|说明|默认值|
|--|--|--|--|
|base|Arc|基线|
|x_range|float|x轴变动范围|
|y_range|float|y轴变动范围|
|count|int|切分数量|
|mode|str|模式，`m`以基线为中线，`b`以基线为边线|m|
|easing|str|生成Arc的缓动类型|s|

### 返回值

`(NoteGroup)` 生成的Note。

## `arc_rain()`

生成下雨黑线。

### 原型

`arcfutil.aff.generator.arc_sample.arc_rain(...) -> NoteGroup`

### 参数

|参数名|类型|说明|默认值|
|--|--|--|--|
|original_t|int|下雨起始时间|
|dest_t|int|下雨结束时间|
|step|float|雨点起始点之间的间隔|
|length|float|雨点的长度，`None`则表示充满间隔|None|

### 返回值

`(NoteGroup)` 生成的Note。

## `arc_slice_by_count()`

将Arc切分为固定段数。

### 原型

`arcfutil.aff.generator.arc_sample.arc_slice_by_count(...) -> NoteGroup`

### 参数

|参数名|类型|说明|默认值|
|--|--|--|--|
|arc|Arc|要切分的Arc|
|count|切分数量||
|start|int|切分起始点，`None`表示不指定|None|
|stop|int|切分终点，`None`表示不指定|None|

### 返回值

`(NoteGroup)` 生成的Note。

## `arc_slice_by_timing()`

以Timing组为基准切分Arc。

### 原型

`arcfutil.aff.generator.arc_sample.arc_slice_by_timing(...) -> NoteGroup`

### 参数

|参数名|类型|说明|默认值|
|--|--|--|--|
|arc|Arc|要切分的Arc|
|timings|Iterable|作为切分基准的Timing组|

### 返回值

`(NoteGroup)` 生成的Note。

## `timing_easing()`

生成平缓变化的Timing。

### 原型

`arcfutil.aff.generator.timing_sample.timing_easing(...) -> NoteGroup`

### 参数

|参数名|类型|说明|默认值|
|--|--|--|--|
|origin_t|int|效果起始时间|
|dest_t|int|效果结束时间|
|origin_bpm|float|起始BPM|
|dest_bpm|float|目标BPM|
|count|int|Timing数量|
|bar|float|小节线数值|4.00|
|mode||缓动模式，可选`b|s|si|so`|s|
|b_point|list|贝塞尔缓动曲线，mode的值为`b`时生效|[1/3, 0, 2/3, 1]|

### 返回值

`(NoteGroup)` 生成的Note。

## `timing_easing_linear()`

::: warning 注意
这个方法已被废弃。请使用[`aff.generator.timing_easing()`](#timing-easing)代替。
:::

生成线性变化的Timing。

### 原型

`arcfutil.aff.generator.timing_sample.timing_easing_linear(...) -> NoteGroup`

### 参数

|参数名|类型|说明|默认值|
|--|--|--|--|
|origin_t|int|效果起始时间|
|dest_t|int|效果结束时间|
|origin_bpm|float|起始BPM|
|dest_bpm|float|目标BPM|
|count|int|Timing数量|
|bar|float|小节线数值|4.00|

### 返回值

`(NoteGroup)` 生成的Note。

## `timing_glitch()`

生成原地抖动的Timing。

### 原型

`arcfutil.aff.generator.timing_sample.timing_glitch(...) -> NoteGroup`

### 参数

|参数名|类型|说明|默认值|
|--|--|--|--|
|origin_t|int|效果起始时间|
|dest_t|int|效果结束时间|
|count|int|Timing数量|
|bpm_range|float|BPM变化范围|
|exact_bar|float|BPM变化极值时的小节线数值|4.00|
|zero_bar|float|BPM为零值时的小节线数值|4.00|

### 返回值

`(NoteGroup)` 生成的Note。

