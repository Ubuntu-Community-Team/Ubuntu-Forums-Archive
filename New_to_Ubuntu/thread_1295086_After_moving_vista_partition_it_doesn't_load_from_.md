---
title: "After moving vista partition it doesn't load from grub"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by HungryOcopus on 2009-10-19
This might be a problem more related to vista itself than grub, but I thought i'd ask here just in case it isn't. I have a dual boot with ubuntu and vista.

I recently realigned a couple of my partitions with gparted, my main vista partition which was on c: (there was some extra space immediately in front of it, and I didnt realise extending it into that would move the whole thing left), and on my second drive I have a data partition and my ubuntu partition (I grew the ubuntu partition without any problems).

Although my ubuntu partition works fine from grub, and I can even access all my vista and data partition files from it, when I try to start vista from grub it hangs at 'starting up...'. I think it may be doing something, because my fan goes crazy, but my hard drive light doesn't blink at all. I'v tried waiting for a good hour or two and nothing happens still.

Any help or advice would be much appreciated, I can provide more information, but I'm a real noob with ubuntu so please bear with me!

---

### Post by louieb on 2009-10-19
Before Vista MS an Microsoft OS  started 63 sectors from the start of the partition.  The 63 sectors is called the boot sector or volume boot record (VBR). The VBR is similar to the  MBR if function. 

In Vista and win 7 the VBR is 2048 sectors long.  When resizing a Vista  partiton to the left Gparted needs to be told to preserve  that length.

Might want to look at [http://www.uluga.ubuntuforums.org/showthread.php?p=7816261](http://www.uluga.ubuntuforums.org/showthread.php?p=7816261)

Long thread but at least look at post #25 and #17. 

The only fix I've seen is to boot the Vista recover cd to the repair console and run ```
bootrec.exe /fixboot
``` Haven't seen anybody say if works or not.   [Bootrec.exe tool Vista (MS support)]("http://support.microsoft.com/kb/927392")

---

### Post by Paddy Landau on 2009-10-19
Also, there are various warnings that manipulating a Windows partition with GParted can screw things up. Not everyone gets that problem, but be warned.

If you want to move a Windows partition, use the Windows built-in partition manager to do that, then use GParted to manipulate the remaining partitions.

---

### Post by Zimmer on 2009-10-19
Suggested reading..
[http://www.multibooters.co.uk/](http://www.multibooters.co.uk/)

[http://www.multibooters.co.uk/cloning.html](http://www.multibooters.co.uk/cloning.html)

---

### Post by HungryOcopus on 2009-10-19
> **louieb said:**
> Before Vista MS an Microsoft OS  started 63 sectors from the start of the partition.  The 63 sectors is called the boot sector or volume boot record (VBR). The VBR is similar to the  MBR if function. 

In Vista and win 7 the VBR is 2048 sectors long.  When resizing a Vista  partiton to the left Gparted needs to be told to preserve  that length.

Might want to look at [http://www.uluga.ubuntuforums.org/showthread.php?p=7816261](http://www.uluga.ubuntuforums.org/showthread.php?p=7816261)

Long thread but at least look at post #25 and #17. 

The only fix I've seen is to boot the Vista recover cd to the repair console and run ```
bootrec.exe /fixboot
``` Haven't seen anybody say if works or not.   [Bootrec.exe tool Vista (MS support)]("http://support.microsoft.com/kb/927392")

I tried that with no luck. I also tried some of the other tools on the vista recovery disk (repair your computer, startup repair, etc) and trying to boot into safe mode (it didn't) without any difference.

Can anyone tell me what exactly happens when 'starting up...' occurs on the screen? I notice it happens when I boot ubuntu too, so I thought it may be something grub does.

---

### Post by Paddy Landau on 2009-10-19
Have you tried to reinstall grub?

If that still doesn't work, then I fear that your Windows partition might have been corrupted, and you'll have to reinstall Windows. As I mentioned earlier, grub is unreliable for manipulating Windows partitions.

---

### Post by HungryOcopus on 2009-10-19
> **Paddy Landau said:**
> Have you tried to reinstall grub?

If that still doesn't work, then I fear that your Windows partition might have been corrupted, and you'll have to reinstall Windows. As I mentioned earlier, grub is unreliable for manipulating Windows partitions.

I just tried reinstalling grub and no change. I guess I'll have to depend on ubuntu for now, as I left my vista disk abroad when I moved. Maybe I'll give windows 7 beta a try.

---

### Post by mikechant on 2009-10-19
> I've tried waiting for a good hour or two and nothing happens still..

After moving a Vista partition with Gparted I had to wait about 3 hours (with no real signs of progress) for Vista to boot next time, but it did eventually boot sucessfully and was fine after that. I'd suggest leaving it overnight.

---

### Post by louieb on 2009-10-19
> **HungryOcopus said:**
> ...Can anyone tell me what exactly happens when 'starting up...' occurs on the screen? I notice it happens when I boot ubuntu too, so I thought it may be something grub does.

Your thinking is right - thats a message from GRUB.

---

### Post by HungryOcopus on 2009-10-19
> **mikechant said:**
> .

After moving a Vista partition with Gparted I had to wait about 3 hours (with no real signs of progress) for Vista to boot next time, but it did eventually boot sucessfully and was fine after that. I'd suggest leaving it overnight.

I was thinking this too. As I mentioned, my fan goes crazy, which it only does when the processor is doing a lot (it goes quiet fairly quickly when I leave the computer without any apps running). I didn't want to leave it on for too long, simply because my fan would go at full speed, and I worry it will wear it down over the course of many hours, but if it worked for you then I will definitely try it.

---

### Post by Mark Phelps on 2009-10-19
> **HungryOcopus said:**
> I just tried reinstalling grub and no change. I guess I'll have to depend on ubuntu for now, as I left my vista disk abroad when I moved. Maybe I'll give windows 7 beta a try.

GRUB's not going to fix Vista bootloader problems. The only thing that is KNOWN to fix it is what you've already tried -- Startup Repair from a Vista DVD or recovery CD.

As to Windows 7, the release version comes out in a few days; so if you want to use that, you would do better to wait and get that version.  The RC version will be time limited in a few months, and I believe the Beta already is.

---

### Post by HungryOcopus on 2009-10-20
I tried waiting at the 'starting up...' screen for many hours (left it on while I went out for about 3-4 hours) and no sign of any change, so I guess that doesn't work for me.

I have one question though about installing windows 7 which it seems I'll have to do. Should I format my C: drive from dos before I install it or will this in some way affect my ubuntu boot or partition? I'm not sure if windows 7 will allow me to specifiy where I want to install it.

Just to clarify again, I have two hard drives, C: and E: with Ubuntu existing on a seperate partition at the end of E: (the first half of E: is just data like music and movies). C: was where I had vista. Thanks for help everyone.

---

### Post by louieb on 2009-10-20
> **HungryOcopus said:**
> I'm not sure if windows 7 will allow me to specifiy where I want to install it.
Yes it will. Been a couple of months since I installed it. But I had a partition set up and specified install it there. IIRC use the custom install option.
> 
Just to clarify again, I have two hard drives, C: and E: with Ubuntu existing on a seperate partition at the end of E: (the first half of E: is just data like music and movies). C: was where I had vista. Thanks for help everyone.Are you sure you have two drives? What windows calls a drive - most would call a partition. c: and e: could be two partitions on the same drive. 

Really don't want to guess. Please use the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file it creates in your next post.

---

