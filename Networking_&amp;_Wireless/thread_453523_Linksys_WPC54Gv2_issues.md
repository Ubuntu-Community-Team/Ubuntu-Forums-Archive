---
title: "Linksys WPC54Gv2 issues"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by headkase on 2007-05-24
I have read every possible solution for this problem and still have gone nowhere.  Here is where I stand, bare in mind that I only have wireless internet at this time and wired is not an option.

I did a fresh install of fiesty.  I am new to Linux so I am learning as I go.

Got everything booted and then started on the wireless.  ubuntu sees it, but is using the acx_pci driver.

I tried the ndiswrapper fix with the windows driver and it installed without the 4 lines of radio state changes(maybe this is my problem)?

I did more research and thought I found out how to keep the wireless card from using the acx_pci driver by blacklisting it but it still uses it.

I even went into the terminal and tried telling the wireless adapter to use the ndiswrapper driver and it said it was not installed correctly. 

I checked the log and it said the driver was possibly missing a symbolic link.

I am able to scan for networks and I do see a couple, but even with the access point right next to me I don't get better than like 30% and it tries to connect but will not.

What can I do to get this to work?  I have maxed out my current knowledge and looking for any help possible

---

### Post by benanzo on 2007-05-24
I have a WPC54Gv2 PCMCIA card on a laptop here, and it worked out of the box on Feisty with the *bcm43xx* driver.  Just to be clear of which chipset your card is actually using, do this in terminal:

```
sudo update-pciids
```
then
```
lspci | grep Broadcom
```

That will determine if there is support for your card in the *bcm43xx* code.

---

### Post by headkase on 2007-05-25
I have the ACX111 chipset, however I got it to work with the help of one of the posts already here.  I used the ndiswrapper to no avail before however I was not changing the case of the .sys file.  Once I did that, works like a champ.

Thanks

kase

---

