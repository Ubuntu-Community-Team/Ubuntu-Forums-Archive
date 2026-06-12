---
title: "No entry for synaptics touchpad in /etc/X11/xorg.conf"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by bhargava470 on 2009-05-06
Hi,
I recently installed Ubuntu 9.04. I wanted to disable the touchpad using the command line, but it says "SHMConfig disabled?"  to make SHMConfig "on" addition in the /etc/X11/xorg.conf , I found there was no entry for the touchpad in the file. Though I was able to disable the touchpad using the system->preference->mouse , but no entry in the file !!!!!!!!! so is ubuntu properly installed or can i know what the problem is ???? 
Any suggestion in this regard is greatly appreciated.

Thanks
--
Bhargava

---

### Post by mick8985 on 2009-05-06
There is no need to have an entry for your touchpad in the xorg.conf file anymore. In a 9.04 install you should find that xorg.conf is pretty baron.
I don't quite understand what your problem is, do you want your touchpad enabled or disabled?

---

### Post by kpkeerthi on 2009-05-06
Recent xorg-server uses hotplug to discover input devices dynamically and that's why xorg.conf is mostly empty.

See: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig")

---

### Post by bhargava470 on 2009-05-07
Thanks [kpkeerthi]("http://ubuntuforums.org/member.php?u=123376") that was helpful

---

