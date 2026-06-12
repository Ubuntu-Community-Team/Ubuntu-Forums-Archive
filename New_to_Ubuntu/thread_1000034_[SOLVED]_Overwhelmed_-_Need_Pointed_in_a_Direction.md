---
title: "[SOLVED] Overwhelmed - Need Pointed in a Direction"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by mdwpm on 2008-12-02
Wow, this isn't going to be easy.

Absolutely new to linux and Ubuntu. Ordered the Ubuntu 8.10 desktop edition disk to start the journey.

Loaded on to my Windows XP PC - inside windows, so I can dual boot.

Ubuntu loaded and asked me to reboot which I did and I selected the PC to boot Ubuntu. It dumped me to the "grub" prompt. I'm lost -- where can I find out where to go from here.

I've looked over the absolute beginners forum, searched the forum, etc. It doesn't seem like anyone has had this basic of a question.

Can someone please point to somewhere to get me going?

Thanks
Jim

---

### Post by Dedoimedo on 2008-12-02
Hello,

Please help me out with what you did.

You installed Ubuntu using WUBI, I presume? From inside Windows?
After the installation completed, you rebooted?

You reached GRUB, which is the default bootloader for Linux. For all practical purposes, it's a menu, where you choose which operating system to load.

Can you please specify more information?

Dedoimedo

---

### Post by anotherdisciple on 2008-12-02
Grub prompt? It should give you (2) options to select from... Ubuntu and Windows... you select the one you want and hit enter.

Is that not happening?

---

### Post by mdwpm on 2008-12-02
Yes upon reboot I get the choice to boot either Windows or Ubuntu. If I choose to boot Ubuntu the next thing I see is this:

GRUB4DOS 0.4.4 2008-10-27, Memory: 639K/1022M, CodeEnd: 0x42910 [Minimal Bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]

grub>





Note I installed from the Ubuntu disk I received in the mail from Ubuntu. I started in Windows and inserted the CD into the drive. I choose to install 'inside windows' in order to maintain the dual boot capability between windows and Ubuntu.

I guess I'm looking for the command(s) to input at "grub>" to get me to a graphic interface of some sort -- I think.?

> **anotherdisciple said:**
> Grub prompt? It should give you (2) options to select from... Ubuntu and Windows... you select the one you want and hit enter. I don't know if I installed with Wubi or whatever - it's whatever install comes on hte dis from Ubuntu.

Is that not happening?

---

### Post by mapes12 on 2008-12-02
Some how your windoze boot loader has not been configured correctly. Can you load windoze OK? If you can then you may be able to reconfigure your system and remove the offending files. For a more comprehensive guide go here: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

It may be helpful to read more of the guides on the site and maybe have a look at alternative dual boot alternative solutions.

Welcome to Ubuntu and good luck!!

---

### Post by mdwpm on 2008-12-02
Thanks, I'll check it out.


> **mapes12 said:**
> Some how your windoze boot loader has not been configured correctly. Can you load windoze OK? If you can then you may be able to reconfigure your system and remove the offending files. For a more comprehensive guide go here: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

It may be helpful to read more of the guides on the site and maybe have a look at alternative dual boot alternative solutions.

Welcome to Ubuntu and good luck!!

---

### Post by mdwpm on 2008-12-02
OK, I uninstalled Ubuntu. Before I reinstalled Ubuntu I turned off Avast anti-virus. Rebooting after this installation I am able to chose Ubuntu as my operating system.

There is activity at the Ubuntu 'splash' screen as it is apparently loading then I get a Oversize Recommand Mode 1280x1024error and my monitor is turned off.

It is a Kogi monitor which I see others may have had the same problem with although I don't see any solutions posted anywhere. I'm not giving up 'the truth is out there'.  ;)

---

### Post by mdwpm on 2008-12-02
OK, I'm up and running. 

To solve the monitor problem I rebooted to windows and then changed my display setting to 800x600. I then rebooted into Ubuntu and the installation finished and here I am running Ubuntu.

Thanks to all for tolerating I real newbie. ):P

---

