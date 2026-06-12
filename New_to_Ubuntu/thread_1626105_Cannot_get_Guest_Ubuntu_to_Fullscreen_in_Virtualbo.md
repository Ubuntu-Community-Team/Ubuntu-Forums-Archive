---
title: "Cannot get Guest Ubuntu to Fullscreen in Virtualbox, even after installing..."
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Rettocs on 2010-11-19
Cannot get Guest Ubuntu to Fullscreen in Virtualbox, even after installing the guest additions software.

I am getting frustrated as I am new (this is my first linux install) and I have no idea what I could be doing wrong. I did the dkma command, installed the additions, restarted, all from guides posted on the internet. Nothing seemed to go wrong, but I still am getting the small screened window even with Host+F. I have an XP Guest as well, and I got it fullscreened very easily.

My host is Windows 7, if you need any other info, please let me know...

Thanks in advance,
Rettocs

---

### Post by uRock on 2010-11-19
Hello and welcome to the forums. 


How did you install Guest additions in the Ubuntu VM? 

> The way I install guest additions is by first mounting the ISO in the VM, drag and drop VBoxLinuxAdditions-amd64.run or VBoxLinuxAdditions-x86.run(32bit), whichever matches your VM's archetecture, into your home folder, then run the following two commandsone after the other into a terminal in the VM, ```
chmod 777 VBoxLinuxAddition*.run
``````
sudo ./VBoxLinuxAddition*.run
```If you have installed any updates since installing the guest additions, then you will have to reinstall guest additions.

Hope this helps,
uRock

---

### Post by Rettocs on 2010-11-20
Alright, I followed those instructions, restarted the machine again, and still no dice.

---

### Post by slooksterpsv on 2010-11-20
What version of VirtualBox are you running? 3.2.8 had problems with the Additions, they were junk for Ubuntu 10.10, at least I found; if you aren't running 3.2.10, upgrade to that.

---

### Post by uRock on 2010-11-20
Which version of VirtualBox are you using?

---

### Post by Rettocs on 2010-11-20
I'm running VB 3.2.8. So this could be the problem? Awesome. I'm installing a W7 Vbox real quick, and then when it is done, I'll try to upgrade.

---

### Post by Rettocs on 2010-11-20
Thanks guys. After all of that frustration, it WAS the version of VB I was running the whole time. 3.2.10 fixed it.

You all rock.

---

### Post by slooksterpsv on 2010-11-21
> **Rettocs said:**
> Thanks guys. After all of that frustration, it WAS the version of VB I was running the whole time. 3.2.10 fixed it.

You all rock.

Anytime, I see you're new to the forums, I highly recommend marking your thread as Solved, at the top under Thread Tools there's an option for Mark Thread Solved - so that if others search for the issue, instead of reading to see "if" it was resolved, they can see it was. =D

---

