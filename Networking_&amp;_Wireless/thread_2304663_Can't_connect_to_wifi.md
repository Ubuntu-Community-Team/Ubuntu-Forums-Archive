---
title: "Can't connect to wifi"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by sean108 on 2015-11-28
Hi so I'm new to Ubuntu and for whatever reason I was only able to connect to my wifi for a couple minutes after I installed Ubuntu. Being as I'm new to Ubuntu I really have no clue where to start. I can connect just fine with PS3 and iPhone. I'm using an hp pavilion 500-424. Any help would be greatly appreciated.

---

### Post by tridentlead on 2015-11-29
Try installing any proprietary drivers for your system by running:
```

sudo ubuntu-drivers autoinstall

```
for a more detailed explanation read my post here [http://ubuntuforums.org/showthread.php?t=2304664&p=13398528#post13398528](http://ubuntuforums.org/showthread.php?t=2304664&p=13398528#post13398528)

---

### Post by Bucky Ball on 2015-11-29
Welcome. 

[QUOTE=Daniel_Stutman]Try installing any proprietary drivers for your system by running:
Code:

```
sudo ubuntu-drivers autoinstall
```[/QUOTE]

If your system is running fine and your only problem is wifi, do not do this. There is no point in installing every proprietary driver available and it may not fix your issue anyway. It could possibly cause a few, though.

Please open a terminal and paste this in:

```
sudo lshw -C network
```

Hit return. You will be asked for your password. When you type it, it will be invisible. This is normal.

Copy/paste the output here, please. Please use code tags (see the last link in my signature).

* PS: Just thought of something. Sounds like you can't get online at all with this machine. You can't get online with a cable? It would make your job a lot easier. Posting the output of the command I've given is going to be difficult but you could copy it to a text file, drop it to your phone, copy it to a post here. ;)

@Daniel_Stutman: Your link is to a thread concerning graphics/sound issues. Nothing to do with wifi. :)

---

