---
title: "Try hd(0,0): NTFS5: No wubildr"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by pra.agar on 2010-09-30
Hi,

I have been using ubuntu from past 1 year. First the 9.10 and now upgraded to 10.04 in April, 2010. I installed it using windows 7 wubi installer.

Yesterday night i found some updates as usual in my ubuntu and had updated the same. But this morning when i tried to boot the system by selecting ubuntu in the OS options it started giving me 
"Try hd(0,0): NTFS5: No wubildr" Error in fraction of seconds and the system restart back.

I googled and found a solution @  
[https://bugs.launchpad.net/wubi/+bug/478717]("https://bugs.launchpad.net/wubi/+bug/478717")

that redirected me too a link [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

I did as instructed and my luck it worked fine. Then i tried updating the grub-pc through my sym-package. 

And now again the same problem repeats and the above link instruction also seems to be not solving the issue.

This started from yesterday's ubuntu updates. I have the files{wubildr ,wubildr.mbr} in my windows directory[c:\] as well in my ubuntu dir [C:\ubuntu\winboot] files{wubildr ,wubildr.mbr, wubildr.cfg}.

Please i need a urgent solution as my work is on hold due to it.

Regards
Prateek Agarwal

---

### Post by P4man on 2010-09-30
wubi is at best a way to test ubuntu for a few days. You've used it for a year now, do yourself a favor and do a proper dualboot. These problems happen all too often with wubi.

---

### Post by pra.agar on 2010-09-30
I dont want to loss my existing data and config in ubuntu env..

How do i make it work for some time. and how to make it dual bootable.... 

Please guide me...

---

### Post by P4man on 2010-09-30
This is precisely why I hate wubi, because its hard to fix, its even harder to migrate to a real install and even recovering files isnt trivial.

Anyway, Im no wubi expert, but I think you followed instruction for ubuntu 9.10 and you installed a "wubildr" that may not work with 10.04? Can you still boot windows?  

Alternatively, to access files stored in ubuntu, you can boot from an ubuntu liveCD or USB stick, and then mount the windows filesystem, then mount the wubi filesystem contained inside it. Instructions here:
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

You can then copy whatever files you need to the windows filesystem or an another drive. But temporarily fixing wubi is probably easier.

---

### Post by pra.agar on 2010-09-30
Ya im able to access my Windows 7. I was even able to access ubuntu few min back. if i delete the file from the c dir and then copy paste the one avaible @ the sourceforge site. But that is accessible only once. When i try second time the same problem occurs...

---

### Post by rubing on 2010-12-09
same problem here.  what an enormous piece of junk!

---

### Post by Rubi1200 on 2010-12-09
> **rubing said:**
> same problem here.  what an enormous piece of junk!
Have you read this thread and tried the solutions there?
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by rucker222 on 2011-02-22
Guys, 

I am very new to Linux and Ubuntu so i'm just going to tell you how I got around this problem but would have no idea if it will work for any one else.  

I'm running the 10.4 windows install on my Windows XP laptop and have not had any trouble my self as I have been really slack with the updates. 

I also had this installed on the girlfriends windows 7 notebook who is clearly less slack than I am because she has been keeping on top of the updates.  A few days ago after having done an update she was having the exact same problem. 

After looking at a few different forum threads and not understanding any of it I decided to have a go at something myself.

I had a look through the windows files on my laptop for anything with wubildr in the file name and found the attached files wubildr.mbr & wubildr (if I have managed to attach them correctly that is) and put them onto a thumb drive. I then loaded windows 7 on the girlfriends notebook found the same two files and replaced them with the ones I had just copied from my laptop.

After a restart of her notebook and selecting Ubuntu I still had the same message pop up but this time instead of just going back the the screen asking me if i wanted to run Ubuntu or Windows 7 I was able to continue and load Ubuntu.

As I said, I have no idea if this will work for anyone else but cant see why not if it worked for me :D

---

### Post by bcbc on 2011-02-23
> **rucker222 said:**
> As I said, I have no idea if this will work for anyone else but cant see why not if it worked for me :D

Follow the Permanent Fix from the Wubi megathread that Rubi1200 linked to. It's very simple to do. The reason is that the symptoms of this problem are inconsistent. Some people it fails right away. Others it will fail later after a kernel update (when grub is regenerated). And some have reported it working on and off... 
Also the symptoms can differ between rebooting, grub prompt, or just freezing.

So... save your girlfriend the hassle and fix it right. A lot of effort went into figuring out a solution, it's been tested on multiple releases of Ubuntu (and grub) and it's been performed and confirmed by many many Wubi users.

---

### Post by Rubi1200 on 2011-02-23
Just to reiterate what bcbc has already said, there has been a lot of hard work put in to find solutions for issues with Wubi installs.

Use the Permanent Fix from the [main post]("http://ubuntuforums.org/showthread.php?t=1639198") and make sure to lock the grub packages in Synaptic.

---

### Post by etapomay on 2012-03-14
Just wait for sometime on the screen saying "Try hd(0,0): NTFS5: No wubildr". Grub comes up later without doing anything.

I was getting windows boot loader earlier. Selected Ubuntu and I was stuck with above message.

---

### Post by Rubi1200 on 2012-03-14
Thanks for the input.

Thread closed.

Reason: necromancy

---

