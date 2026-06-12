---
title: "Ubuntu 10.10 and connections, and ease of use"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by zdubun on 2010-10-20
Hi there,

This seems to be becoming a million dollar question. Now
1. Is it possible to upgrade from 10.04 to 10.10, even though I have missed out on a lot of updates.
2.  I appreciate all the replies to my previous questions about my LAN connection and wifi. But being computer illiterate I cannot understand what to do. I wish somebody could simple the process to a few steps. All the replies led to other threads invoving loads of commands which might as well be greek to me.
3. Guys, I have to admit, I like Ubuntu but one has to be a little computer literate apart from knowing how to click the mouse inorder to use it. I understand Windows is less secure but seems easy you use by the common homosapien. If Ubuntu is to be accepted , it should be more easy to use. 
All the replies that I got did not give a definite answer of what to do and therefore yes, I am still using Windows.

It is now irritating.

Thanks

---

### Post by Joshwaa on 2010-10-20
The commands people tell you to do you run in the Terminal. You get to this by going to Applications -> Accessories -> Terminal.
Hope this helped.

---

### Post by TBABill on 2010-10-20
1. I would recommend you not upgrade to 10.10 until you can get all updates installed and applied. The upgrade process counts on you having your system fully up to date. If you want to move up to 10.10 anyway, perhaps save what you need from your 10.04 install (home directory) and then do a fresh install of 10.10 from LiveCD.
 
2. I haven't seen the wireless issue so I can't say what steps may help.
 
3. Ubuntu being easier...yes there is a definite learning curve, particularly where getting awkward configurations to work regarding drivers. But that also begs the question of why you want to upgrade? For a new user there is likely little reason to upgrade yet and the LTS is supported longest so you can learn the system well first before tackling the issues of a new version that may cause further heartache till the bugs are worked out.
 
It's not so much that Ubuntu is difficult as it is that you can't just sit down in front of it and know what to do. That's not any different than Windows was and if you can imagine sitting down in front of XP, Vista or Win 7 as a first computer experience you would likely have many questions as well. Fortunately for most of us, we lived through the growth of computers so we have taken the learning curve a step at a time. 
 
If you have the time, visit the forums regularly and read posts that sound interesting even if they don't mean much to you. As you see a variety of explanations things will become easy to understand and they'll make sense more as you get perspective from many users. It's not a difficult distro to learn, probably one of the easiest, but it is different. It inherently does require a level of knowledge about it to be comfortable, but so would any other operating system. Patience is key and there is a wealth of knowledge here to assist as you hit roadblocks.

---

### Post by Joshwaa on 2010-10-20
> **TBABill said:**
> 3. Ubuntu being easier...yes there is a definite learning curve, particularly where getting awkward configurations to work regarding drivers. But that also begs the question of why you want to upgrade? For a new user there is likely little reason to upgrade yet and the LTS is supported longest so you can learn the system well first before tackling the issues of a new version that may cause further heartache till the bugs are worked out..

I've never agreed with anything more, the learning curve is hard but now i've learnt about Ubuntu and the power of Ubuntu I rarely have to open Windows.

Seriously, Linux is worth it.

---

### Post by ArgusVision on 2010-10-20
Yes it is possible to upgrade to 10.10, but if your PC is working and usable in 10.04, I would suggest you stay with it for now. Especially if you are a new user. The 10.04 has proven to be more stable and is a Long Term Support (LTS) release. That basically means you will continue to receive updates for 3 years from its release vs. 18 months with a standard release like 10.10. So there is no need to upgrade unless you just want to.
I'll see if there is already a tutorial out there that might help you, other wise I can try to put together some steps to follow if you still want to upgrade.

---

### Post by zdubun on 2010-10-20
Thanks for the encouragement. I shall probably stick to 10.04. However I would really appreciate the guidance how to connect the Dell d530 core 2 duo to the net. Ubuntu 10.04 used to connect fine then suddenly no more. I am attaching  the title of the last thread I posted on this issue. Thanks once again.
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Being forced to use XP because no internet connection]("http://ubuntuforums.org/showthread.php?t=1587063")

---

### Post by zdubun on 2010-10-20
I have followed the instructions for downloading the broadcom driver but no success. Help !!!

---

### Post by jtarin on 2010-10-20
> **zdubun said:**
> I have followed the instructions for downloading the broadcom driver but no success. Help !!!Ok you have followed the instructions for downloading the broadcom driver.....are you having problems downloading? If not,what steps have you taken after downloading? Document your steps taken so that we can help you where you need help. Are you using network manager or WICD?

> If Ubuntu is to be accepted , it should be more easy to use.I agree, however it's not the fault of the Linux community that broadcom has only now open-sourced it drivers for the Linux developers to create a driver for Linus.Broadcom is one piece of hardware that has been most problematic for ease in setup of Linux.

---

### Post by jtarin on 2010-10-20
I'm attaching the "README" from the Broadcom driver package. Any questions after reading...please ask.
> 
Some distros (Ubuntu and Fedora at the least) already have a version of
this driver in their repositories precompiled, tested and ready to go.
You just use the package manager to install the proper package.  If
its available for your distro, this is usually an easier solution. See
the end of this document for further discussion.

---

### Post by zdubun on 2010-10-21
> **jtarin said:**
> I'm attaching the "README" from the Broadcom driver package. Any questions after reading...please ask.

Thanks, I shall try today and let u know in a couple of hours.

---

### Post by coffeecat on 2010-10-21
@zdubun, I see from your other thread that you have the bcm4311 card. It should be easy enough to set up and I'm sorry to see that someone in that thread pointed you to ndiswrapper and Windows drivers for download. That should be unnecessary.

Have a look at this community documentation. It should complement what others have said in this thread.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

You'll see that you don't need ndiswrapper. The Linux driver you need can be downloaded from the Ubuntu repository if you can connect with ethernet. Or, if not, the driver is on the install CD. The page describes how to use the CD as a repository temporarily to get the wireless card working.

---

### Post by zdubun on 2010-10-21
> **coffeecat said:**
> @zdubun, I see from your other thread that you have the bcm4311 card. It should be easy enough to set up and I'm sorry to see that someone in that thread pointed you to ndiswrapper and Windows drivers for download. That should be unnecessary.

Have a look at this community documentation. It should complement what others have said in this thread.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

You'll see that you don't need ndiswrapper. The Linux driver you need can be downloaded from the Ubuntu repository if you can connect with ethernet. Or, if not, the driver is on the install CD. The page describes how to use the CD as a repository temporarily to get the wireless card working.

Shall try it soon and let post the results. Thanks

---

