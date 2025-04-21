# 简介



# 接口概览

| 接口                     | 对应平台及关键字段 | 每次调用消耗token数  |响应数据 | 接口超时时间 |
| ------------------------ | ------------------ |   -------- |-------- | ------------ |
| /get_notes | 笔记详情                  | 20 token/次                 | 秒级 | 无       | 
| /get_comments| 笔记评论                  | 20 token/次                 | 秒级 | 无       | 
| /get_sub_comments | 笔记子评论                  | 20 token/次                 | 秒级 | 无       | 
| /get_search | 笔记搜索                  | 60 token/次                 | 秒级 | 无       |
| /get_user_info | 用户详情                  | 50 token/次                 | 秒级 | 无       |
| /get_user_note | 用户发布笔记列表                  | 40 token/次                 | 秒级 | 无       | 
| /get_tag_notes | 话题笔记列表                  | 20 token/次                 | 秒级 | 无       | 



# 价格

按次收费。





# 接口文档

## 服务器地址
联系作者获取

## 公共请求头(header)
所有接口都一样
```json
{
  //  联系作者获取token。
  "Authorization": "0xOseNAwOYjtI9hTUvkBAoNZAOpLlMPD",
 
}
```

## 1. GET /get_notes 笔记详情接口 

> 金额：0.01

> param:

| 参数         | 类型	| 含义         | 是否必须 |
| ------------ | ------|--------------------- | -------- |
|   noteId  | string |   笔记id    | 必须|

> 返回:

| 参数         | 类型	| 含义         |
| ------------ | ------|--------------------- |
|   code  | string |    状态码   |
|   msg  | string |    状态说明   |
|   balance  | string |    余额   |
|   data  | string |    小红书官方接口返回   |

## 2. GET /get_comments 笔记评论接口

> 金额：0.01

> param:

| 参数         | 类型	| 含义         | 是否必须 |
| ------------ | ------|--------------------- | -------- |
|   noteId  | string |   笔记id    | 必须|
|   start  | string |      翻页，上一次请求最后一条评论的id。不传默认请求第一页。 | 非必需|
|   sort_comment  | string |      1：默认排序，2：最新评论排序 | 非必需|

> 返回:

| 参数         | 类型	| 含义         |
| ------------ | ------|--------------------- |
|   code  | string |    状态码   |
|   msg  | string |    状态说明   |
|   balance  | string |    余额   |
|   data  | string |    小红书官方接口返回   |

## 3. GET /get_sub_comments  笔记子评论接口

> 金额：0.01

> param:

| 参数         | 类型	| 含义         | 是否必须 |
| ------------ | ------|--------------------- | -------- |
|   noteId  | string |   笔记id    | 必须|
|   commentId  | string |   一级评论id（要请求哪条评论的子评论）    | 必须|
|   start  | string |      翻页，上一次请求最后一条评论的id。不传默认请求第一页。 | 非必需|

> 返回:

| 参数         | 类型	| 含义         |
| ------------ | ------|--------------------- |
|   code  | string |    状态码   |
|   msg  | string |    状态说明   |
|   balance  | string |    余额   |
|   data  | string |    小红书官方接口返回   |

## 4. GET /get_search 笔记搜索接口

金额：0.05

> param:

| 参数         | 类型	| 含义         | 是否必须 |
| ------------ | ------|--------------------- | -------- |
| keyword    | string  |     要搜索的关键字  |  必须|
| page    | integer  |     第几页，从0开始  |  必须|
| searchId    | string  |   第一次请求可不传，服务端会生成searchId。 翻页时建议携带服务端返回的searchId。多个关键字不要复用searchId。    |  非必须|
| sessionId    | string  |    第一次请求可不传，服务端会生成sessionId。 翻页时建议携带服务端返回的sessionId。   |  非必须|
| sort_type    | string  |    笔记排序规则 默认值：general 可选值：综合：general、最新：time_descending、最多点赞：popularity_descending、最多评论：comment_descending、最多收藏：collect_descending   |  非必须|
| filter_type    | string  |   筛选笔记类型 默认值：不限 可选值：视频笔记、普通笔记    |  非必须|
| filter_time    | string  |    筛选笔记发布时间 默认值：不限 可选值：一天内、一周内、半年内   |  非必须|
| filter_range    | string  |   筛选笔记搜索范围 默认值：不限 可选值：已看过、未看过、已关注    |  非必须|
| filter_screening    | string  |   筛选标签，可以更精细的搜索,标签可以通过/get_search_filter获取，传入get_search_filter获取到的searchId和关键字。比如:旅游    |  非必须|

