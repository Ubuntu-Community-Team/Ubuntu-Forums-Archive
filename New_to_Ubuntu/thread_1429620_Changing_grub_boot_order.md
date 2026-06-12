---
title: "Changing grub boot order"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by 6SPEED on 2010-03-14
hello everyone, I installed Ubuntu 9.10 64bit yesterday and am having a hard time configuring grub. This Is my first time even using a linux based OS so be easy on me. I want to change the boot order on grub so that my windows 7 is the default. I've read alot about how to fix this but I'm stuck. I've looked everywhere for the menu.lst file and it's nowhere to found. Also I read to boot into my LiveCD and look there but ever since I installed Ubuntu when I put my LiveCD in and boot up it doesn't boot from it, it just loads grub like normal. Any help would be appreciated, thanks in advance.

---

### Post by steve-shinn on 2010-03-14
menu.lst does not exist with grub2 it's been replaced with grub.cfg ..... which you shouldn't edit. Instead edit etc/defualt/grub and then update grub (or reboot)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by audiomick on 2010-03-14
9.10 uses grub2, which doesn't use the menu.lst file anymore. Here is some reading:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

And I got these from a post from sisco311 [_here_]("http://ubuntuforums.org/showpost.php?p=8776107&postcount=9")

[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")
[The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by 6SPEED on 2010-03-14
Thanks everyone for the quick response. I downloaded startup manager and everything is perfect now. thanks again.

---

### Post by Robledo on 2010-03-14
Hi, 

if I change (update) grub to grub2, would that change the booting order? As a beginner it tooked me quiet some time to boot windows first. What's the benefit of grub2? I use Ubuntu and Kde. Thanks you from Austria. ;)[FONT=Verdana] el robledo[/FONT]

---

### Post by ershibbu on 2010-03-14
guys i can't understand ...
plz give only the way via i change my boot order ..
n want some delete also...plz

---

### Post by markmaus on 2010-03-14
Below are some more targeted instructions to fix your problem than simply directing you into the GRUB manual page.  Since this is your first experience with Linux, I'll try to tell you every step in detail.  I had the same problem as you and this fixed it for me.

Boot into Linux and open a terminal from the menu: Applications/Accessories/Terminal

Type: "sudo nano /etc/default/grub" (without the quotes) and hit ENTER.
Then enter your password.

Arrow down to the third line that says
GRUB_DEFAULT=0
and change it to 
GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda1)"  (with the quotes)

(This is assuming a typical install where your Win7 boot partition is the first partition of the first hard drive, if it's on the second partition of the fourth hard drive it would be .../dev/sdd2, etc.)

Once you have made that change, hit:
CTRL x  (this will exit the nano editor)
y       (this will save the changes made)  
ENTER   (this will leave the file name as grub)

Now you must run the following command in a terminal to have this change written to the grub.cfg file

sudo update-grub  (hit ENTER and type password if prompted)

Now you can look in the grub.cfg file to make sure the changes were applied, using the command:
"sudo nano /boot/grub/grub.cfg"  (without the quotes)

After viewing it make sure to exit this file without making any changes.
Or you can just re-boot the computer without looking at the grub.cfg file and see if Win7 is now the default choice. 

Good luck and welcome to Linux!

Ps.  Grub (legacy) used to be much simpler to edit, but now Ubuntu 9.10 uses Grub2 which is quite a bit more complicated.  (Not an improvement IMHO)  The file you were looking for, menu.lst is no longer used.  Hopefully Grub2 will implement some kind of GUI to enable simple boot order changes like this.

---

### Post by audiomick on 2010-03-14
> **Robledo said:**
> Hi, 

if I change (update) grub to grub2, would that change the booting order? As a beginner it tooked me quiet some time to boot windows first. What's the benefit of grub2? I use Ubuntu and Kde. Thanks you from Austria. ;)[FONT=Verdana] el robledo[/FONT]
Servus
It wont change the boot order as such, but it would probably default to booting Ubuntu first.

Grub 2 is a newer version, and, from what I have read, does offer some advantages. However I haven't altered anything on my grub, and don't know exactly what the advantages are.

If you are happy with your setup, just leave it. When you do a fresh install, which you most likely will do one day, it will be updated then.

@markmaus : I haven't looked at it yet myself, but I think startup manager offers a good GUI alternative for setting up grub.

---

### Post by markmaus on 2010-03-14
audiomick,
I just installed startup-manager.  It is easily found in Synaptic.  It works great!  Thanks, this greatly simplifies things.
Mark

---

