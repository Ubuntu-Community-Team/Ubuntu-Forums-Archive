---
title: "Not sure what the problem is. But GRUB loader screen won't show up"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Xephyrind on 2009-04-30
Hi Masters of Linux,

I ran into problem trying to install the new version of Debian 5.0 today with AMD64 architecture. So here's the story, I had 2 hard drives. Both 500GB. I had Windows Vista Ultimate 64bit installed on first hard drive around August 2008. Later on, I installed Debian 4.0 AMD64 on the second hard drive on September 2008, which ran fine with grub loader screen showing up asking me to pick the operating system I want to use. I didn't run into any problem back then. I just had to switch the hard drive priority in BIOS to get GRUB loaded by the system instead of going straight into Windows Vista. Then I decided to remove Debian 4.0 January 2009 from the second hard drive to back up important files for another computer. After this, I switched hard drive priority in BIOS to let Windows Master Boot Loader take over.

Today I bought a new hard drive with 640GB Seagate and decided to install Debian 5.0 AMD64 on this 640GB hard drive, my third hard drive. Toward the end of installation when its installing GRUB onto this hard drive, the system detected Windows Vista and said the message something along the lines, " if this is the only other operating system on your computer then it is probably safe to install GRUB". I clicked yes after reading that. After installation I took out my CD and went into BIOS and put 640GB hard drive on the top priority. I was expecting a blue screen with Debian and Vista/Longhorn to show up as its options, instead, The system went into Black screen with a '_' blinking there and just pretty much stayed in that state. After the typical start up BIOS message, then it goes into that black screen with an underscore sign blinking. About two seconds after it goes into that screen, I see my hard drive light blink for about half a second. After that, I just sit in that screen with that underscore sign blinking there and hard drive LED seems to have gone to sleep after that.

I reinstalled 2x on that same hard drive after that, same thing happened. I thought maybe Debian 5.0.... nah, that's impossible, 5.0's a stable version Linux is pr0 too how's that even possible. But I still decided to try the Debian 4.0 AMD64 installation on my new 640GB hard drive, the one installation I know worked last time, to see what's up. Unfortunately Debian 4.0 AMD64 also ran into the same problem on start up Q_Q... After BIOS message telling me ASUS motherboards are all about Reliability, Compatibility, and Stability, then it goes into Black screen of death with a blinking underscore....

I put down as much details as I could. Help please >.<lll

---

### Post by nandemonai on 2009-04-30
> **Xephyrind said:**
> Hi Masters of Linux,

I ran into problem trying to install the new version of Debian 5.0 today with AMD64 architecture. So here's the story, I had 2 hard drives. Both 500GB. I had Windows Vista Ultimate 64bit installed on first hard drive around August 2008. Later on, I installed Debian 4.0 AMD64 on the second hard drive on September 2008, which ran fine with grub loader screen showing up asking me to pick the operating system I want to use. I didn't run into any problem back then. I just had to switch the hard drive priority in BIOS to get GRUB loaded by the system instead of going straight into Windows Vista. Then I decided to remove Debian 4.0 January 2009 from the second hard drive to back up important files for another computer. After this, I switched hard drive priority in BIOS to let Windows Master Boot Loader take over.

Today I bought a new hard drive with 640GB Seagate and decided to install Debian 5.0 AMD64 on this 640GB hard drive, my third hard drive. Toward the end of installation when its installing GRUB onto this hard drive, the system detected Windows Vista and said the message something along the lines, " if this is the only other operating system on your computer then it is probably safe to install GRUB". I clicked yes after reading that. After installation I took out my CD and went into BIOS and put 640GB hard drive on the top priority. I was expecting a blue screen with Debian and Vista/Longhorn to show up as its options, instead, The system went into Black screen with a '_' blinking there and just pretty much stayed in that state. After the typical start up BIOS message, then it goes into that black screen with an underscore sign blinking. About two seconds after it goes into that screen, I see my hard drive light blink for about half a second. After that, I just sit in that screen with that underscore sign blinking there and hard drive LED seems to have gone to sleep after that.

I reinstalled 2x on that same hard drive after that, same thing happened. I thought maybe Debian 5.0.... nah, that's impossible, 5.0's a stable version Linux is pr0 too how's that even possible. But I still decided to try the Debian 4.0 AMD64 installation on my new 640GB hard drive, the one installation I know worked last time, to see what's up. Unfortunately Debian 4.0 AMD64 also ran into the same problem on start up Q_Q... After BIOS message telling me ASUS motherboards are all about Reliability, Compatibility, and Stability, then it goes into Black screen of death with a blinking underscore....

I put down as much details as I could. Help please >.<lll

Sounds like you've installed grub to the mbr of the first disk. Try booting off your first disk.

---

### Post by Xephyrind on 2009-04-30
I booted off of the first disk and it automatically loads me into Windows Vista without going through the selection of Operating System at all XD

---

### Post by Niniel on 2009-04-30
> After installation I took out my CD and went into BIOS and put 640GB hard drive on the top priority.
Top priority? For booting?
I think this is most likely the reason for your problem. What I would try next is to have the original disk as primary master, the new disk as primary slave, and BIOS settings to boot from the first hd (PM). 
Then reinstall Linux, and Grub. Grub will need to go into the MBR of the first disk (PM).

---

### Post by Xephyrind on 2009-04-30
Regarding priority, I think I might have misused the language.

By the priority I meant, the device list. Basically, I can change the order of the list of the hard drives in BIOS. It seems the drive that's on top of the list is the one read by the system; therefore, if I have a MBR on the windows hard drive and another GRUB on the MBR of the second hard drive. The MBR first on the list of the hard drive will be read first. That's what I meant by that. Not sure if I've cleared it enough. Sowwi for my nubbiness =.=lll

---

### Post by caljohnsmith on 2009-04-30
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your linux desktop (can be any Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by Xephyrind on 2009-04-30
Yes Master~ getting on that right away!~~ will return my result soon /bow

---

### Post by Xephyrind on 2009-05-01
hmm.... Updating news.... I found my GRUB... It is installed on the "second hard drive" referred to my original post on top. The one drive that had linux but got erased to store other files. Here's another question. Debian installer stated that "it's installed GRUB onto the first hard drive (hd0)." How does it determine who's hd0? I originally thought GRUB is suppose to be installed on the same hard drive as the one I install debian/linux on.... However, that apparently isn't the case right now... I am a bit lost. Enlighten me please. Is there anyway to change or choose which drive I want GRUB to be on? thank you...~

---

