---
title: "help with Ubuntu 10.04/Slackware 13.1 dual boot?"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by disastrophe on 2010-08-22
Hello, I've been using Ubuntu and/or Mint now for about 4 months. I've been maintaining a constantly changing lineup of 2 - 4 distros on grub2 with *buntu being about the only constant lol. <- I'm a little hyper :D.
Anyway, I would like to install Slackware 13.1 to one of my partitions. It's kind of like the grandaddy of them all and I'd like to take it for a spin.
As a somewhat hyperactive and relatively new user it's not uncommon for me to break things, hahah - helps me learn. I have a really sweet Ubuntu desktop setup now and it's working marvelously so if I can avoid any catastrophes I would rather do so. But then again that hasn't stopped me yet lol.
I, of course do have all my critical data and media backed up to optical.
What can I expect in the process? I know Slack uses Lilo so can I chain load from grub2 the same way as I would with say, Mandriva or PCLinuxOS?  What would I need to edit on the Slackware side? I am assuming it would need similar changes to the partition numbers as with legacy grub? Help![-o<  
I would be grateful for any assistance, thank you.

---

### Post by neilms on 2010-08-22
Try it and you will see.:lolflag:

---

### Post by oldfred on 2010-08-22
I have not used lilo but it is more like the windows boot loader. It normally installs a simple MBR that just like windows looks for the boot flag and boots that partition. You have to have part 2 of the boot loader in the PBR or partition boot sector (like windows does). Not sure if it needs a primary partition as most systems using boot flag have to have boot flag on primary partition. Grub can chainboot to the lilo boot loader in the PBR.

---

### Post by jtarin on 2010-08-22
In Slack install the option to install Lilo to the Slack partition is available, no need to make the partition active. Grub2 installed to the MBR will detect it. Don't forget to run the command "sudo update-grub" for it to show in the boot line-up.

---

### Post by andrew.46 on 2010-08-22
Hi disastrophe,

You could probably save yourself a world of pain by loading Slackware 13.1 as guest in a virtual machine. I run this the reverse: Slackware 13.1 host and Ubuntu Lucid as guest with Virtualbox ose. In this case you simply install lilo to the *virtual* MBR.

Andrew

---

