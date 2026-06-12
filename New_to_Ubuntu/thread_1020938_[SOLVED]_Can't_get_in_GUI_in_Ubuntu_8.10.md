---
title: "[SOLVED] Can't get in GUI in Ubuntu 8.10"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by MortenHolst on 2008-12-24
Hi all, I really hope you guys can help me out, as I have spend most of my christmas (arh, but almost), trying to solve it. 

First of all, I'm all new to Linux based OS'. I decided to try it, for the first time, as I got myself a lenovo t400.

(specs, which might be able to clear things out
Prozessor:
Intel Core 2 Duo P8400 2.26 GHz, 1066 MHz Front Side Bus, 3 MB-L2-Cache

Arbeitsspeicher:
2 GB PC3-8500 DDR3-SDRAM 1066 MHz, max. 4 GB 
(2 x 1 GB )

HD:
250 GB SATA, 5.400U/min 
Active Protection System 

Display:
14.1" TFT-Farbdisplay, WSXGA (1440x900) 
CCFL Backlight, 200nits, 16:10, Kontrast 300:1

Grafikkort:
Intel Graphics Media Accelerator X4500MHD
ATI Radeon HD3470, 256MB RAM
(Hybrid Grafik umschaltbar)

Network/Kommunikation:
10/100/1000 Intel 82567LM Ethernetadapter
56k Modem
Intel WLan 5100 a/g/n
Bluetooth 2.0
WWAN Ready (Optional erhältlich: HSDPA Mini PCI Karte (43R9153)
)

Started out by installing 8.04.1. This ran quite good, except I wasn't able to get the wireless internet up and running. My conclusion was, that there didn't excist any drivers for my type of Wlan in 8.04.1, and I therefore updated to 8.10. 
This might have been quite a mistake, as I'm now confronted with a larger problem.

When I boot i start up in the "console mode (?)", there is no GUI, that is. The Ubuntu sign pops up, and after loading it thinks for a while and then proceeds in the console mode. It says:
loading, please wait...
usplash: Setting mode 1152x864 failed
usplash: using mode 1024x768
19+0 records in
19+0 records out
klinit: name_to_dev_t(/dev/disk/by-uuid/whole lot of letters and numbers)
klinit: trying to resume from /dev/disk/by-uuid/same numbers as above
klinit: No resume image, doing normal boot...

Ubuntu 8.10 (login) tty1

Login: _

Thats about it, and I've been searching for a solution for hours, without any luck.

Thanks
Morten

---

### Post by Coder543 on 2008-12-24
login, then type
sudo gdm
enter your password (it will not appear)

---

### Post by igknighted on 2008-12-24
You are correct about your wifi.  That card did not exist when Ubuntu 8.10 was released.  When you get that login prompt at the terminal, could you log in and post the output of the command 'lspci | grep VGA'?

---

### Post by squee on 2008-12-24
It might also help to know how you updated?

Did you run the update manager from the desktop or did you do a fresh install from a disk?

I would suggest doing a fresh install if no-one else can suggest anything that works.


I'd also try "ctrl + alt + F7" from your plain screen. I cant remember what that is on a german keyboard but you should be able to work it out

If they doesnt work, type ```
gdm
``` and see if that works.

Viel Glück!

---

### Post by squee on 2008-12-24
> **Coder543 said:**
> login, then type
sudo gdm
enter your password (it will not appear)

Damn you guys are quick.

I'd try that ^^ which is what I was eluding to but couldnt explain as well.

---

### Post by nynoah on 2008-12-24
Your graphics drivers are most likely messed up.  Sometimes when you upgrade your drivers will need a dependency that is not needed in the other version.  Then when you reboot you get black screen.  It is why every time I install something like Kubuntu, Studio Ubuntu or KDE4 that I always roll back my graphics drivers to non proprietary.  I forget that exact commands for it,  I will have to look it up.  But basically you need to reconfigure your drivers back to something like VGA or Vesa.  Then once that is done reinstall you proprietary drivers again.

---

### Post by nynoah on 2008-12-24
ok when you are booting up get into your Grub menu and type this > sudo dpkg-reconfigure xserver-xorg 

Then reset it to Vesa or VGA.  I find vesa works best.  You will have to go through the whole configuration thing.  basically just hit return for most all of it.  Then choose Vesa for your graphics driver.

---

### Post by MortenHolst on 2008-12-24
Ok, thanks a lot guys, I'll give it a go, with the different proposals. I forgot to say, that I already tried the "sudo gmd" without succes, it just said
gdm[5724]: warning: GDM already running. Aborting!
ctrl+alt+f7 doesn't do the trick either, it just gives me a black screen. (nice detective work btw. squee, I'm Danish though, just bought my laptop in germany, as it's cheaper. Aber danke eben so. I ran the update-manager, as I tried to install the 8.10 earluier on, but it resulted in the same problem, I'm in now.

igknighted, the output is:
00:02.0 vga compatible controller: Intel corporation Mobile 4 series chipset integrated graphics controller (rev 07)
01:00.1 vga compatible controller: ATI tech Inc mobolity radeon HD 3400 series


I'll give it a go with the graphics things and return

---

### Post by abn91c on 2008-12-24
what happens when you just do startx and just for kicks remove compiz also
sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

### Post by MortenHolst on 2008-12-24
After startx it says

Fatal server error:
no screens found
giving up.

Didn't help removing compiz either. But thanks anyway. 
Btw. I might be doing something wrong, when I type 
sudo dpkg-reconfigure xserver-xorg
i get one screen with some framebuffer question, and then just a lot of stuff about my keyboard. 
According to this ([http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)) and nynoah I should arrive at another result

---

### Post by abn91c on 2008-12-24
try this sudo dpkg-reconfigure -phig xserver-xorg

and maybe reinstalling the usplash

---

### Post by MortenHolst on 2008-12-24
Still no luck, I might be missing something though. I'm not sure, wether I'm in the Grub menu, after booting I write my login and password, and get:
"(username)@computername:^$ _"
"sudo dpkg-reconfigure -phig xserver-xorg" doesn't change anything
Will try to reinstall usplash

---

### Post by Coder543 on 2008-12-24
Do you have any important data on that computer? If not you *could* just do a clean install.

If you do have data, you could use the 'cd FOLDER' command to get to your data then 'mv FILENAME /media/DISKNAME' command to move your data to an external drive with the name DISKNAME. or 'mv * /media/DISKNAME' to move *everything* in your current directory to device DISKNAME.

---

### Post by MortenHolst on 2008-12-24
Argh, I'm getting frustrated, which it's way to late for, so I'll call it a day. Thanks heaps for your help everyone, it really encouraged me to continue trying. Will be back with updates.

---

### Post by MortenHolst on 2008-12-24
Coder, I don't think it'd help reinstalling, as I'll probably encounter the excact same problem. I tried to start out with 8.10, and therefore have a live cd, but it just brings me in the same situation, as I am now.

---

### Post by dallas8101 on 2008-12-24
I am having much the same experience.  I upgraded to 8.10 from 8.04.  It comes to the "starting bluetooth" message and hangs for a long time before going to a black screen.  I don't have a bluetooth device on the system.

The only way out is to push the power button, which triggers a shutdown, which then hangs on trying to stop the bluetooth.  I have to hold in the power button to finish the power down. I also tried the dpkg-reconfigure and I also only get questions about the keyboard.  I have to do an Esc during boot to get to "recovery mode" to do anything.

After a little google searching I found it was my Haupaugge PVR-USB2 causing the hang.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927)

---

### Post by MortenHolst on 2008-12-25
Yay, I got it to work out. The switchable graphics was the thing that caused the trouble. All I had to do was entering the bios menu with F1 and change to discrete graphics. Awesome, thanks a lot you guys.

[http://ubuntuforums.org/showthread.php?t=922428&highlight=t400](http://ubuntuforums.org/showthread.php?t=922428&highlight=t400)

---

### Post by Troll_the_Great on 2008-12-25
Glad we could help.Now please mark the thread as "solved", using the thread tools at the top of the page, so others can benefit from your experience and to prevent users to waist their time reading an already solved problem.
Cheers and Merry Christmas!

---

