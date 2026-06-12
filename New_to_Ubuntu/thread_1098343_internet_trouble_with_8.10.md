---
title: "internet trouble with 8.10"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by 2roombas on 2009-03-16
I have a Dell Inspirion  1505 and have installed 8.10.  I'm very new to Linux.

1. When I rt -click on the icon  **Wired Networks**,** Auto etho** and **Wireless Networks** are all grayed out.
2. With a left click,**Enable Networking** and **Enable Wireless** are both checked.
3.  In **System/Admin/Hardware Driver** there s only a "**wi**" there, and it is activated
2  In Network Tools on the Devices tab I see the **Interface Information **says...

Hardware address   loopback
Multicast           Disabled
MTU:                16436
Link Speed:
State:             Active

That disabled notice doesn't look good, does that mean something?

On this page below I saw something I could try, but both files "could not be found."  He says they're on the Live CD, which is what I used, odd.  Am I supposed to do this with the CD inserted?

[http://www.ubuntu1501.com/2008/10/ubuntu-810-intrepid-ibex-on-dell.html](http://www.ubuntu1501.com/2008/10/ubuntu-810-intrepid-ibex-on-dell.html)

sudo apt-get install compizconfig-settings-manager
sudo apt-get install fusion-icon 

Everything was working fine when I was dual booting, then I foolishly I guess decided to get rid of Windows and just have ubuntu.  I keep no files, just the default on that laptop, so I thought it would be no problem to just choose full install this time..  It appears to have removed something I needed to get internet access.:(
I cannot download this ndidwrapper thing I'm seeing since I can't eveb get on the internet to begin with that computer. I can on this desktop,yes, but this desktop has only Windows on it and not enough memory to dual-boot.  Anything else I can do?  If there is any other information you need I'll be happy to supply it.

---

### Post by phantom3113 on 2009-03-16
If you just installed recently, it's probably a wireless driver problem. Could you post the output of lspci please? Also, with the live CD, you need to select it as a source first (system>>administration>>software sources) and there should be a white box near the bottom that says "CD ..." and lists your ubuntu version. Select that and reload when it prompts.

---

### Post by 2roombas on 2009-03-17
Thank tou for your reply.  How do I get the output from the lspci?  Is this typed in terminal? 

I do have a dell mini with 8.04, which connects just fine.  The two look similar EXCEPT that in the Edit Connection settings of the 8.04 there is **WEP 64/128-bit Hex **(which I selected when setting up my router) and 8.10 does not even have that option.  Otherwise it all looks similar in what I mention in my original post.

---

### Post by 2roombas on 2009-03-17
Ah... I see this is a rather common problem...

[http://ubuntuforums.org/showthread.php?t=974272](http://ubuntuforums.org/showthread.php?t=974272)

---

### Post by 2roombas on 2009-03-17
OK... I read this as a possible fix in that thread.  I can't get the wicd mentioned bc my dell mini does not have an external disk drive. So, would this work?  If so, please remember I'm very new to linux. What is this actually telling me to do?:)
------------------
I believe there is a way to make the wi-fi work without having to install wicd. Here is how I did it:

1) Add the following repositories to update network-manager:

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

2) run apt-get update

After this, your network manager should be able to receive wep 64/128-bit Hex keys.

---

### Post by 2roombas on 2009-03-17
[B]
UPDATE:  Please disregard this particular post.How cn I delete a post I made?[/B]

> **phantom3113 said:**
> Also, with the live CD, you need to select it as a source first (system>>administration>>software sources) and there should be a white box near the bottom that says "CD ..." and lists your ubuntu version. Select that and reload when it prompts.

When I did this up popped ab "Error occurred" box

W:  Failed to fetch [http://us.archives.ubuntu.com/ubuntu/dists/intrepid/release.gpg](http://us.archives.ubuntu.com/ubuntu/dists/intrepid/release.gpg)  Could not resolve `us.archive.ubuntu.com'

This Live CD is one that was sent to me too, it's not a download.
[B]
UPDATE:  Please disregard this particular post.How cn I delete a post I made?[/B]

---

### Post by 2roombas on 2009-03-17
I'm still researching this and it appears to be a rather big problem quie a few users have. Since I have no way to get that **WICD**, I guess the best bet is to just reset my router and set up a **128-bit passhrase** or a **wpa personal**, right?

---

