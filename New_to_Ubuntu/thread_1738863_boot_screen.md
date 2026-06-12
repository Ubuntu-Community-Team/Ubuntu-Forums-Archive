---
title: "boot screen"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-25
yesterday,i had started up my lappy and saw that the boot screen (the one with the pink background and says ubuntu with the dots going around) was extra huge and pixelated and it just made me feel uncomfortable, anyone knows how to fix it ?

---

### Post by FormatSeize on 2011-04-25
I, too, would like to change this. From some things that I've read, though, it would be rather hard to do since Ubuntu doesn't use usplash during booting anymore, but rather some other thing that I can't remember right now.

It was changed to get the boot time to under ten seconds. I suppose it's not compatible with usplash, which I found out when I tried to replace that with the splash screen for 9.10 last night to no avail.

---

### Post by mr.farenheit on 2011-04-25
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by neil_1 on 2011-04-26
> **mr.farenheit said:**
> [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

i tried that but now its BIGGER THAN EVER :shock:

edit
boot time also takes a lot more time :(

---

### Post by yash0406 on 2011-04-26
[COLOR=Black][COLOR=#FF6600]**Step 1:**[/COLOR] Hit the ALT+F2 key combination, paste the following command and check the "Run in terminal" option:
 
 [COLOR=#008080]* sudo apt-get install v86d*[/COLOR]
 
 ...a terminal window will appear. Enter your password when asked, hit  the Enter key and wait for the package to be installed. The terminal  window will automatically close!

[COLOR=#FF6600]**Step 2:**[/COLOR] Hit the ALT+F2 key combination, paste the following command and check the "Run in terminal" option:
 
 [COLOR=#008080]* gksu gedit /etc/default/grub*[/COLOR]
 
 ...enter your password when asked and hit the Enter key.
 
 - Replace the following line (line number 9):
 
 [COLOR=#008080]* GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*[/COLOR]
 
 with this one:
 
 [COLOR=#008080]*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"*[/COLOR]
 
 - Replace the following line (line number 18):
 
 [COLOR=#008080]* #GRUB_GFXMODE=640x480*[/COLOR]
 
 with this one:
 
 [COLOR=#008080][I] GRUB_GFXMODE=1280x1024

[/I][/COLOR]Save the file and close it!
 
 [COLOR=#FF6600]**Step 3:**[/COLOR] Hit the ALT+F2 key combination, paste the following command and check the "Run in terminal" option:
 
 [COLOR=#008080]* gksu gedit /etc/initramfs-tools/modules*[/COLOR]
 
 When the text window appears, add the following line at the end of the file:
 
 [COLOR=#008080]* uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap*[/COLOR]

Save the file and close it!
 
 [COLOR=#FF6600]**Step 4:**[/COLOR] Hit the ALT+F2 key combination, paste the following command and check the "Run in terminal" option:
 
 [COLOR=#008080]* echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash*[/COLOR]
 
 ...a terminal window will appear for a second or two. The terminal window will automatically close!

[COLOR=#FF6600]**Step 5:**[/COLOR] Hit the ALT+F2 key combination, paste the following command and check the "Run in terminal" option:
 
 [COLOR=#008080]* sudo update-grub2*[/COLOR]
 
 ...a terminal window will appear. Enter your password when asked, hit  the Enter key and wait for the command to finish. The terminal window  will automatically close!

[COLOR=#FF6600]**Step 6:**[/COLOR] Hit the ALT+F2 key combination, paste the following command and check the "Run in terminal" option:
 
 [COLOR=#008080]* sudo update-initramfs -u*[/COLOR]
 
 ...a terminal window will appear. Enter your password when asked, hit  the Enter key and wait for the command to finish. The terminal window  will automatically close!

[COLOR=#FF6600]**Step 7:**[/COLOR] Reboot your computer. When the system starts, you should see a better looking Ubuntu logo!
[/COLOR]

---

### Post by neil_1 on 2011-04-26
> **yash0406 said:**
> [COLOR=Black]**..........**sh. The terminal window  will automatically close!

[COLOR=#ff6600]**Step 7:**[/COLOR] Reboot your computer. When the system starts, you should see a better looking Ubuntu logo!
[/COLOR]
thats what mr.farenheit posted , and the plymouth became worse :(

---

### Post by neil_1 on 2011-05-02
*bump*
no one ?

---

