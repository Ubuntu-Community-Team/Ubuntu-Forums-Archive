---
title: "Portable Ubuntu Remix in Windows 7"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by ubantunovice on 2010-05-25
I read in PC Magazine about the possibility of running Portable Ubuntu Remix as an application under Windows 7. Sounding fascinating to try, but I could not get it to work.

[http://www.ghacks.net/2009/04/02/portable-ubuntu/](http://www.ghacks.net/2009/04/02/portable-ubuntu/)

I carefully followed the instructions in
[http://www.progmic.com/2009/09/portable-ubuntu-in-windows-7/](http://www.progmic.com/2009/09/portable-ubuntu-in-windows-7/)
but despite that pubuntu.exe opened the opening flash window and then Windows popped up an error with a fatal cygwin error and did not proceed further.

Does Portable Ubuntu Remix really work under W7? Is there a trick to make it work? Maybe I downloaded the wrong version.

Any help appreciated.

---

### Post by -humanaut- on 2010-05-25
Installing it with Wubi would be a far better and more supported option. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

that link should explain it to you perfectly.

---

### Post by ubantunovice on 2010-05-26
Thank you.  Much appreciated.

---

### Post by ubantunovice on 2010-05-26
Just read about Wubi.  Sounds like that sets up a dual boot. What attracted me to the Portable ubuntu Remix is the ability to 

"run Ubuntu within Windows as a Windows app", 

not a dual boot. See [http://www.progmic.com/2009/09/portable-ubuntu-in-windows-7/](http://www.progmic.com/2009/09/portable-ubuntu-in-windows-7/)

Is that really possible? I am running Windows 7 home Premium 64 bit.

---

### Post by Mark Phelps on 2010-05-26
It's been a few months since I tried it, and I don't remember the specific product, but I did try some portable Ubuntu stuff.  I read about it in one of the on-line computer news forums.

And, while it installed, it was basically a disaster afterward.  Screen display was hosed. Wireless wouldn't work.  Response was so laggy as to be all but useless.

And, yes, I did install it in Win7 -- but it was 32-bit, not 64-bit.

So, it might be a problem trying to use it in 64-bit Win7.  Don't know. Sorry.

---

### Post by ubantunovice on 2010-05-26
Thank you.  Hearing your experience, perhaps it is just great it did not install on my system!

Thanks.

---

### Post by -humanaut- on 2010-05-26
Wubi "acts" like a dual-boot but it's run from windows just like any other installed program.

---

### Post by migs73 on 2010-05-26
Try downloading Virtualbox. Then you can install Ubuntu onto it. This then allows you to be running windows, then with a couple of clicks you can be booting into Ubuntu, with windows still running in the background. I do this with Vista, but the other way round (Vista on virtualbox running on Ubuntu). Works great!!

---

### Post by ubantunovice on 2010-05-26
> **migs73 said:**
> Try downloading Virtualbox. Then you can install Ubuntu onto it. This then allows you to be running windows, then with a couple of clicks you can be booting into Ubuntu, with windows still running in the background. I do this with Vista, but the other way round (Vista on virtualbox running on Ubuntu). Works great!!

Thank you.  That might be my ticket. Thanks.

---

### Post by migs73 on 2010-05-26
Hope it is what you need. It is surprisingly easy to set up. Once downloaded it only takes a few minutes to set up and then you install the OS (probably take about 30 mins for Ubuntu). Remember to set up the guest additions afterwards to let you get full screen!!

---

### Post by ubantunovice on 2010-05-26
Thanks MIGS73.
I downloaded and installed Virtual-box. Went very smoothly.  Which Ubuntu should I download and install in Virtual-box? There are so many it is confusing. One of the portable ones or a full version? I was only looking at the Portable Remix because it was said to run as a Windows app - which it failed to do for me.

"Remember to set up the guest additions afterwards to let you get full screen!!" What do you mean by that and how do I do it?

Thanks.

---

### Post by migs73 on 2010-05-26
There is a good end user manual on the VB website. I would give this a quick read through first.
Any of the *buntus should do. If your system is reasonably well specced the plain ubuntu should be fine.  First find out how much RAM W7 needs and allocate most of the rest to your virtual machine (this is only utilised whilst the virtual machine is running). Virtualbox will only allow you to allocate 50% of your memory, to save your native OS from crashing.
You then require to set up a virtual hard disk, I think the recommended size for plain Ubuntu is 10Gb, but you can allow the virtual disk to dynamically expand if you have plenty of HDD space and are likely to download a few new programs.
The guest additions are just add-ons specific to OS you have installed in VB, you just have to select them from the VB menus once the OS is installed.

---

### Post by ubantunovice on 2010-05-26
Thanks.  I have 6 GB of ram so there should be plenty for both.
What about the part about getting a full screen using guest additions?

Thanks for your help.  Very helpful and I appreciate it.

---

### Post by migs73 on 2010-05-26
The guest additions is covered in section 4 of the user manual. Until you add them the native resolution for the guest OS (Ubuntu in you case) will be quite low. Just follow the instructions in the manual and set it to your preferred resolution.

Follow all the other set-up instructions first though!! The guest additions are additions, you will get Ubuntu working in no time, without it.

---

### Post by ubantunovice on 2010-05-26
Just installed Ubuntu as a virtual OS in Virtual box.  Just amazing!

---

### Post by migs73 on 2010-05-28
Glad to be of help. I have had so much help from people on the forums, it is finally nice to give some back. Enjoy!:P

---

