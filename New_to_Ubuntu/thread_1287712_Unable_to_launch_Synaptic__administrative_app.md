---
title: "Unable to launch Synaptic / administrative app"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by kinson on 2009-10-10
Hi Guys,

I just downloaded and installed 9.04 Ubuntu and installed it on my AMD Athlon 3000+, 1GB RAM, Dlink DWL-520+ PCI Wireless.

I've installed ubuntu 6.xx in the past and everything was fine, but this time, I can't seem to launch Synaptic / software sources, or administrative apps.

Whenever I try to launch them via the menu bar, I see the bar (at the bottom) saying "starting administrative app"(or something), and then nothing happens.

I can however launch synaptic via terminal "synaptic" or "sudo synaptic". 

I'm not sure if this is related to it, but I suspect this problem might be vaguely related to my wireless problem? The card should be installed, since I see the wireless icon on the top, but when I left click, the "wired network / wireless networks" options are greyed out. 

Any help no this issue would be greatly appreciated :( With it connected to the net, updating and fixing stuff would be a lot easier, but without wireless, it's a major pain, ahah. Using another computer to go online now.

Update: I thought it might be related to my username not being in the sudoer list though (weird). I can't seem to authenticate on "su" anymore. I've since added my username to the sudoer list, but I can't still "su", and the main problem is still there :/

It has also hung on me twice now, with the Caps Lock and Scroll Lock lights blinking. The hardware should be fine, as I can run WinXP on it without any problems. Weird...

Thanks in advance!

Cheers,
Kinson.

---

### Post by zvacet on 2009-10-12
> Update: I thought it might be related to my username not being in the sudoer list though (weird). I can't seem to authenticate on "su" anymore. 

Boot in recovery mode and type

```
adduser username admin
```

username=your user name

Better option is to install most recent Ubuntu version,because Dapper is not supported any more.Probably you  will get better support for your wireless.

---

### Post by mikechant on 2009-10-12
> Better option is to install most recent Ubuntu version,because Dapper is not supported any more.

You missed this in the original post:


> I just downloaded and installed 9.04 Ubuntu

---

### Post by HarrisonNapper on 2009-10-12
> **mikechant said:**
> You missed this in the original post:

But his advice to adduser username admin was probably still correct. If user and security settings are shot, adding the new user will fix most of those issues. This is even the case in Jaunty.

---

### Post by rb0171610 on 2009-10-12
> **kinson said:**
> Hi Guys,

I just downloaded and installed 9.04 Ubuntu and installed it on my AMD Athlon 3000+, 1GB RAM, Dlink DWL-520+ PCI Wireless.

I've installed ubuntu 6.xx in the past and everything was fine, but this time, I can't seem to launch Synaptic / software sources, or administrative apps.

Whenever I try to launch them via the menu bar, I see the bar (at the bottom) saying "starting administrative app"(or something), and then nothing happens.

I can however launch synaptic via terminal "synaptic" or "sudo synaptic". 

I'm not sure if this is related to it, but I suspect this problem might be vaguely related to my wireless problem? The card should be installed, since I see the wireless icon on the top, but when I left click, the "wired network / wireless networks" options are greyed out. 

Any help no this issue would be greatly appreciated :( With it connected to the net, updating and fixing stuff would be a lot easier, but without wireless, it's a major pain, ahah. Using another computer to go online now.

Update: I thought it might be related to my username not being in the sudoer list though (weird). I can't seem to authenticate on "su" anymore. I've since added my username to the sudoer list, but I can't still "su", and the main problem is still there :/

It has also hung on me twice now, with the Caps Lock and Scroll Lock lights blinking. The hardware should be fine, as I can run WinXP on it without any problems. Weird...

Thanks in advance!

Cheers,
Kinson.

If I understand you correctly, you will not be able to type su at the terminal and switch to root, unless you give root a  password  by typing:
*sudo passwd*
at this point you will be prompted for a new password for the root account.  You would then be able to login as root at the command line.  Do so at your own risk.  Otherwise, just use sudo.

I like having a root password because I find it occasionally necessary when installing a proprietary driver or something.  However, I use sudo most of the time.

---

### Post by zvacet on 2009-10-13
There is no need for root password.[Here]("https://help.ubuntu.com/community/RootSudo")

---

