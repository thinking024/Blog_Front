# 一、需求分析

## （一）后台

- 登录
- 文章
  - 增删改查
  - 按条件搜索：todo
  - 标签：不要二级标签，不要分类
- 公告
  - 增删改查
- 设置
  - 基本信息
- 友情链接：todo

## （二）前台



# 二、数据库

# （一）数据字典

- article文章

  | 列名                | 数据类型     | 键   | 能否为空 | 是否自增 | 默认值 | 约束   | 备注 |
  | ------------------- | ------------ | ---- | -------- | -------- | ------ | ------ | ---- |
  | article_id          | int          | PM   | NO       | YES      |        |        |      |
  | article_title       | varchar(255) |      |          |          |        | unique |      |
  | article_content     | mediumtext   |      |          |          |        |        |      |
  | article_create_time | datetime     |      |          |          |        |        |      |
  | article_update_time | datetime     |      |          |          |        |        |      |
  | article_status      | varchar(255) |      |          |          |        |        |      |
  | article_view_count  | int          |      |          |          |        |        |      |
  | article_pic_url     | varchar(255) |      |          |          |        |        |      |
  | category_id         | int          | FK   |          |          |        |        |      |



- category文章类别

  | 列名           | 数据类型    | 键   | 能否为空 | 是否自增 | 默认值 | 约束 | 备注     |
  | -------------- | ----------- | ---- | -------- | -------- | ------ | ---- | -------- |
  | category_id    | int         | PK   | NO       | YES      |        |      | 分类id   |
  | category_name  | varchar(50) |      |          |          |        |      | 分类名称 |
  | category_order | int         |      |          |          | 1      |      | 排序值   |
  | category_pid   | int         |      |          |          |        |      | 分类父id |



- notice公告

| 列名               | 数据类型       | 键   | 能否为空 | 是否自增 | 默认值 | 备注     |
| ------------------ | -------------- | ---- | -------- | -------- | ------ | -------- |
| notice_id          | int            | PK   | NO       | YES      |        |          |
| notice_content     | varchar(10000) |      |          |          |        | 公告内容 |
| notice_create_time | datetime       |      |          |          |        | 创建时间 |
| notice_order       | int            |      |          |          |        | 排序值   |
| notice_status      | int            |      |          |          | 1      | 状态     |
| notice_title       | varchar(255)   |      |          |          |        | 标题     |
| notice_update_time | datetime       |      |          |          |        | 更新时间 |



- user用户

| 列名                 | 数据类型     | 键   | 能否为空 | 是否自增       | 默认值 | 备注         |
| -------------------- | ------------ | ---- | -------- | -------------- | ------ | ------------ |
| user_id              | int          | PK   | NO       | auto_increment |        | 用户id       |
| user_pass            | varchar(255) |      | NO       |                |        | 用户密码     |
| user_last_login_ip   | varchar(255) |      |          |                |        | 最后登录ip   |
| user_last_login_time | datetime     |      |          |                |        | 最后登录时间 |





# api文档

## 首页请求公告

- get请求  /notice/getIndexNotice

- 请求参数：无
- 返回示例

```json
"code": 100,
"msg": "success",
"data": [
    {
        "noticeId": 1,
        "noticeTitle": "notice",
        "noticeOrder": 1
    }
]
```



## 获取顶部菜单栏类别

- get   /category/getCategories
- 请求参数：无
- 返回示例

```json
{
    "code": 100,
    "msg": "success",
    "data": [
        {
            "categoryId": 1,
            "categoryName": "parent",
            "childern": [
                {
                    "categoryId": 1,
                    "categoryName": "child"
                },
                {
                    "categoryId": 1,
                    "categoryName": "child2"
                }
            ]
        },
        {
            "categoryId": 2,
            "categoryName": "parent2",
            "childern": [
                {
                    "categoryId": 1,
                    "categoryName": "child1"
                },
                {
                    "categoryId": 1,
                    "categoryName": "child2"
                }
            ]
        }
    ]
}

```



## 获取热门文章

- get /article/getHot
- 请求参数：无
- 返回示例

```json
{
    "code": 100,
    "msg": "success",
    "data": [
        {
            "articleId": 1,
            "articleName": "parent",
            "articlePicUrl": "/"
        }
    ]
}
```





# 获取站点基本信息

- get /info/getInfo
- 请求参数：无
- 返回示例

```json
```

