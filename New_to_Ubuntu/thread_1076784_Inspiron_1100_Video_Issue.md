---
title: "Inspiron 1100 Video Issue"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by pstrany on 2009-02-21
Hi;

I apologize for generating yet another thread on the Dell Inspiron laptop, but I've searched, and tinkered, and edited, and re-installed (6 times so far) and nothing seems to help.

Here's the deal.  I have a Dell Inspiron 1100.  I'm trying to installed 8.10 as the sole operating system.  I've successfully installed 8.10 on several Dell desktops, and I wanted a mobile Ubuntu system to play with. Mind you, I am a complete Linux neophyte.

It took two installs to get to a point where I could actually see anything.  Under XP, my screen resolution was 1024x768, and filled the screen.  The current resolution (one of two choices under screen resolution) is 800x600, but the video is limited to about 2/3 of the full screen, and instead of being just a smaller version of the desktop, it is more like looking at the desktop through a partially closed window - many windows are cut off at the tops and sides.  

I've updated the BIOS from A02 up to A32, I've edited the xorg.conf file several times using different suggestions from various threads, but each time leads to a video crash, in several cases requiring a full re-install to get anything back at all.  I've tried in vain to find a 915resolution, which purportedly will fix this problem.

So, is there a solution to the problem?  One suggestion I've seen is to install an older version of Ubuntu, such as 7.10.  I've found a few threads that offer suggestions on adding/changing lines in the xorg.conf file, but I've tried all I found with no joy.

Anybody else manage to actually get an Inspiron 1100 to work with 1024x768, full-screen graphics? 

Thanks for your time,

Paul

---

### Post by loafkin on 2009-03-14
I also had problems trying to get 8.10 to work with my Inspiron 1100. I tried both the live CD and alternate install, and couldn't even get through the installation. I also tried the alternate install of 8.04, however It kept crashing on me at startup. I did, however, get 7.10 to work... There are a few issues... first, use the alternate install, it just saves headaches. Second, you'll have to manually configure xorg.conf to use the i810 drivers, as well as manually input the monitor specs. 3rd, I had to edit grubs boot menu to remove the splash screen. My computer works just fine at 1024x768 even with advanced graphics turned on... though it slows my computer down some.

---

### Post by pstrany on 2009-03-15
Thank you very much for your reply.  I actually tried 7.10 as an install (that was suggested, though with somewhat less detail, in another thread) but had no success.  I'll have to find the alternate disk image and give it a whirl.  

Could you post the relevant sections of the xorg.conf file.  I think I can figure out how to edit the file (I did it once - then had to re-install the system because it trashed everything) but it would be helpful to have the changes so I don't have to experiment with them.

Also, what is a "grubs boot menu" and how do I edit that?  

Thanks!!

Paul

---

### Post by sidewinder12s on 2009-03-21
Hey, i have the Same laptop running right now with 8.10. I had the same problems with mine.

Do you have the Intel Motherboard with the Video card that has an Error in the Firmware? that is what my Problem was so i had to Delete some file in Failsafe Terminal. Can you get to the Log in Screen?

If the Motherboard is the problem then you just need to install 8.10 in Graphics Safe Mode and set the Video stuff to None. thats about the only advice i can give on Ubuntu since i just switched from XP. haha

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)    Bottom of the Page.

---

