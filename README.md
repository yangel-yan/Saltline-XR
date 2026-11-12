# 断讯港 · SALTLINE XR

面向 PICO Swan 头显与双手柄的港区第一人称射击游戏。切断三处通信中继后登船撤离，或在生存模式中迎战连续波次。

本仓库是 Unity 6000.3.25f1 导出的独立 Android Gradle 工程，包含预编译 ARM64 IL2CPP 运行库。包名为 `com.yangel.saltline`，首次发布版本为 `V1.0.0`。采用无 HDR 的 LDR 画面。

## 玩法

- PAC-9 步枪与 PAC-4 手枪，包含换弹手部动画、双臂 IK、后坐力、子弹和弹着反馈。
- 任务与生存模式，标准、困难、残酷三档难度。
- 地面机械、空中敌人与可连锁引爆的场景爆炸物。
- 中文空间菜单、目标标记与腕部状态界面。

| Swan 操作 | 功能 |
| --- | --- |
| 左摇杆 | 移动；按下冲刺 |
| 右摇杆 | 分段转向 |
| 右扳机 | 射击 |
| 右侧握把 Grip | 瞄准 |
| 左 X | 切换武器 |
| 右 B | 换弹 |
| 右 A | 跳跃 |
| 左扳机 | 操作中继 |
| 左菜单 / Y | 暂停 |

## 构建

需要 JDK 17、Android SDK 36 / Build Tools 36、NDK 27.2.12479018，以及可访问公开 Maven 仓库的网络。NDK 应安装在 Android SDK 的 `ndk/27.2.12479018` 下，用于原生库打包处理。配置 `JAVA_HOME` 和 `ANDROID_HOME` 后执行：

```powershell
.\gradlew.bat --no-daemon assembleRelease
```

macOS / Linux：

```sh
./gradlew --no-daemon assembleRelease
```

输出为 `launcher/build/outputs/apk/release/launcher-release.apk`。Gradle Wrapper 使用 9.3.1，Android Gradle Plugin 使用 9.0.0。原生库已预编译，`buildIl2Cpp` 任务保持禁用；修改 C# 玩法需要从原 Unity 工程重新导出。

发布配置为 `vibelab.yaml`。`.vibelab/` 是本地发布状态，根目录 `assets/` 是本地上传素材，均不提交 Git。仓库不包含本机 SDK 路径或签名密钥。

## 参考与许可

玩法和港区视觉参考用户提供的 [SALTLINE 原作](https://claude.ai/artifact/BGY1SztrAYcJQHSsnHHGmp)，并适配立体视角与 Swan 手柄。

新增中文标题补字使用 Noto Sans SC；SIL Open Font License 随包保存在 `unityLibrary/src/main/assets/licenses/NotoSansSC-OFL.txt`。其他随附运行库保留各自原有许可。
