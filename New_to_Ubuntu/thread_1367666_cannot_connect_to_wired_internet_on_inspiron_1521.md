---
title: "cannot connect to wired internet on inspiron 1521"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by sugarnips on 2009-12-29
i really dont know whats is going on with my computer, i know for a fact my rooter is fine, internet works, since im on this dinosaur laptop getting wireless internet fine.
 
connected my other laptop to wired internet, since i have a few ideas on how to fix my wifi connection problems, and even this doesnt work.
 
i am using the most recent version of ubuntu, (9.10) and havnt tweaked anything i know of, only tried a few simple step by step instructionhttp://ubuntuforums.org/showthread.php?p=8545321#post8545321
 
here is my ifconfig log
 
eth0
 
link encap: Ethernet HQWaddr 00:19:b9:7e:0c:16
inet6 addr: fe80::219:b9ff:fe7e:c16/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
Rx packets: 483 errors:0 dropped:0 overruns: 0 frame:0
TX packets: 10 errors:0 dropped: 0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes: 31812 (31.8 KB) TX bytes:1876 (1.8 KB)
Interrupt:21
 
lo
 
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
i will be checking this page very often, kinda desperate, i have no idea why or how this problem occured.

---

### Post by tom.swartz07 on 2009-12-29
> **sugarnips said:**
> i really dont know whats is going on with my computer, i know for a fact my rooter is fine, internet works, since im on this dinosaur laptop getting wireless internet fine.
 
connected my other laptop to wired internet, since i have a few ideas on how to fix my wifi connection problems, and even this doesnt work.
 
i am using the most recent version of ubuntu, (9.10) and havnt tweaked anything i know of, only tried a few simple step by step instructionhttp://ubuntuforums.org/showthread.php?p=8545321#post8545321
 
here is my ifconfig log
 
eth0
 
link encap: Ethernet HQWaddr 00:19:b9:7e:0c:16
inet6 addr: fe80::219:b9ff:fe7e:c16/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
Rx packets: 483 errors:0 dropped:0 overruns: 0 frame:0
TX packets: 10 errors:0 dropped: 0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes: 31812 (31.8 KB) TX bytes:1876 (1.8 KB)
Interrupt:21
 
lo
 
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
i will be checking this page very often, kinda desperate, i have no idea why or how this problem occured.

Hiya!

Im using a Dell 1521 also.

Did you just install Ubuntu on the system, or did this just occur? 


It says that your wired ethernet is up ETH0, but there is no entry for your wifi card. Did you enable the driver from the system>admin>hardware drivers application yet?


Ive had some minor problems with the newest version of Ubuntu on my rig. If you have Windows still on your system, I DEFINITELY RECOMMEND installing the latest bios. Version A06, I believe. That cleared up problems with both my install and drivers.

---

### Post by sugarnips on 2009-12-29
unfortunatly i no longuer have windows on my pc, got too lazy to split up the discspace
 
also, my wifi card doesnt appear in hardware drivers.
 
im extremly new to linux, but very commited to this os change i made, what is this bios u speak of?

---

### Post by tom.swartz07 on 2009-12-29
> **sugarnips said:**
> unfortunatly i no longuer have windows on my pc, got too lazy to split up the discspace
 
also, my wifi card doesnt appear in hardware drivers.
 
im extremly new to linux, but very commited to this os change i made, what is this bios u speak of?

Okay, When you first turn on your computer, it says DELL! and has the AMD logo on the bottom. Thats your Bios. It powers up the different components of the computer (hard drive, keyboard, mouse, etc) so that the OS could use them.

Could you verify that your Bios version? It says the version across the bottom as soon as you hit the power button. Its usually 'Version A0*'

---

### Post by tom.swartz07 on 2009-12-29
Do you still have your Windows Cd? Unfortunately, it seems that you had a bad install of ubuntu, and it needs to be wiped and redone anyway.

I figure that because of this, you could install Windows (unfortunately) update your BIOS, and then fresh install Ubuntu.


The only reason that I recommend installing Windows is because of the circumstance and from past experience. The only way to update your BIOS with the Dell installer is to use Windows. Its an .exe file and will not run from WINE. Once the BIOS is updated, it will clear up problems that Ubuntu (and even Windows) experience with wifi drivers and ethernet controllers. If you choose to upgrade your Hard Drive, the BIOS will not recognize it. (this is how I found out that it needed to be updated)

Fortunately, The BIOS updates are extremely rare.


Let me know if you need help going through it. I have links available once you get up and running.

---

### Post by sugarnips on 2009-12-29
Bios Revision A00
 
and yes, i still have the windows cd, 
 
tried that already though, and encountered a problem reinstallling.
 
on the other hand, i have the same cd i installed ubuntu 9.10 from, i didnt get it from internet, a family friend made one for me. im thinking that i should pop it in and just reinstall the whole thing, doubt it would change anything though...

---

### Post by tom.swartz07 on 2009-12-29
> **sugarnips said:**
> Bios Revision A00
 
and yes, i still have the windows cd, 
 
tried that already though, and encountered a problem reinstallling.
 
on the other hand, i have the same cd i installed ubuntu 9.10 from, i didnt get it from internet, a family friend made one for me. im thinking that i should pop it in and just reinstall the whole thing, doubt it would change anything though...

Alrighty, since you cant(?) install windows to update the BIOS, Lets just skip to step 2.

Do a complete, fresh install of Ubuntu using that cd that your friend gave to you. I would suggest just using the whole disk, to maximize your space and you arent using Windows anymore.

When you put the disk in, select 'try ubuntu w/out changes' and boot to the desktop. See if it recognizes your WiFi driver (it should after a few minutes). Then select Install Ubuntu. Follow it step by step and let it do its thing.

NOW, you should have a working, fully functional install after that.




Im still kind of worried about the BIOS, knowing what kinds of grief that it caused me. Although I dont fully agree that it should be left alone at version A00 (especially when the current version is A06). I suppose there is no control over what is going to happen.



Let me know if you run into any kinks along the way.

---

### Post by sugarnips on 2009-12-29
i ran it from live and my wired worked!!!; thats will be good enough, i am finishing the install, will be dre installing everyhting i need to get wireless going now.

---

### Post by tom.swartz07 on 2009-12-29
> **sugarnips said:**
> i ran it from live and my wired worked!!!; thats will be good enough, i am finishing the install, will be dre installing everyhting i need to get wireless going now.

Great news!

It should be noted that it is not uncommon that installs sometimes cause errors with the 'technical' aspects of computers, wifi drivers, sound cards, etc. are the most common causes of errors.


Theyre working on it, but until its completely bulletproof, its often easier to re-install.

Let us know if the driver works, and if so- we could call this thread [solved]

---

