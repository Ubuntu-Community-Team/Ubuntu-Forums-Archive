---
title: "nvidia wont load after update"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-24
Computer seems like it is going to boot, and then hangs.

After several trouble shoots etc, I decided to take out the video card, and try on board video card.  It booted ok.

It gave me a nvidia error.  It gave me several options such as restart x, low session etc
> 
Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this. 

(EE) NVIDIA:Failed to load the NVIDIA kernel module. Please check your 
(EE) NVIDIA: system's kernel log for additional error messages.
(EE)Failed to load module "nvidia" (module-specific error,0)
(EE)No drivers available

Then, I get
> 
What would you like to do?
Run Ubuntu in low graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to console login
Restart X

I wanted to see if there is an update for nvidia, or if I can update the computer one more time.  I chose low graphics mode for one session.  Nothing happened.  It just went black screen.

In a nutshell, a few weeks ago, I got an update, I ignored it.
Then, I got another update reminder yesterday.  I accepted it.  

And, then the one I ignored a few weeks back popped up again.  I accepted it.  Now, nvidia drive wont load, because of that I cant access the computer via monitor.

please, advise. Thank you.

---

### Post by 007casper on 2011-07-24
All other options failed. 

I tried all of them. It will seem like it is going to console but it would disappear.  

As a last resort, I chose "Reconfigure graphics", and that option worked on the old monitor.

It settled for old factory settings without nvidia.  I turned off the computer.  Powered off all the way.

However, I need my nice size monitor.  So, I needed to make the graphics card work.

So, I hooked up my graphics card that works with nvidia drive.  I figured it would default low graphics, and I can restarted the nvidia graphics drive.  However, I have the same problem.  It just doesnt work. 

??

---

### Post by 007casper on 2011-07-24
on the old monitor I did
> sudo apt-get install nvidia-current

then as root
> sudo nvidia-xconfig

hooked up the video card.  It doesnt boot.  I cant even get console login.

???

---

### Post by 007casper on 2011-07-24
somehow, it posted twice.  Sorry.

on the old monitor I did
> sudo apt-get install nvidia-current

then as root
> sudo nvidia-xconfig

hooked up the video card.  It doesnt boot.  I cant even get console login.

???

---

### Post by 007casper on 2011-07-25
try these two links
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by darknuts on 2011-08-26
Did you ever solve the problem? Can you tell me how?

---

### Post by 007casper on 2011-08-27
I posted the links, please follow those.  

> try these two links
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

They are really good links regarding this issue.

However, the only way I got it working was trying it one at a time - all the variables.  It took a full day to fix this issue.  I hoping next time, I can fix it under ten minutes.

my posting on one of the urls
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=007casper&page=51](http://ubuntuforums.org/showthread.php?t=1743535&highlight=007casper&page=51)

[http://ubuntuforums.org/showthread.php?t=1743535&highlight=007casper&page=52](http://ubuntuforums.org/showthread.php?t=1743535&highlight=007casper&page=52)
> 
your nvidia thread was super.  I cant thank you enough!!! Cheers!

I tried all variables one at a time.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\"
and it didnt work.

but for me vga=0x101 worked.  It posts a funky message during boot.  I got to find out what it says during boot.  It also boots slower than before.  However, it works.  Thats what matters.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=0x101"
```

GRUB> echo $linux_gfx_mode
echo $gfxmode
 set gfxmode=2560x1600
load_video (this line didnt work for me)
insmod gfxterm
 GRUB> vbeinfo

```
append/adding a vga=xxx, where xxx is the mode. 

thank you.

---

