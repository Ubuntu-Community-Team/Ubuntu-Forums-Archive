---
title: "Just installed Ubuntu Linux, now I need interne working on it..."
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by ihatevista on 2008-06-09
ubuntu 8.04 & Atheros AR8121/AR8113 NIC is what im working with.

Im also very very new to this so I will need alot of explaining :p

I just ned to know how to get online on a freshly installed Linux. this is my first time.

thanks.

---

### Post by ihatevista on 2008-06-09
ubuntu 8.04 & Atheros AR8121/AR8113 NIC is what im working with.

Im also very very new to this so I will need alot of explaining 

I just ned to know how to get online on a freshly installed Linux. this is my first time.

thanks.

---

### Post by LO Matt on 2008-06-09
this looks promising . . .

[http://ubuntuforums.org/showthread.php?t=770173&highlight=no+ethernet+acer](http://ubuntuforums.org/showthread.php?t=770173&highlight=no+ethernet+acer)

---

### Post by ihatevista on 2008-06-10
> **LO Matt said:**
> this looks promising . . .

[http://ubuntuforums.org/showthread.php?t=770173&highlight=no+ethernet+acer](http://ubuntuforums.org/showthread.php?t=770173&highlight=no+ethernet+acer)

hey, thanks for the answer.

Ive already seen that thread and it is WWAAAYYYYY too complicated for me... Im going to need to be guided through it step by step :(

is this what im supposed to do?



1) I installed ubuntu hardy 64bit, i has build-essential package installed
2) Then i downloaded the linux driver from: [http://support.asus.com/download/dow...model=P5KPL-CM](http://support.asus.com/download/dow...model=P5KPL-CM)
(as per my original post)
3) I then transfered the driver via usb stick to my laptop and unpacked the zip. (Actually i unpacked it on windows first as it has a .rar file that i could not unpack on linux Then i packed it up again on windows).
4) cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src
5) then i ran: sudo KBUILD_NOPEDANTIC=1 make
6) then i ran: sudo KBUILD_NOPEDANTIC=1 make install
7) that worked and put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/at1le.ko
8 ) i cd into that director and i run: sudo insmod ./atl1e.ko



that is ricidulously complicted... for me :(

thanks guys.

---

### Post by ihatevista on 2008-06-11
so can anyone help me?

I really want to get rid of vista :(

does anyone here have msn messenger that could help me through there?

thanks.

---

### Post by ihatevista on 2008-06-17
Thanks alot for the help guys!

---

### Post by WSmart on 2008-06-17
Are you connected?

---

### Post by ihatevista on 2008-06-17
> **WSmart said:**
> Are you connected?

thanks for the reply.

I am connected to the internet in vista.

I cant connect in Linux, I dont know what to do. Im very new at Linux and know nothing about the "code talk" you guys use and all the abbreviations and how to find them. Im good with computers, just some of this is a little complicated for me.

Can I put my music file into an external harddrive, then get rid of vista, then open linux and put all my stuff onto it via the external HDD?

Thanks

---

### Post by ihatevista on 2008-06-19
so why isnt anyone answering me?

Am I in the wrong forum?
Is it my usename?
Am I too "nooby" for you guys?
Is my question too hard?
Is there something I should know?
[SIZE="1"]
I doubt this will get answered....[/SIZE]

---

### Post by WSmart on 2008-07-01
Any luck?  

Is this a wireless connection?  You didn't give very much information.  Seems like there are some new issues in 8.04 with some wireless adaptors.

The best advice I can give you is don't 'quite your day job', get a KVM switch and keep using Vista until you eventually have everything working in Ubuntu.  I did that six months ago with XP and now I do everythiung with Ubuntu and I'm checking out Kubuntu and Xubuntu.  Learning a new system takes time and it can be frustrating when you already have skills in another system. 

When our leaders fail to recognize character, everyone loses.

---

