---
title: "crossover networking"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by thaddeusthudpucker on 2007-10-14
I have a machine that i am soon going to be running the 7.04 server version on. I want to configure it as a fileserver and have it sit by itself, connected only via a crossover cable to a Windows XP machine. All I want to use the ubuntu machine for is overflow of files from my Win XP machine. How can I configure it using ONLY what came on the ubuntu disc? I do not have an internet connection at home, and it looks like i will not have one for some time.

i am fine using filezilla to FTP things back and forth, but i do not know how to configure the ubuntu machine, or if there is a better way.

Thanks in advance!

---

### Post by spd106 on 2007-10-15
You can install Samba then access the Ubuntu machine via Windows Explorer just like any other Windows share.

Start by using the System -> Admin -> Shared Folders utility, you will then likely have to add yourself as a samba user and maybe a few further settings as described in the [wiki]("https://help.ubuntu.com/community/SettingUpSamba").

Also, it would probably be a good idea to set static addresses and then put each of the machines names in the others hosts file. On Ubuntu you can add hosts in the System ->  Admin -> Network utility and Windows probably has something similar in the Control Panel

---