> 返回:

| 参数         | 类型	| 含义         |
| ------------ | ------|--------------------- |
|   code  | string |    状态码   |
|   msg  | string |    状态说明   |
|   searchId  | string |    用于翻页   |
|   sessionId  | string |    用于翻页   |
|   balance  | string |    余额   |
|   data  | string |    小红书官方接口返回   |




## 5. GET /get_user_info 用户详情接口

金额：0.04

> param:

| 参数         | 类型	| 含义         | 是否必须 |
| ------------ | ------|--------------------- | -------- |
|  userId   | string |   用户id    | 必须 |

> 返回:

| 参数         | 类型	| 含义         |
| ------------ | ------|--------------------- |
|   code  | string |    状态码   |
|   msg  | string |    状态说明   |
|   balance  | string |    余额   |
|   data  | string |    小红书官方接口返回   |



## 6. GET /get_user_note  用户笔记列表
金额：0.04

> param:

| 参数         | 类型	| 含义         | 是否必须 |
| ------------ | ------|--------------------- | -------- |
|   userId  | string |    用户id   | 必须 |
|   cursor  | string |    用于翻页，上一次请求到的最后一条作品id。 不传默认请求第一页。   | 非必须 |

> 返回:

| 参数         | 类型	| 含义         |
| ------------ | ------|--------------------- |
|   code  | string |    状态码   |
|   msg  | string |    状态说明   |
|   balance  | string |    余额   |
|   data  | string |    小红书官方接口返回   |



## 7. GET /get_tag_notes 话题标签笔记列表

金额：0.05

> param:

| 参数         | 类型	| 含义         | 是否必须 |
| ------------ | ------|--------------------- | -------- |
|   pageId  | string |   标签id    | 必须 |
|   first_load_time  | string |   首次请求的时间，毫秒级时间戳    | 必须 |
|   sort  | string |   排序 默认值：hot（综合） 可选值：hot（综合）、time（最新）、trend（最热）    | 非必须 |
|   session_id  | string |   首次不要传，由服务端生成。 翻页传。    | 非必须 |
|   last_note_ct  | string |   首次不传。翻页传上一次请求返回的最后一条笔记create_time字段    | 非必须 |
|   last_note_id  | string |   首次不传。翻页传上一次请求返回的最后一条笔记id    | 非必须 |
|   cursor_score  | string |   首次不传。翻页传上一次请求返回的最后一条笔记cursor_score字段    | 非必须 |

> 返回:

| 参数         | 类型	| 含义         |
| ------------ | ------|--------------------- |
|   code  | string |    状态码   |
|   msg  | string |    状态说明   |
|   balance  | string |    余额   |
|   data  | string |    小红书官方接口返回   |


## 8. GET /get_search_filter  搜索标签列表
金额：0.05

> param:

| 参数         | 类型	| 含义         | 是否必须 |
| ------------ | ------|--------------------- | -------- |
|   userId  | string |    用户id   | 必须 |
|   cursor  | string |    用于翻页，上一次请求到的最后一条作品id。 不传默认请求第一页。   | 非必须 |

> 返回:
| 参数         | 类型	| 含义         |
| ------------ | ------|--------------------- |
|   code  | string |    状态码   |
|   msg  | string |    状态说明   |
|   balance  | string |    余额   |
|   searchId  | string |    可以用于搜索   |
|   data  | string |    小红书官方接口返回   |




 

