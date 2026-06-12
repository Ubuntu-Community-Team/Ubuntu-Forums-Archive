---
title: "Help!!!!!"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Neoki on 2008-05-16
Hello, Would like to pop in and say hi.

Never used linux ever ever before so I am completely new to this thing.

So far impressed yet my broadcom 4311 does not work. Had a quick look around followed the guides on all these strage commands but no luck

I have installed ubuntu-8.04-desktop and followed [This]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

---

### Post by james_vanb on 2008-05-16
This helped sort mine out.  It is used in conjunction with the "How To" you reference.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=bcmwl5](http://ubuntuforums.org/showthread.php?t=766560&highlight=bcmwl5)

Edit:  The link contained in the above thread is not the one you listed in your post and may be a little more recent.

---

### Post by Ayuthia on 2008-05-16
> **Neoki said:**
> Hello, Would like to pop in and say hi.

Never used linux ever ever before so I am completely new to this thing.

So far impressed yet my broadcom 4311 does not work. Had a quick look around followed the guides on all these strage commands but no luck

I have installed ubuntu-8.04-desktop and followed [This]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")
The guide that you used is a little old.  Let's see how far you have made it in the guide.  Can you go to the Terminal and post the results for the following:
```
lshw -C network
ndiswrapper -v
ndiswrapper -l
```
The first command will help determine what driver your wireless is using.  There is a line that contains the word "driver:".  It should say ndiswrapper.  

The second command will tell us if ndiswrapper is happy.  If ndiswrapper is not installed correctly, this will tell us.  It actually provide the version of ndiswrapper, but when it is not installed right, it will give out error messages.

The third command will let us know if the driver that you are using with ndiswrapper is ok.  It will need to show "device (14e4:43XX) present" or else it has the wrong driver.

The second and third commands are the main things that you need to see if ndiswrapper is working.  From there, we can then start configuring ndiswrapper so that it will work on reboot.

---

