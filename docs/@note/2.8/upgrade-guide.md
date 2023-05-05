---
title: 📑 Layui 2.8 《升级指南》
toc: false
---
 
# 📑 Layui 2.8 《升级指南》

Layui `2.8` 总体向下兼容，但仍有以下变更需要注意：

1. `2.8` 剔除了 ~~layedit~~ 组件，若是之前用到该组件的，注意采用第三方成熟富文本组件替换，详见：#I5JSE3
1. `2.8` 调整了 `table` 的 `page,limit` 属性，当 `page` 未开启时，则默认不再向后端传递这两个参数
1. `2.8` 调整了 `table` 的特定属性名。序号: `LAY_INDEX` → `LAY_NUM`；下标: `LAY_TABLE_INDEX` → `LAY_INDEX`，若是之前用到这几个特定属性，需更换为新版名称。
1. `2.8` 调整了 `checkbox` 的 `lay-skin` 属性默认为原始风格，原来的标签风格可通过 `lay-skin="tag"` 来设置。
1. `2.8` 调整了 `checkbox` 的私有属性 `lay-text`，采用统一的 `title` 属性替代
1. `2.8` 调整了 `util.fixbar` 的 `showHeight` 属性名称为 `margin`

### 2.7.6 升级到 2.8

`2.8` 对 `2.7.6` 最友好，可直接覆盖升级，只需按照上述提到的几点进行适配即可。

### 2.6.x 升级到 2.8

该跨度相对较大，主要是中间的 `2.6.11` 和 `2.7.x` 的几处调整要适配，包括：

1. **重要**：`2.6.11` 调整了 `laytpl` 的 `{{ d.field }}` 标签的输出为默认开启编码。即与 {{= d.field }} 等同。因此，若输出内容包含 `HTML` 且需要正常渲染的，需采用 `{{- d.field }}` 的标签语句。详细可参考：#I5AXSP
1. `2.6.11` 调整了 `table` 组件的 `escape` 属性默认为 `true`，即默认开启编码功能（之前默认为 `false`）
1. `2.7.5` 调整了 `table` 表头的 `edit` 属性，支持函数写法，且单元格是否编辑不再以 `<td>` 标签上的 `data-edit` 属性为准，而是统一以 `cols` 属性中的 `edit` 属性为准，详细可参考新版文档关于 `edit` 的用法：https://layui.dev/docs/table/#cols.edit

### 2.6.0 以下版本 升级到 2.8

若当前用的版本低于 `2.6.0`，一般不建议升级。但如果非升级不可，除了结合上述提到的变更外，还要重点参考 `2.6.0` 的更新日志中提到的「重要提示」进行适配：https://layui.dev/2.7/docs/base/changelog.html#2.6.0 

同时，还要特别注意，`2.6.0` 之前的版本是按需加载内置组件，从 `2.6.0` 开始，统一构建到 `layui.js` 中。因此，要注意下之前引入的 `JS` 业务代码的放置位置，若是放在 `<head>` 区域，需调整放置到 `<body>` 标签内部的尾端。

### layuiAdmin 主题升级 Layui 到 2.8

主要还是根据当前主题中所用的 Layui 的版本，进行对应的适配，尤其是单页版中的动态模板，需按照前面提到的 `laytpl` 的调整进行修改。具体也可以参考：#I65D80

### 其他细节

若按照以上调整后仍然存在兼容性问题，也可以详细阅读过往所有版本的更新日志：
https://layui.dev/docs/versions.html

或新建 `Issue` 进行详细反馈。

---

<div class="layui-btn-container">
  <a class="layui-btn" href="https://gitee.com/layui/layui/issues/" target="_blank" style="word-spacing: normal;">前往 Issues</a>
  <a class="layui-btn layui-btn-primary" href="../../versions.html#2.8.x">
    <i class="layui-icon layui-icon-left"></i> 更新日志
  </a>
</div>

