---
title: "NVIDIA 7300LE. No GUI. Terminal Screen"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by YfoMp5QBh2 on 2010-08-31
Hi All,
 
I am new to Ubuntu 10.04 lucid lynx, and just started using recently. I want to create a HTPC using a Dell Dimension 9150 with LIRC, MythTV, and XBMC. I have searched the forums with no luck as to solve the issue so I hope someone can help.
 
I intalled XBMC to find that the mouse pointer wasnt moving correctly (sorta jerky, delayed movement), and I read on WIKI in the HOWTO that I should install the Nvidia drivers in the terminal.
 
I did this and as soon as I rebooted I got the black terminal screen prompting me to login but with no GUI. So far I have been following this thread below (This problem also occurred when I tried to turn on the desktop effects to enhanced whereby Ubuntu prompts you to update the display drivers):
 
[http://ubuntuforums.org/showthread.php?t=1140291&page=3](http://ubuntuforums.org/showthread.php?t=1140291&page=3)
 
I believe I need to reconfigure the Xserver? or do something like "sudo nvidia-xorg.conf" but I have tried most of the commands in the above thread with no luck. Finally I tried "sudo rm-nvida" (or something along those lines) to prompt the removal of the drivers, but the terminal still comes up and now when I try "startx" it gives me a blank screen and my monitor says "no Input".
 
sorry about the lack of details in term of the commands I have used I'm still really new. Can someone help please? I am at my whits end :(

---

### Post by hhh on 2010-08-31
Troubleshooting video problems can be a real pain in the rear and I don't have the experience to help with that, but no one else has given any advice, so...

Lucid should automatically detect and prompt you to install video drivers, why it didn't I don't know (or maybe it did immediately after install and you ignored it but didn't do it manually later). Is your install new enough that you can just rerun the Live CD installer without losing too much in the way of personal files? Or else mount your home folder from the Live CD and download files to a USB drive and then reinstall?

Maybe now that one person has answered others will jump in to help, that often seems to be the case here.

---

### Post by YfoMp5QBh2 on 2010-09-01
Hi There,
 
Thanks for responding so quickly! Everyone seems to be very helpful in these forums.
 
It is a brand new installation of Ubuntu 10.04 on a new computer so is sorta like a blank canvas, so not worried about losing any files at this point.
 
I did try a fresh installation but this is the second time this has happened. The first time the update manager came up and prompted to download the drivers necessary, thats what happened when I wanted to enable the desktop effects.
The second time this happened was after another fresh installation. I was following the HOWTO WIKI about installing XBMC. After XBMC had been installed, the HOWTO said to run "sudo apt-get...." and something to do with installing/updating the Nvidia driver.
 
On both occasions I got the black terminal screen, which is when I did "sudo rm-nvidia...ect" but after I used "startx" the screen goes blank and says "no input". The person in the above post had to manually add the drivers using a flash drive.
 
**_Possible solution?:_** fresh install of Ubuntu (again) but can someone please tell me how to install the correct drivers for the Nvidia Geforce 7300 LE without this error?

---

### Post by YfoMp5QBh2 on 2010-09-01
Just to clarify the command I used was "sudo rm /etc/X11/xorg.conf" and then tried "startx" which gave me the blank screen.

---

### Post by ellgor on 2010-09-02
Hi,

I found this guide thats easy to follow and works:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by YfoMp5QBh2 on 2010-09-03
I'll give ti a shot, thanks Ellgor. However since I'm a noob hopefully you'll indulge me further.

With regards to step 1), I am still stuck on the terminal screen. What code would I have to enter to download the drivers?

Should I completely re-install Ubuntu then follow your guide?

---

### Post by realzippy on 2010-09-03
Assuming nouveau is still blacklisted,but generally
confused about your machine's status....you removed xorg.conf,so no nvidia-driver will start(If it is still installed;you seem to have run some "remove" commands).Anyway,run

```
sudo nvidia-xconfig
```

what creates new xorg.conf or complains about not installed nvidia-driver.
Then reboot ...... (sudo reboot)

Or (drivers not installed,not correctly installed)......:

According to nvidia your 7300 le is supported by the 256.xx driver?Any reason why not using this?
Ok,stuck on terminal you get it by typing:

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/256.53/NVIDIA-Linux-x86-256.53.run
```
may take a while...when finished:

stop XBMC (Admit I never used XBMC,do not know how to stop it...but that is necessary):

```
sudo service xbmc-live stop
```
does not work?Try:
```
sudo /etc/init.d/xbmc stop
```


run the installer:

```
sudo sh NVIDIA-Linux-x86-256.53.run --no-distro-scripts
```


"YES" to all questions during install

```
sudo reboot
```

---

### Post by YfoMp5QBh2 on 2010-09-05
Hi All, Here's where I'm up to.

I followed realzippy's instructions, installed the Nvidia drivers. However now when Ubuntu starts I hear the startup noise but theres nothing on my screen (my samsung tells me no input)
I hear Ubuntu play the startup/welcome noise through my speakers but there is no screen? I suppose that Ubuntu GUI has started but its just not being displayed on the screen?

If I press Ctrl+F1 my samsung still can display terminal screen though (full screen). I am using my Samsung TV connected using a DVI (from computer) to HDMI cable (TV).

---

### Post by realzippy on 2010-09-05
Log in at terminal screen and create the nvidia-bug-report file to attach it here.

```
sudo nvidia-bug-report.sh
```

File (will be in your user's directory) contains xorg.conf and X log file,so we get an idea whats wrong...

---

### Post by YfoMp5QBh2 on 2010-09-06
Hi All,

I tried using a VGA cable to hook up the PC with the TV and this confirmed what I said in my last post. I can now see the GUI screen when using the VGA port, but not through the DVI port.

I ran "sudo nvidia-bug-report.sh" and this produced the following log file [http://pastebin.com/SpbGVTPj](http://pastebin.com/SpbGVTPj)

---

### Post by realzippy on 2010-09-06
Do you have 2 samsung monitors connected?


[I](--) Sep 06 15:13:15 NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0:
(--) Sep 06 15:13:15 NVIDIA(0):     SAMSUNG (CRT-0)
(--) Sep 06 15:13:15 NVIDIA(0):     SAMSUNG (DFP-0)
(--) Sep 06 15:13:15 NVIDIA(0): SAMSUNG (CRT-0): 400.0 MHz maximum pixel clock
(--) Sep 06 15:13:15 NVIDIA(0): SAMSUNG (DFP-0): 165.0 MHz maximum pixel clock[/I]

---

### Post by realzippy on 2010-09-06
Anyway,you could add 

[B]Option         "UseDisplayDevice" "DFP-0"
[/B]

to your xorg.conf's "device" section to force use of DFP-0...:

```
gksudo gedit /etc/X11/xorg.conf
```

opens the file with admin privileges.
Make "device"section look like:

[I]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "UseDisplayDevice" "DFP-0"
EndSection
[/I]
and change *HorizSync* ("monitor" section) from:  

*28.0 - [COLOR="Red"]33.0[/COLOR] *

to:

28.0 - 70.0


exit file saving changes.Reboot.

If this should mess up the GUI,simply delete xorg.conf and make a new one (you already know):

```
sudo rm /etc/X11/xorg.conf
      sudo nvidia-xconfig
```

---

### Post by YfoMp5QBh2 on 2010-09-06
No I am using 1 samsung TV. I have it connected via the DVI and the VGA cable now because the DVI output seemed to stop working after the Nvidia driver install, would only give me a picture through VGA.

The most important thing for me is using the TV via the DVI as I plan to use it to watch full 1080p movies.

I'll try out your new suggestion, but before I do I want to make sure that when I input these commands that I am telling Ubuntu I want to use the DVI output on the Nvidia card from now on (not the VGA output).

---

### Post by realzippy on 2010-09-06
[I]...telling Ubuntu I want to use the DVI output
[/I]
This is what Option "UseDisplayDevice" "DFP-0"  (hopefully)does.

---

### Post by YfoMp5QBh2 on 2010-09-07
Thanks RealZippy, & everyone else who posted! Everything is now the way I need to it be. I know I've asked lots of questions and been a pain, so thank you all for your patients! :D

---

### Post by realzippy on 2010-09-07
...fine.Can you set thread as solved? (Threadtools)


...just see it already is...thanks.

---

