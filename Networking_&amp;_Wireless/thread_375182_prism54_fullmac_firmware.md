---
title: "prism54 fullmac firmware"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by cr4z3d on 2007-03-03
Does ubuntu edgy come with the prism54 firmware? or do I have to install that myself? I have a netgear wg511v1 and trying to figure out if i actually need the firmware. The card works fine after just installing ubuntu but no support for WPA it seems. Tried following the WPA sticky but that didn't help much.

---

### Post by chili555 on 2007-03-03
Yes it does. after a sudo updatedb, locate firmware | grep isl

I found my WG511 v.1 to work, mostly but occasionally it would hang with the little yellow LED blazing. I Googled for the kernel message it threw up and no one seemed to have a fix, Ubuntu or otherwise.

I finally installed ndiswrapper and blacklisted prism54. It works perfectly now. I don't know about WPA, I use WEP.

If you need the WG511ICB.sys you need to get ndiswrapper going, I will be happy to help you extract it.

---

### Post by cr4z3d on 2007-03-03
Alright, thanks for the quick reply. I'm going to try the update now and if that doesn't work I'm going to need help extracting the .sys file for ndiswrapper. I guess i could install it on my windows machine.. but i really don't want to have random drivers and netgear crap laying around. So yeah if you know a way to do it in ubuntu that would be very helpful

---

### Post by cr4z3d on 2007-03-03
Still no luck getting WPA to work. I guess I have to go with ndiswrapper. Where can I get the .sys file? I downloaded the file from netgear but it's a .exe (i got version 3)

---

### Post by chili555 on 2007-03-03
Alrighty, then!

Open a terminal and ```
wget ftp://downloads.netgear.com/files/wg511v300.zip
unzip wg511v300.zip
```
A folder will be created in your /home/username called WG511v300
```
cd WG511v300
```
You will need cabextract and unshield. If you do not have them ```
sudo apt-get install cabextract unshield
cabextract WG511v300.exe
cd Disk1
unshield x data1.cab
cd Driver_xp_File_Group
ls -l
```

And there is WG511ICB.inf! Strictly for my own convenience, instead of drilling down through all those folders, I ```
cp /home/username/WG511v300/Disk1/Driver_xp_File_Group/WG511ICB.inf /home/username 
``` Then the relevant .inf is in my /home/username, rather than 58 layers down. Easier to find.

---

### Post by cr4z3d on 2007-03-03
Thanks! Only problem I ran into was with unshield. says command not found. So I installed it with apt-get no problem. Only question I have is for blacklisting prism. What exactly do I do for that?

---

### Post by chili555 on 2007-03-03
You blacklist prism54 because if ndiswrapper tries to load *and* the native driver prism54 loads, they will lock in mortal combat for computer supremacy and you will yell, "Curse you, Chili! I said, curse you" when your wireless doesn't work.

sudo gedit /etc/modprobe.d/blacklist and add a couple of lines something like this:
```
#chili sez prism54 sux
blacklist prism54
```

---

### Post by cr4z3d on 2007-03-03
Haha alright, I got it blacklisted then I realized i set ndiswrapper to use the .sys file. You meant the .inf file right? Well anyway I set it up with the .inf and I'm on my own network with WPA instead of using someone's unprotected haha. Thanks for all the help.

---

### Post by chili555 on 2007-03-03
Glad it's working. You are right, it should be .inf. I will edit for the benefit of the searchers.

---

