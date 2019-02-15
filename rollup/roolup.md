## roolup.js 内容梳理

### init安装
```npm install --global rollu```

### 命令压缩模式（同时可以配置config文件）
```rollup src/main.js -f cjs```

### 常用配置项
* 核心选项   
input  
external  
plugins  
* 额外选项
onwarn  
acorn  
context  
moduleContext  
legacy  

* *output*（重点，以下均为output下字段）  
  file
  format  
  name  
  globals  

  paths  
  banner  
  footer  
  intro  
  outro  
  sourcemap  
  sourcemapFile  
  interop  
  exports  
  amd  
  indent  
  strict  


### 重要插件
#### rollup-plugin-node-resolve（告诉 Rollup 如何查找外部模块）
```
import resolve from 'rollup-plugin-node-resolve';  
export default {
  input: 'src/main.js',
  output: {
    file: 'bundle.js',
    format: 'cjs'
  },
  plugins: [ resolve() ]
};
```

#### rollup-plugin-commonjs（将 CommonJS 转换成 ES2015 模块的）

#### rollup-plugin-babel
```
// rollup.config.js
import resolve from 'rollup-plugin-node-resolve';
import babel from 'rollup-plugin-babel';

export default {
  input: 'src/main.js',
  output: {
    file: 'bundle.js',
    format: 'cjs'
  },
  plugins: [
    resolve(),
    babel({
      exclude: 'node_modules/**' // 只编译我们的源代码
    })
  ]
};
```

