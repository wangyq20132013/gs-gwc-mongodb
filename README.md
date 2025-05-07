# GeoServer GWC Mongo 存储扩展插件

## 简介

本项目为 GeoServer 的 GeoWebCache (GWC) 添加了一个 MongoDB 存储扩展，用于将瓦片缓存存储在 MongoDB 数据库中。适用于希望利用 MongoDB 构建可扩展、分布式地图服务的场景。

## 功能特点

- 将 GWC 缓存瓦片数据存储至 MongoDB。
- 支持多图层、多坐标系、多缩放级别的瓦片存储。
- 支持 MongoDB 副本集部署，提高可靠性。
- 可选启用 GridFS 存储模式以支持大尺寸瓦片。
- 与原生 GWC 缓存机制兼容，可无缝集成 GeoServer。

## 依赖环境

- GeoServer 版本：2.14.x 及以上（建议与您的插件版本匹配）
- Java 8 或 11
- MongoDB 4.2+（推荐使用副本集）
- Maven 3.x（用于构建插件）

## 在 geowebcache.xml 中添加 Mongo 存储配置
~~~ xml
<gwcConfiguration>
  ...
  <blobStores>
    <MongoBlobStore>
      <id>mongo-store</id>
      <enabled>true</enabled>
      <default>true</default>
      <mongoURI>mongodb://user:password@host:27017</mongoURI>
      <databaseName>gwc_tiles</databaseName>
      <collectionName>tiles</collectionName>
      <useGridFS>false</useGridFS>
    </MongoBlobStore>
  </blobStores>
  ...
</gwcConfiguration>
~~~
