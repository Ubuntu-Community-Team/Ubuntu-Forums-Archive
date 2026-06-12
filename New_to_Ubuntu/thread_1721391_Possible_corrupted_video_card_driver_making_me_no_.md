---
title: "Possible corrupted video card driver making me no longer able to load desktop."
date: 2011-04-04
forum: New to Ubuntu
---

### Post by TruePurple on 2011-04-04
How it all started:

I was looking to install a video card driver for ubuntu 10.10 64bit, radeon 6850. After some searching and a phone call to ATI I found their linux drivers which I download,  but I couldn't figure out to install it despite the website saying it was 'autoinstall' or something. I asked in chat for help, and was directed to  instructional page. I followed the instructions, system- admin- other drivers or something like that. I selected (can't recall exactly) thinking that it would install the driver I downloaded from ATI.

Instead it started "downloading and installing" something else. I immediately pressed cancel, I wanted to install the driver I got from ATI or at least inquire more into which I should use. But pressing cancel didn't do anything, pressing the top left X for the window box didn't do anything, pressing ctrl C didn't do anything. I tried to get help from chat, and help was slow coming. I noticed the 'download and install' bar had finished filling and it was starting to do something else, so in desperation I stopped it the only way I know how, I turned off the PC through the desktop command.

So now I don't get a desktop, I no longer auto-log in but have to log in with password, and now I get just a command prompt.

When I enter startx, it gives me alot of errors and messages, too long to see them all, or even write down all that I do see (though if specifically asked I could, though it would take quit some time, I can't copy paste it)

Alot of failure to load, can't find, this or that failed. 
Two errors of seeming interest are:
(EE) Screen(s) found, but none have a usable configuration.
&
Fatel server error:
No screens found.

---

### Post by TruePurple on 2011-04-04
Some advice given in chat that didn't work

[QUOTE=oldos2er]choose recovery mode from the grub menu. If you don't see a menu, hold down the left Shift key after POST[/QUOTE]

No grub menu that I can determine shows (not that I know what one looks like) And holding down left shift doesn't work.

sudo dpkg-reconfigure xserver-xorg 

Didn't seem to do anything, and didn't fix the problem

sudo dpkg-reconfigure -a

Brought up a stream of stuff asking about this and that, where I didn't understand most of what options were presented. So I got out of it by turning off the PC.(ctrl c just brought me to the next option)

---

### Post by rileyp on 2011-04-05
Apparently the drivers for the 6850 are still in development from what I just found.
[http://ubuntuforums.org/showthread.php?t=1709769](http://ubuntuforums.org/showthread.php?t=1709769)
I could be wrong though.  I didnt google for long.....
 *I have always used nvidia cards with great success with Ubuntu as it has vdpau support and can run 1080p video on a 1.6ghz ion nettop*.I moved to linux for mythtv 2 years ago and have never looked back.
If you cannot google and find a full blown guide on how to install the driver I would not attempt it else you'll be deleting /etc/X11/xorg.conf  again...  The capital in X11 is critical.
Welcome aboard!
Ps If you need help in future a good way to get info off your problem linux pc is to use ssh from another pc. Or you can use putty from windows....
All the logs are in /var/log So if you look at /var/log/xorg0.log it wil have all the info in there of what went wrong with x. You simply highlight and dump in [http://pastebin.com/](http://pastebin.com/) to get it on the net
The thing I like most about ubuntu is when you highlight something and then click the mouse wheel it pastes it! How cool it that!

cheers rileyp

---

