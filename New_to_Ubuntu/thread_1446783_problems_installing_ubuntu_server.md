---
title: "problems installing ubuntu server"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-04-04
ok im trying to install a 32bit version of ubuntu server 9.10  and after like forever installing it  it says to eject the disk i do that   and 


it wont boot up the gui at all  

then it pops up this this

grub rescue>

and i have no idea what to do after that i have tried this three times already and getting kind of irritated  any suggestions

---

### Post by mikewhatever on 2010-04-04
Well, the server has no gui, which kind of makes sense.

---

### Post by pyrofreak99 on 2010-04-04
yeah i im not sure im installing right or what i never installed a server before and i always get that error no matter what

---

### Post by itiswhatitis on 2010-04-04
So the problem is that grub is having an issue...

What is the hardware you are installing on?

It it really a server hardware or a desktop you are installing server to?

What type of hard drives?

RAID? 

No gui with ubuntu server, so you'll need to be familiar with the command line.

---

### Post by lavinog on 2010-04-04
You might want to check the instalation disk for errors.
It shouldn't take a long time to install the server.

Can you give some details of the configuration?

Server installs will not give you a gui, but you shouldn't be booting to a grub rescue prompt though.

---

### Post by pyrofreak99 on 2010-04-04
its a 80 gb desktop computer  im not really sure what the other specs on it are

---

### Post by pyrofreak99 on 2010-04-04
ok pretty much what i do when i install it  i go through and type all the information in

then i get to install software  i install a lamp server and open ssh   it installs that  then tells me to eject the disk  then when it restarts it tells me there is no gui and it gives me a grub rescue thing

---

### Post by pyrofreak99 on 2010-04-04
am i supposed to have ubuntu already installed on the computer before i  try to install the server edition? 


cuz im booting it from a wiped hardrive

---

### Post by s_ø on 2010-04-04
> **pyrofreak99 said:**
> am i supposed to have ubuntu already installed on the computer before i  try to install the server edition?
No

How does it tell you that you have no gui? What are the exact words?

There is no gui installed with the server install. But you should get a command line. If you need a gui you can install the x-server from command line.

If you are uncertain about the server setup and the command line, you could install desktop ubuntu and add LAMP + SSH to that.

---

### Post by pyrofreak99 on 2010-04-04
ok here is exactly what it says 


grub loading


error: no such partition

grub rescue>

---

### Post by sandyd on 2010-04-04
> **pyrofreak99 said:**
> ok here is exactly what it says 


grub loading


error: no such partition

grub rescue>

then it is not a issue with it not booting into a gui. it is not even making it past grub. if you have a desktop livecd, could you boot it up on that and run the boot info script?

---

### Post by s_ø on 2010-04-04
This is presumably because grub is looking in the wrong place for your install. Look at this [https://help.ubuntu.com/community/Grub2#Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")
If you have trouble following the instructions post again and i will try to help you.

---

