---
title: "New kernel appears to have broken WIRED networking."
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by em3raldxiii on 2015-08-18
Okay here's the lowdown:

1.  I had Ubuntu 14.04 running, and all was well - wired networking purred along right outa tha box; but I started getting curious about the newfangled things in 15.04.
2.  I didn't want to upgrade to 14.10 and then again to 15.04, I figured that was silly.
3.  Whipped up a USB stick with unetbootin and a fresh ISO of Ubuntu 15.04.
4.  From the stick, all was well.  Networking worked, although I have to be honest that I don't remember consciously testing it.  I _do_ remember it downloading some updates during the install.  Probably the kernel.
5.  Rebooted.  **Networking tries to connect over and over continually** but never succeeds.

[SIZE=1]*It should be noted that this problem is also occurring in the latest version of Sabayon which I have jammed into a small corner of one of my hard drives to see what all the fuss is about.*[/SIZE]

I searched online using *Tha Googz* on my phone for hours, and the consensus appears to be that there's something [FONT=comic sans ms]gooftastic[/FONT] about the kernel not playing nice with my particular NIC (and a few others).  I am running kernel 3.19.025 generic (off the top of my head).

[B][U][FONT=book antiqua][SIZE=5][COLOR=#006400]SOLUTION [/COLOR][/SIZE][/FONT]

[/U][/B](Condensed from the entire thread)

This applies to UBUNTU 15.04
```
lspci | grep Ethernet
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

My kernel version at the time:
```
uname -r
3.19.0-25-generic

```

It appears that my particular hardware/kernel/driver combo was bad, please read the entire thread (which isn't too long) in order to get the whole story.  All credit goes to @praeseodym for figuring out the problem.

Note that not every single one of these commands is necessary; some may be redundant.

[LIST=1]
[*]Download the new Network Card driver from here:  [https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz)
[*]Download the DEB package from here:  [http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu3_all.deb)
[*]If you have recently updated to a new kernel once again after following this guide, you'll have to remove the module and its source directory like this:
```
uname -r
[COLOR=#000000][FONT=Ubuntu Mono]sudo dkms remove r8168-dkms/8.040.00 -k {output from uname -r}
[/FONT][/COLOR]sudo rm -r /usr/src/r8168-dkms-8.040.00/

```
[*]Run this series of commands from the directory where you downloaded those files:
```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
[*]For some reason, I had to give this command *another go* in order to purge the old driver (I had run this once previously):
```
sudo apt-get remove --purge r8168-dkms
```
[*]After rebooting, both drivers were still running.  I am sure that people with even marginally better understanding would realize the issue.  Thus, to kill the old and make the new driver take effect:
```
sudo modprobe -rfv r8169 r8168
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```
[/LIST]

Again, some of this stuff is a little redundant, but I am reasonably confident that if people are having the same trouble as I was, and their hardware is the same, this series of steps will solve it.  All credit to @praseodym.

---

### Post by praseodym on 2015-08-18
Please run the wireless-script from the sticky thread for more information

---

### Post by em3raldxiii on 2015-08-18
@praseodym I will do that, but you _did_ read what I said, right?  This is not a wireless issue.

---

### Post by em3raldxiii on 2015-08-18
@praseodym:  I apologize for my slightly snippy response ... I am too accustomed to people not reading all the details.  Anyhoo ... I didn't realize that the "wireless-info" script _also_ helps with the wired stuff.  Also, I was a little frustrated by the time I posted.

SOOOO ... here's the information on pastebin.  I've browsed over it, but I can't really see specifically what the issue is.  I see some suspiciously missing details, but that's about it.  (At the bottom, I have included the wireless-info from my Ubuntu 13.10 for comparison).  

*edit:  *I did a diff comparison, and it's not giving me much that's useful that I can see.  I could be out of my depth.

[http://paste.ubuntu.com/12119893/](http://paste.ubuntu.com/12119893/)

---

### Post by praseodym on 2015-08-18
See below

---

### Post by praseodym on 2015-08-18
Hi, I just made the latest driver available, Version 40, try this one instead:

[https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu3_all.deb)
```

cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
See here
[https://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms](https://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms)

---

### Post by em3raldxiii on 2015-08-18
Heh, nice timing, I was just in the process of downloading those files.  I'll snag the new ones and give that a go.  If I don't reply here in the next 10 minutes, it means I was called away.  I will report my results later if that is the case.  Thank you very much for your help!

---

### Post by praseodym on 2015-08-18
It compiled without errors here on Trusty with kernel 3.16

---

### Post by em3raldxiii on 2015-08-18
It compiled just fine on my machine.  I'm away from my pc right now, but the I didn't have networking resolved by the time I left.  It compiled and installed okay, but I had a " good news" message about something being identical to the one installed (sorry I don't have word for word, I'm on my cell).  I'll snag more feedback once I'm home.

---

### Post by em3raldxiii on 2015-08-18
Okay, still no go.

After following your instructions without any troubles, network is still not connecting.  I'll run the wireless-info package again after I reboot back into 15.04.  Here is a screenshot of the directory in Terminal after running the commands:

[IMG]http://ibin.co/2CdKjBCzOtNV[/IMG]

And here is the output regarding the module:

```
$ sudo dkms install -m r8168-dkms -v 8.040.00

r8168:
Running module version sanity check.


Good news! Module version 8.040.00-NAPI for r8168.ko
exactly matches what is already found in kernel 3.19.0-25-generic.
DKMS will not replace this module.
You may override by specifying --force.


depmod....


DKMS: install completed.

```

---

### Post by praseodym on 2015-08-19
Did you uninstall the other package?
```

sudo apt-get remove --purge r8168-dkms
```
Reboot and check:```


modinfo r8168 | egrep 'versi|filen'
locate r8168.ko | grep lib
lsmod
dmesg | grep r8
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by em3raldxiii on 2015-08-25
I've finally had a chance to sit back down at my PC and give 'er a go.  I didn't get very far.  Here's the output of the commands listed just so we can be totally clear.  Note that the dmesg appears to have one entry for 8168:

apt-get remove
[IMG]http://ibin.co/2DJwWImrWbfV[/IMG]

modinfo
[IMG]http://ibin.co/2DJwtPF9tNDt[/IMG]

lsmod
[IMG]http://ibin.co/2DJx9dpnbuBV[/IMG]

dmesg
[IMG]http://ibin.co/2DJxcg5FifQH[/IMG]

Interfaces
[IMG]http://ibin.co/2DJyHZv1JI6U[/IMG]

Resolv
[IMG]http://ibin.co/2DJyVwMfDSdd[/IMG]

So I am a little unsure of how to proceed at this juncture.

---

### Post by praseodym on 2015-08-25
Both drivers are loaded:
```

sudo modprobe -rfv r8169 r8168
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by Bashing-om on 2015-08-25
em3raldxiii; Hello:

@ praseodym; As I pass by and peek over your shoulder.

The system shows to have 202 packages needing updating. Recon updating will go a long way in correcting this situation ?

[INDENT][INDENT]an extra pair of eyes
[/INDENT][/INDENT]

---

### Post by em3raldxiii on 2015-08-28
@Bashing-om I too noticed the need for updating, but I am a little fuzzy as to how to do it without a network connection (in all my years of Linuxing, I have never encountered this need LOL - wired Networking has rarely ever been a problem for me).

Anyhoo ... I am about to give this another go ...

---

### Post by Bashing-om on 2015-08-28
em3raldxiii; My Thought ;

Boot up a live environment, and from that alternate perform a full CHange Root routine into the install.

Once in the install from the CHRoot, one can do the updates .

Mind you, in the Networking arena, I will take a back seat to praseodym, but might consider firing up that wired connection manually ( /etc/network/interfaces) .

[INDENT][INDENT]with a liveDVD
[INDENT][INDENT][INDENT]wonders can happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by em3raldxiii on 2015-08-28
@Bashing-om I'll keep the live-enviro CHRooting in mind if this happens again.  On the upside, @praseodym has patiently won this round - I'm posting this from U15.04!  Woot.  I'll mark the thread as solved, and put a brief synopsis in the original post with props to Praseodym.

---

### Post by Bashing-om on 2015-08-28
em3raldxiii :)


When he us good
[INDENT][INDENT][INDENT]he is good
[/INDENT][/INDENT][/INDENT]

---

### Post by em3raldxiii on 2015-11-17
UPDATE:  Ever since kernel [COLOR=#000000][FONT=Ubuntu Mono]3.19.0-26-generic, this solution has stopped working properly.  I am going to try running the whole shebang once again and see if I can get it rocking again.  I have been using Kernel '26 in the meantime.
UPDATE NOVEMBER 30:  I've solved this problem, too, and I have edited the original post.  It turns out that I had to remove the previous module AND its source files.[/FONT][/COLOR]

---

