---
title: "Hi Gain Wireless-150N USB (HWDN2) wireless router problems.  Please help!"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by guitar2007 on 2008-12-30
I got this new wireless dish for x-mas, and it seems to work very well with windows xp and vista.  I tried loading this up on Ubuntu for hours last night. I installed netr28u.inf with its .sys file of course using ndiswrapper and it seems to know the driver for the router is installed under admin -> windows wireless drivers, but when i got to Admin -> Network, i have no wireless options at all.  I looked for people with the same problem, and found this. [http://www.mattpacker.com/?p=19](http://www.mattpacker.com/?p=19).  I downloaded the new driver (the .tar.bz2 file) and typed 

tar -xjvf 2008_0718_RT2870_Linux_STA_v1.3.1.0.tar.bz2

as i was told to do... however i just get errors:

tar: 2008_0718_RT2870_Linux_STA_v1.3.1.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I'm new to linux obviously, so I really don't know much about the commands yet at all.  Please help me!  I'm a noob :confused: :D

ps i am unsure of what chipset this usb dish adapter is. 


UPDATE!!  I got the tar.bz2 file extracted, but i can't run make or make install to get the driver and adapter up and running.   Here is my terminal window:

cody@cody-desktop:~$ cd /home/cody/Desktop/2008_0718_RT2870_Linux_STA_v1.3.1.0 cody@cody-desktop:~/Desktop/2008_0718_RT2870_Linux_STA_v1.3.1.0$ make
make -C tools
make[1]: Entering directory `/home/cody/Desktop/2008_0718_RT2870_Linux_STA_v1.3.1.0/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function &#8216;main&#8217;:
bin2h.c:34: error: &#8216;FILE&#8217; undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: &#8216;infile&#8217; undeclared (first use in this function)
bin2h.c:34: error: &#8216;outfile&#8217; undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
bin2h.c:49: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:54: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:57: warning: incompatible implicit declaration of built-in function &#8216;strcat&#8217;
bin2h.c:69: error: expected expression before &#8216;)&#8217; token
bin2h.c:71: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:76: error: expected expression before &#8216;)&#8217; token
bin2h.c:78: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:146: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
bin2h.c:155: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/cody/Desktop/2008_0718_RT2870_Linux_STA_v1.3.1.0/tools'
make: *** [build_tools] Error 2

---

### Post by guitar2007 on 2008-12-30
Anybody out there with even a hint of an idea on what to do?

---

### Post by guitar2007 on 2008-12-30
Hmm... still working on this.

---

### Post by guitar2007 on 2009-01-05
Hello?  Anybody out there with this problem or something similar?

---

### Post by stir-crazy on 2009-02-10
This might or might not help you, but I found this from a product review on Amazon.com.  I have the same adapter so I'll give this method a shot later this week.

> 2. This adapter also works with Ubuntu (Linux) 8.04, using NDISWrapper. The adapter's chipset is the Ralink RT2870. After XP installation, the rt2870.sys and .inf files (for use with NDISWrapper) are available in the Program Files\Hawking\HWDN1 Wireless LAN Card\Driver directory. You can point to rt2870.inf in this directory (on a Windows partition) from Ubuntu's Windows Wireless Drivers tool (or copy the .sys and .inf files to something like a USB memory stick and carry them to an Ubuntu machine). The driver was installed instantly, and the adapter works without rebooting Ubuntu.

---

### Post by stir-crazy on 2009-02-20
Well, I tried ndiswrapper, and though it seems to take the driver just fine (using the WinXP driver), it never seems to recognize that the dish is plugged in.  Pah!

---

### Post by jualin on 2009-07-09
Anybody got this dish adapter to work?

---

### Post by m_a on 2009-12-22
I know this is a little delayed, but I was able to get this to work. I had previously tried all the solutions I could find in the forums but I had the same symptom as [COLOR=Black]*stir-crazy*[/COLOR], where the 2870 driver would install but the hardware would not be recognized. 

My HWDN2 is a rev E, so I figure it uses a different chipset (ie not the rt2870). Using the "net8192su.inf" driver from the installation cd finally solved my problems.

Attached are the driver files. Hope this saves someone some trouble.

---

### Post by trailboss221 on 2010-09-24
> **m_a said:**
> I know this is a little delayed, but I was able to get this to work. I had previously tried all the solutions I could find in the forums but I had the same symptom as [COLOR=Black]*stir-crazy*[/COLOR], where the 2870 driver would install but the hardware would not be recognized. 

My HWDN2 is a rev E, so I figure it uses a different chipset (ie not the rt2870). Using the "net8192su.inf" driver from the installation cd finally solved my problems.

Attached are the driver files. Hope this saves someone some trouble.
so where do i install my .inf and .cat files?

---

### Post by taxiracer55 on 2011-04-16
"""I know this is a little delayed, but I was able to get this to work. I had previously tried all the solutions I could find in the forums but I had the same symptom as [COLOR=black]*stir-crazy*[/COLOR], where the 2870 driver would install but the hardware would not be recognized. 

My HWDN2 is a rev E, so I figure it uses a different chipset (ie not the rt2870). Using the "net8192su.inf" driver from the installation cd finally solved my problems.

Attached are the driver files. Hope this saves someone some trouble. """
 
 
 
 
 
 
Where Do i Put those Files In Backtrack 4?
Or what command do Run.
Thanks in Advance.

---

