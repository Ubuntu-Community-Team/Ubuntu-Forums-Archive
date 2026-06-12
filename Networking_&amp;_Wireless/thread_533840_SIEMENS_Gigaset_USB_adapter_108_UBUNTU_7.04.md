---
title: "SIEMENS Gigaset USB adapter 108 UBUNTU 7.04"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by source of the chaos on 2007-08-24
dear people.

i installed linux ubuntu 7.04 yesterday and i am very happy because i hate windows.
everything works perfect but i can't install drivers for gigaset usb adapter 108
i tried to find pages on internet but they are all similar and i can't install driver.
i tried with   ndiswrapper but when i click "install new drivers" and select "athfmwdl.inf" or "net5523.inf" nothing happens.

i even try in terminal, but i don't know what to write.
then i found on net what to write:
ndiswrapper -i athfmwdl.inf
ndiswrapper -i net5523.inf

and this shows: "Permission denied at /usr/sbin/ndiswrapper-1.9 line 146."

can someone be so kind and tell me step by step what i need to do. PLEASE.
i like very much linux but I'm noob here.

---

### Post by source of the chaos on 2007-08-25
please help me

---

### Post by source of the chaos on 2007-08-26
> **source of the chaos said:**
> please help me

someone????

---

### Post by fatski on 2007-08-26
try putting **sudo** before the the terminal commands, eg:

sudo ndiswrapper -i athfmwdl.inf
sudo ndiswrapper -i net5523.inf

This makes the command run as the root user, you will be asked to type in your password.

---

### Post by source of the chaos on 2007-08-26
i tried that.

nothing happens :(

---

### Post by source of the chaos on 2007-08-26
help me

---

### Post by source of the chaos on 2007-08-27
> **source of the chaos said:**
> help me

help me

---

### Post by source of the chaos on 2007-08-27
> **source of the chaos said:**
> help me

help me

---

### Post by markcgriffiths on 2007-08-29
Hi, 

My device installed with no problems.  Here is what I did.

[http://www.linuxquestions.org/questions/showthread.php?p=2367128](http://www.linuxquestions.org/questions/showthread.php?p=2367128)

Check out the ndiswrapper website, there's lots of useful information there.

---

