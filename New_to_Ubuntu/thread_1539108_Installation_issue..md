---
title: "Installation issue."
date: 2010-07-26
forum: New to Ubuntu
---

### Post by pravej1 on 2010-07-26
Hi All,
 
I have windows XP installed on my machine. Yesterday I tried to install ubuntu 10.04. 
I have 4 partitation of my 40GB drive. in C drive I am having XP. I installed ubuntu in in D drive. It was installed successfully and I am able to login to ubuntu. But the problem is that I was not able to login to my Windows account. Also it dint show any menu at the startup, like which version you want to run (i.e. XP or ubuntu).
Today morning I again installed XP in C drive. Now I ma not able to login to ubuntu account.
Please help me, so that my both the account work (XP and ubuntu)
Thanks
Pravej

---

### Post by jarviser on 2010-07-26
Re-installing XP would destroy the Ubuntu boot. Windows does not play fair!

Remember C and D drive naming is a Windows thing.

Easiest way, as you have just reinstalled XP, assuming the other partitions are not wanted, use a tool like GParted (download the iso and burn to a CD) to delete unwanted partitions (D drive etc). If XP partition tool will allow you to remove D completely then do that. 
That leaves disk space that is unformatted.  Then tell Ubuntu to install using available unused space. It will then create all the required Linux format partitions it needs. These will not be visible in Windows by default.

---

### Post by Wiid on 2010-07-26
Maybe it overwrote your files, What method did you use.. Extract the ISO and install so it depends on your windows machine ?

---

### Post by oldfred on 2010-07-26
If your Ubuntu install really was in a D: partition separate from C: then the wubi file root.disk is still there and can be used/recovered.

You probably did not have to reinstall windows if it was just a boot issue as that has to do with boot loaders. The windows reinstall recreated boot.ini without the extra entry for wubi and some files that link it to the install. It should be repairable if you do not want to reinstall.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

---

