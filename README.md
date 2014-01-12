sersync
=======

Synchronize files and folders between servers -using inotiy and rsync with c++

Introduce

sersync主要用于服务器同步，web镜像等功能。基于boost1.43.0,inotify api,rsync command.开发。目前使用的比较多的同步解决方案是inotify-tools+rsync ，另外一个是google开源项目Openduckbill（依赖于inotify- tools），这两个都是基于脚本语言编写的。相比较上面两个项目，本项目优点是：
sersync是使用c++编写，而且对linux系统文件系统产生的临时文件和重复的文件操作进行过滤（详细见附录，这个过滤脚本程序没有实现），所以在结合rsync同步的时候，节省了运行时耗和网络资源。因此更快。
相比较上面两个项目，sersync配置起来很简单，其中bin目录下已经有基本上静态编译的2进制文件，配合bin目录下的xml配置文件直接使用即可。
另外本项目相比较其他脚本开源项目，使用多线程进行同步，尤其在同步较大文件时，能够保证多个服务器实时保持同步状态。
本项目有出错处理机制，通过失败队列对出错的文件重新同步，如果仍旧失败，则按设定时长对同步失败的文件重新同步。
本项目自带crontab功能，只需在xml配置文件中开启，即可按您的要求，隔一段时间整体同步一次。无需再额外配置crontab功能。
本项目socket与http插件扩展，满足您二次开发的需要。
欢迎参与讨论，持续更新中.thank you!
感谢 xoyo 组长宴哥(s135)和 好友吴浩(terry),对本项目开发过程中的指导与帮助。
