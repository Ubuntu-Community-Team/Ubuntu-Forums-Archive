---
title: "Scrambled boot screen?"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by kuraykillua on 2010-07-29
I installed Ubuntu yesterday, ran into quite a few problems but I managed to fix all of the bigger ones, and so far I LOVE Ubuntu. Way better than Mac or Windows IMO.
However there's also a few smaller problems I'd like to take care of, and I decided to start a separate thread for each one.
So when I load Ubuntu, the loading screen is scrambled. It's black with random green dots in weird patterns that make no sense. Then the login screen comes up and everything's fine. I really like the look of the loading screen and I'd like to fix it. So to be precise, it's not the Grub2 screen. It's the one after that, where it's a purple background with the word Ubuntu in the middle and some color-changing dots under that. I'm not sure what that screen is called.
I've searched the forums, and I've read ones that recommended changing the Startupmanager's resolution. I've tried that, with no difference, as I believe that applies to the grub screen... not the one I'm talking about. That screen was perfectly fine when I installed it, and I'm not sure what I did, if anything, to mess it up. Any ideas? Thanks!

PS: How do I change a thread's prefix to solved?

---

### Post by roger_1960 on 2010-07-29
Hi

Click on thread tools link at the top and select "mark as solved"

I have the same display problem with an old laptop - garbled display until the login dialog appears.  No idea how to cure it though....

---

### Post by kuraykillua on 2010-07-29
Ok so far I've managed to find out that it's called a splash screen. I've attempted to change the splash screen, and now it's just scrambled with different colors.

---

### Post by kuraykillua on 2010-07-29
So I've fixed the problem after 6 hours of messing around.
The problem was most likely that the resolution display after installing my driver (nVdia 9800MGT), some system file changed and thus the resolution had problems.
To fix the problem, I found the following and followed the instructions
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Not exactly the same problem, but I gave it a shot an that fixed my problem as well.
Before I also had the problem which the virtual terminal was scrambled, and responded while I typed stuff but nothing was legible.

Here's the steps in case the website doesn't work:
[COLOR=#008080][I]
Open Terminal, type the following:
sudo apt-get install v86d[/I][/COLOR]
Then
[COLOR=#008080][I]gksu gedit /etc/default/grub
[/I][/COLOR]
 - Replace the following  line (line number 9):
 
 [COLOR=#008080]*  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*[/COLOR]
 
 with  this one:
 
 [COLOR=#008080]*GRUB_CMDLINE_LINUX_DEFAULT="quiet  splash nomodeset  video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"*[/COLOR]
 
 - Replace the following line (line number 18):
 
 [COLOR=#008080]* #GRUB_GFXMODE=640x480*[/COLOR]
 
 with this one:
 
 [COLOR=#008080]*  GRUB_GFXMODE=1280x1024*[/COLOR]
Then
[COLOR=#008080]*gksu gedit /etc/initramfs-tools/modules*[/COLOR]
 
  When the text window appears, add the following line at the end of the  file:
 
 [COLOR=#008080]* uvesafb  mode_option=1280x1024-24 mtrr=3 scroll=ywrap*[/COLOR]
Then
Hit the ALT+F2 key  combination, paste the following command and check the "Run in terminal"  option:
 
 [COLOR=#008080]* echo  FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash*[/COLOR]
 
 ...a terminal window will appear for a second or two. The terminal  window will automatically close!
Then
[COLOR=#FF6600][/COLOR] Hit the ALT+F2 key  combination, paste the following command and check the "Run in terminal"  option:
 
 [COLOR=#008080]* sudo  update-grub2*[/COLOR]
 
 ...a terminal window will appear.  Enter your password when asked, hit the Enter key and wait for the  command to finish. The terminal window will automatically close!
Then
[COLOR=#008080]*sudo update-initramfs -u*[/COLOR]
 
 ...a terminal  window will appear. Enter your password when asked, hit the Enter key  and wait for the command to finish. The terminal window will  automatically close!
Then, Reboot.

-------
All of the above was copied directly from the site. Credit goes to Marius Nestor who wrote it.

---

