---
title: "GRUB and grub-legacy"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by fslezak on 2010-08-24
Hello.

I prefer to use grub-legacy in Ubuntu, but I do not want to mess up my install, so how can I do this on my 10.04 machine without forbidding me to boot again?

---

### Post by wilee-nilee on 2010-08-24
Here is a link for you.
[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

Honestly grub2 is easier to use and finds OS that have been resized and moved around the HD, it is the future. If your going by how often you see grub2 issues on the forum you have to remember that this is where people come when they have problems, and it doesn't represent the overall use of grub2, or any inherent problems. Personally I like it much better.

---

### Post by fslezak on 2010-08-24
You're right, but I like the menu.lst file for easy editing.

Is there a way I can make the system then import the menu.lst and any other functions (moved OSes) when it is time for an update?

---

### Post by oldfred on 2010-08-25
If you have some boot settings in menu.lst, you would have to reformat to the grub2 style. But grub2 is so good at finding other systems it is easier to let it find them and then if you want copy those settings into 40_custom and edit at will.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

I added this to turn off prober :
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by Emek on 2010-11-02
Hi guys!

I have migrate from Debian to Ubuntu 10.10 and this is tricky question  because I want to know about Grub2 and mouserate in Debian and Ubuntu  and Grub1 was something like this:

title           Debian GNU/Linux, kernel 2.6.32-5-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.32-5-686 root=/dev/sda1 ro vga=791** usbhid.mousepoll=2**
initrd          /boot/initrd.img-2.6.32-5-686


And it works for me to have 500Hz mouse rate, now I want to know where to put this little thing:
[B] 
usbhid.mousepoll=2

in Grub2 [/B]

Any suggestions? 

P.S.
Don't tell me please to do it in other way because none of another way works for me even like this [http://ubuntuforums.org/showthread.php?t=215981](http://ubuntuforums.org/showthread.php?t=215981)
So I must edit grub to have 500Hz mouse. 

**Thank you for future answer!**

---

