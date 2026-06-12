---
title: "No internet connection on install, not even in &quot;try&quot; mode"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by nikola6 on 2013-09-25
Hello,
So I am completely new to linux and I installed it alongside windows 7. The first time I installed it it said I have no connection, but I did it anyways, so the grub menu didn't work.
After that I booted the boot-repair-disk, but it said that I need internet to fix it... It somehow shows 1 connection("Wired Connection 1, connected"), but no reaction when I try to open google,for example.
I am searching solutions 2 days now and I decided to post here. I am also doing all this from bootable USB : ) and on Windows 7 I always have internet, no problems. I hope someone can help me.

---

### Post by dshgna on 2013-09-25
What type of connection do you generally use? Wireless, broadband or ethernet?

---

### Post by nikola6 on 2013-09-25
I am not pretty sure, I am not so familiar with these, but I think it's broadband. I am using cable connection trough a router(supporting 2 computers), provided by my cable TV company(if that helps).

---

### Post by varunendra on 2013-09-25
Hello nikola6, Welcome to the forums ! :)

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us a detailed info about your wireless setup, and also something about the Ethernet interface.

If copy-pasting the contents of the above report here, don't forget to use 'Code' tags. Follow the "Using Code Tags" link in my signature to see how to use it.

---

### Post by nikola6 on 2013-09-25
Very strange... I have internet now, I just booted the boot-repair and I am writing this from my ubuntu Web browser. I have a new problem tho... It's something with the boot-repair

---

### Post by varunendra on 2013-09-25
The script also provides 'some' information about the ethernet interface (wired connection), but if you intend to use 'Only' wired one, please post the outputs of the following -
```
lspci -nnk | grep -iA2 net
nm-tool
sudo ethtool eth0
```
..assuming your wired connection interface is "eth0". If is something else, change it accordingly in the last command.

---

### Post by nikola6 on 2013-09-25
I don't know how, but everything is working properly now, the grub menu, the internet connection, everything. Thanks for trying to help out : )
Finally after 2 days it worked.

---

### Post by varunendra on 2013-09-25
While you have working internet on the system, install ethtool if it is not already installed -
```
sudo apt-get install ethtool
```

It will come handy in case ethernet starts acting again.

---

