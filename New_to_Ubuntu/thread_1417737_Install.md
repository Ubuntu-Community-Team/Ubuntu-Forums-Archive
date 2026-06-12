---
title: "Install"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by DarinB on 2010-02-27
i am installing 9.10 on a clevo laptop D900
CPU pentium 4
2GB ram
two HDD 
sde1 in 8.04 **not seen in 9.10 partitioner manual** listed as boot /dev/sda in gparted live
sdf1 /home folder in 9.10 partitioner manual listed as sdb as /dev/sdb in gparted live cd

i want to wipe out the os and install 9.10
how do i do it

---

### Post by mechro on 2010-02-27
I'm guessing you know how to clear a hard drive and install 9.10 using the regular installer.

So you must have another problem that you've not clearly explained.

---

### Post by DarinB on 2010-02-27
please explain what clear hard drive means. only one hard drive is seen on both auto installer and manual partitioner from the 9.10 live cd. 
the smaller / hard drive is not seen at all. if i install on the visible one  he will lose his /home if i do not reformat then i imagine his /boot hardy will then apear as the boot partition and not boot to 9.10.
or i have no frakin idea what i am talking about and am in desperate need of help

---

### Post by mechro on 2010-02-27
clear hard drive = wipe the OS = format the whole drive = nuke everything!

If the 9.10 installer is not seeing all the drives then try formatting/deleting using the gparted CD. The Ubuntu installer may then see all the drives.

... but then again I'm now not clear whether you want to "wipe the OS" or retain a /home and a /boot.

---

### Post by louieb on 2010-02-27
Your not being very clear. 
Does this laptop have Linux install on it now? 
Most laptops only have one hdd - is the other one internal or external?   

To give us good information to work with go to  [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")  run it and put the results.txt file in your next post.

---

### Post by DarinB on 2010-02-27
this lap top has two hard drives and it does have hardy heron installed on it. I purposely set this friends laptop with a /home on a separate Hdd. so he can easily put in a new OS. 
I am not sure if it would be a good idea to wipe out the / and try that way>
any ideas why it is not seen by 9.10 but was perfectly seen by 8.04 I did a format of / and reinstall of Hardy Heron. but i would like to go to 9.10 for him. ??

---

