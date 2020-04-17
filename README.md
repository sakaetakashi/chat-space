# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

- Ruby version

- System dependencies

- Configuration

- Database creation

- Database initialization

- How to run the test suite

- Services (job queues, cache servers, search engines, etc.)

- Deployment instructions

- ...

# DB 設計

**users table**
| Column | type | Option |
|:--|:--|:---|
| name | string | index: true, null: false, unique: true |
| mail | string | null: false, unipue: true |
**Association**

- has_many :groups, through: :group_users
- has_many :group_users
- has_many :massages

---

**groups table**
| Column | type | Option |
|:--|:--|:--|
| name | string | index: true, null: false, unipue: true |
**Association**

- has_many :users, through: :group_users
- has_many :group_users
- has_many :messages

---

**message table**
| Column | type | Option |
|:--|:--|:--|
| body | text | |
| image | string | |
| group_id | references | foreign_key: true |
| user_id | references | foreign_key: true |
**Association**

- belongs_to :user
- belongs_to :group

---

**group_users table**
| Column | type | Option |
|:--|:--|:--|
| group | references | index: true, foreign_key: true, null: false |
| user | references | index: true, foreign_key: true, null: false |
**Association**

- belongs_to :group
- belongs_to :user

---
