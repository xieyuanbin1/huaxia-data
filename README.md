# haxia-data

这里是分类数据

## 数据格式说明

| 序号    | 字段           | 数据类型     | 是否必须 | 说明                                            |
|-------|--------------|----------|------|-----------------------------------------------|
| 1     | title        | object   | O    | 主幻灯片，见 `Slide`                                |                                                                                                                                      |
| 2     | events       | object[] | M    | 幻灯片列表，见 `Slide`                               |
| 3     | eras         | object[] | M    | 用于在时间轴导航组件上标注时间跨度，见 `Eras`                    |
| 4     | scale        | string   | M    | `human`、`cosmological` 人类时间线或宇宙时间线，默认 `human` |


## Slide 格式
| 序号  | 字段           | 数据类型     | 是否必须 | 说明                                                                                                                                                         |
|-----|--------------|----------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1   | start_date   | object   | M    | 整个时间线的开始时间，见 `Date`                                                                                                                                        |
| 2   | end_date     | object   | M    | 整个时间线的结束时间，见 `Date`                                                                                                                                        |
| 3   | text         | object   | O    | 幻灯片描述信息，见 `Text`                                                                                                                                           |
| 4   | media        | object   | O    | 幻灯片中的媒体对象，见 `Media`                                                                                                                                        |
| 5   | group        | string   | O    | 任何文本。如果存在，时间轴会将具有相同组值的事件组织在同一行或相邻行中，与其他组中的事件分开。组的共同值将作为标签显示在导航左侧边缘                                                                                         |
| 6   | display_date | string   | O    | 一个字符串，在 Timeline 显示日期时使用。如果使用，则会覆盖在此事件的开始或结束日期上设置的 display_date 值，这对控制两个日期之间的关系非常有用                                                                        |
| 7   | background   | object   | O    | 背景                                                                                                                                                         |
| 7.1 | url          | string   | O    | 用作背景的图片的完整 URL                                                                                                                                             |
| 7.2 | alt          | string   | O    | 描述 url 属性提供的图像的替代文本                                                                                                                                        |
| 7.3 | color        | number   | O    | 以十六进制表示的 CSS 颜色（如 #0f9bd1）或有效的 CSS 颜色关键字                                                                                                                   |
| 8   | autolink     | boolean  | O    | 默认为 `true`，这意味着时间线将扫描文本字段并自动添加 `<a>` 标记，使链接和电子邮件地址 `可点击`。如果设置为 `false`，在需要链接时，仍可在相应字段中手动应用标记。自动链接适用于文本对象中的文本字段以及媒体对象中的标题和字幕字段                              |
| 9   | unique_id    | string   | O    | 一个字符串值，在时间轴中的所有幻灯片中都是唯一的。如果未指定，TimelineJS 将根据标题构建一个 ID，但如果以后编辑标题，ID 就会改变。唯一 ID 在使用 `hash_bookmark` 选项时使用，也可与 `timeline.goToId()` 方法一起使用，以编程方式将时间线移动到特定幻灯片  |


## Eras 格式
| 序号 | 字段              | 数据类型   | 是否必须 | 说明        |
|----|-----------------|--------|------|-----------|
| 1  | start_date      | object | M    | 见 `Date`  |
| 2  | end_date        | object | M    | 见 `Date`  |
| 3  | text            | object | O    | 可选，但建议使用  |


## Date 格式
| 序号 | 字段           | 数据类型   | 是否必须 | 说明            |
|----|--------------|--------|------|---------------|
| 1  | year         | number | M    | 年             |
| 2  | month        | number | O    | 月             |
| 3  | day          | number | O    | 日             |
| 4  | hour         | number | O    | 小时, 0-23      |
| 5  | minute       | number | O    | 分钟, 0-59      |
| 6  | second       | number | O    | 秒, 0-59       |
| 7  | millisecond  | number | O    | 毫秒            |
| 8  | display_date | string | O    | 不清楚具体用法, 暂时不用 |
| 9  | format       | string | O    | 格式化日期字符串      |

## Text 格式
| 序号 | 字段          | 数据类型   | 是否必须 | 说明                        |
|----|-------------|--------|------|---------------------------|
| 1  | headline    | string | O    | 标题，任何文本，包括 `HTML` 或空白文本   |
| 2  | text        | string | O    | 描述信息，任何文本，包括 `HTML` 或空白文本 |

## Media 格式
| 序号 | 字段           | 数据类型   | 是否必须 | 说明                                  |
|----|--------------|--------|------|-------------------------------------|
| 1  | url          | string | M    | 大多数情况下是媒体的 URL                      |
| 2  | caption      | string | O    | 说明信息，任何文本，包括 `HTML` 标记也是可以的         |
| 3  | credit       | string | O    | 不知道是什么，任何文本，包括 `HTML` 标记也是可以的       |
| 4  | thumbnail    | string | O    | 缩略图                                 |
| 5  | alt          | string | O    | 图片的 `alt` 标签。如果没有提供，将使用标题（如果有的话）    |
| 6  | alt          | string | O    | 图片标题                                |
| 7  | link         | string | O    | 可选 URL，作为使用 `<a>` 标记包装媒体的 href      |
| 8  | link_target  | string | O    | 如果使用，可选择与链接关联的目标                    |
