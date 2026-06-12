---
title: "ATI Radeon 7500 gfx video disaster"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by unkelmarkmark on 2010-02-04
I didn't know KUBUNTU can't handle this video adapter.
 
If anyone has a fix out there,  please post.
 
I can get to terminal,  but cannot see most other tools that i select.
 
 
thanks
 
Mark

---

### Post by Ji Ruo on 2010-02-04
Could you expand a little on what you are getting. Is it just the command line, or are you getting a proper desktop (ie with windows) but the resolution is too low (can't see all of the desktop).

Also, was it like this when you first started up Kubuntu or did it happen after you installed the driver from ATi?

---

### Post by unkelmarkmark on 2010-02-04
It is loading the desktop, and loading the background but when you start using the mouse, often times, on  all programs selected,  it blanks out the display so you cannot see anything.
During installation i didn't explicitly load the ATI drivers myself, its my understanding they were detected and downloaded automatically.  
Problem has been there since the installation was finished.
 
 
Mark

---

### Post by almufadado on 2010-02-04
You must install the ATI driver yourself.

Go to -> System -> Administration -> Hardware controller (jokey-kde).

Install one of the available drivers. 

Restart session (logout-> login).

Open the ATI display manager. (May need to edit the laucher to add "gksu" before the command to get root rights)

---

### Post by unkelmarkmark on 2010-02-04
My options are     system,  administration,  hardware drivers (not hardware controller)

and apparently its already been done (by the installer whom was not myself)  as the only thing in the list is a broadcomm network controller)

but then it gets confusing,  as the    "ATI display manager" that you mention is nowhere to be found.

if the ATI drivers have been installed ,  where should i be seeing the "ATI display manager" ?

---

### Post by Ji Ruo on 2010-02-04
I suspected that the proprietary driver was already installed. There are 2 different drivers for ATi cards in Linux, the other one is the open driver (being developed by the community) and this one has less problems. It should load automatically when the proprietary driver is uninstalled and the computer rebooted.

The information on the open ATi driver is here - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

You should need to just type in the code for removing the proprietary driver in the terminal:```
sudo apt-get remove --purge xorg-driver-fglrx
```then reboot your computer (if you get dropped to a console, I think you just enter 'restart' or 'reboot' to get the computer to restart).

That's all you should need to do. When Kubuntu reloads, the kernel will use its own ATi driver, and hopefully your display will work properly.

I should note also that you shouldn't need to do any configuration etc like the link says. That will all happen automatically.

---

### Post by unkelmarkmark on 2010-02-05
message: package xorg-driver-fglrx is not installed, so not removed,

the following packages were automatically installed and are no longer required:
linux-headers-2.6.31-17 linux-headers-2.6.31-17-generic  

Use 'apt-get autoremove' to remove them




           I tried removing what they recommend above and that makes no difference in the video

---

### Post by unkelmarkmark on 2010-02-05
I also tried the following to check my graphic card and chipset

 lspci -nn | grep VGA
  

ATI Technologies Inc Radeon Mobility M7 LW [radeon mobility 7500] [1002:4c57]


and when i look in "hardware drivers"  no proprietary drivers are installed

---

### Post by Mark Phelps on 2010-02-05
There are no ATI drivers that will work with your card and Ubuntu 9.10, so ignore any advice about trying to install them -- you'll only make the situation worse in the process.

Go to the link that Ji Ruo gave you for the open source driver and read ALL the instructions about removing/installing drivers.

You should end up with a working open source driver -- and that's all that is available for your card.

---

### Post by unkelmarkmark on 2010-02-05
All of this has come to a halt because the install doesn't have an xorg.conf file.

I used "locate" and was logged in as root, and don't find any xorg.conf file

I am using Ubuntu 9.10 released in October 2009.

in the x11 directory i have a file called: default-display-manager
and in this file there is simply the following:
/usr/bin/kdm


am i on the right track here? do i need to create a display file from scratch?

---

### Post by Ji Ruo on 2010-02-07
Sorry for not getting back to you sooner.

Looks like I was wrong with the proprietary driver being the problem. It's probably not showing up as available under 'hardware drivers' because it doesn't work anyway for your card.

To double-check you can enter```
fglrxinfo
``` into the terminal.

kdm I believe is the login manager, where you type in your password, so it's not going to help. The reason you are not finding an xorg.conf file is that it's not usually created unless it's needed in Karmic apparently.

I found a blog entry from someone trying the beta version of Kubuntu Karmic who got your card to work - [http://www.pythian.com/news/4404/first-look-at-kubuntu-9-10-karmic-koala/](http://www.pythian.com/news/4404/first-look-at-kubuntu-9-10-karmic-koala/) They use vi to create a new xorg.conf file, but you may find using the gui editor kate a bit easier. Here are the amended instructions -

Press <Alt>+<F2> and enter```
kdesudo kate /etc//X11/xorg.conf
```which will create the new blank xorg.conf file in the kate text editor. Then copy and paste the contents```
Section "Device"
        Identifier      "vga"
        Driver          "ati"
        Option          "AccelMethod"   "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device          "vga"
        Monitor         "Configured Monitor"
EndSection
```save, exit kate and then reboot. HTH

---

### Post by unkelmarkmark on 2010-02-07
Ok got that all setup.

Now at startup i get the following:

Ubuntu is running in low-graphics mode
The following error was encountered. You may need
to update your configuration to solve this.

(EE) Problem parsing the config file
(EE) Error parsing the config file

         

next screen:
"what would you like to do?"
run ubuntu in low-graphics mode for just one session
reconfigure graphics
troubleshoot the error
exit to console login




(note: reconfigure graphics selection doesn't work)

---

### Post by Ji Ruo on 2010-02-07
I was really hoping that would work... you could try pasting the xorg.conf directly from the link and see if that fixes the error (maybe I made a mistake in copying). And I would also try 'troubleshoot the error'. I will keep searching for a fix when I have some time, unless someone with a better idea of what's going on gets to it first.

---

### Post by Ji Ruo on 2010-02-08
Can you attach or post here the xorg log file - /var/log/Xorg.0.log

It may have more information on what's not being accepted. (Run Ubuntu in low graphics mode).

---

### Post by DenysT on 2010-02-09
> **Ji Ruo said:**
> I was really hoping that would work... you could try pasting the xorg.conf directly from the link and see if that fixes the error (maybe I made a mistake in copying). And I would also try 'troubleshoot the error'. I will keep searching for a fix when I have some time, unless someone with a better idea of what's going on gets to it first.


I used this fix on Ubuntu 9.10 but ran into the same problem. Looking at the log file it said the Identifier was not a valid keyword for the Screen section (but Xorg documentation says it is mandatory). Anyway I just took out Identifier and it worked like a charm. Beats me, I'm just happy I finally got my laptop graphics to work correctly.

---

