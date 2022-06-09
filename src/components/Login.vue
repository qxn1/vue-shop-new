<template>
  <div class="login_container">
    <div class="login_box">
      <!-- 表单区域 -->
      <el-form
        ref="ref"
        :model="loginForm"
        :rules="rules"
        label-width="0px"
        class="login_from"
      >
        <!-- 用户名 -->
        <el-form-item prop="username">
          <el-input
            v-model="loginForm.username"
            prefix-icon="el-icon-user-solid"
          ></el-input>
        </el-form-item>
        <!-- 密码 -->
        <el-form-item prop="password">
          <el-input
            v-model="loginForm.password"
            prefix-icon="el-icon-goods"
            type="password"
          ></el-input>
        </el-form-item>
        <!-- 按钮 -->
        <el-form-item class="btns">
          <el-button
            type="primary"
            @click="login"
          >登录</el-button>
          <el-button
            type="info"
            @click="reset"
          >重置</el-button>
        </el-form-item>

      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      //登录表单的数据绑定对象
      loginForm: {
        username: 'admin',
        password: '123'
      },
      // 表单的验证规则对象
      rules: {
        username: [
          { required: true, message: '请输入名称', trigger: 'blur' },
          { min: 2, max: 9, message: '长度在 2 到 9 个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 2, max: 9, message: '长度在 2 到 9 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    // 重置表单
    reset() {
      this.$refs.ref.resetFields()
    },
    //表单预验证
    login() {
      this.$message.success('登录成功')
      this.$router.push('/home')
    }
    //   this.$refs.ref.validate(async valid => {
    //     //  console.log(valid)
    //     if (!valid) return
    //const result = await this.$http.post('login', this.loginForm)
    //console.log(result)
    //   })
  }
}
</script>

<style lang="less" scoped>
.login_container {
  background-color: #2b4b6b;
  height: 100%;
}
.login_box {
  width: 450px;
  height: 300px;
  background-color: #fff;
  border-radius: 3px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.btns {
  display: flex;
  justify-content: flex-end;
}
.login_from {
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 0 20px;
  box-sizing: border-box;
}
</style>