# DB設計

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|index: true, null: false, unique: true|
|email|string|null: false, unique: true|

### Association
- has_many :groups, through: :memebers
- has_many :messages
- has_many :members


## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
|body|text|
|image|string|

### Association
- belongs_to :group
- belongs_to :user

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|string|null: false, unique: true|

### Association
- has_many :users, through: :memebers
- has_many :messages
- has_many :members

