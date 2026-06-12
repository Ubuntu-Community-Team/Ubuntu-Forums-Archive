---
title: "Auto once boot Ubuntu and Windows"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Joneseh on 2011-07-08
Hiya,
How do you make a script file to set the Grub to boot an OS once only?

So I have been playin around with duel boot with GRUB (Ubuntu 10.04 and Windows 7) which is working fine and great. 
HOWEVER:
I have been searching the forum and google for the past two days before I gave up to ask.
In the Grub boot menu it says 1.98 BUT I look for the Grub 1.98 file (I think grug.cgf or something) But I find a Grub 2 file instead (menu.something). 
So I assume I have Grub 2 and open it up and all... I see all the normal stuff like the defualt line and all.... Cant edit it cos im not root (later fixed as i gave myself root access). 

I have found a few scripts to edit the file so it boots once but they dont work.... And each grub version needs a different auto grub command (or so they say) 

Can someone step by step for all noobs now and in the future put a detailed and working script to allow someone to click or run it in Ubuntu, reboot (restart computer) and boot up ONCE ONLY in chosen OS, and once I shutdown/restart that chosen OS Ubuntu loads up again forever after untill that script is run again?

---

### Post by grahammechanical on 2011-07-08
There are two things that you can do for yourself.

1) Study what is written in this link

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

2) Open the Ubuntu Software Centre and search for Grub Customizer and install it.

This utility will allow you to set the default entry as either predefined by position in the menu or as the previously booted entry. You can also set the position of each entry in the menu and use Grub Customizer to change the appearance of the menu by putting an image behind the menu and other stuff.

Be careful. Do not reduce the timeout to zero as that will remove the menu from the screen. Which will cause difficulties should you wish to boot into another OS.

Regards.

---

### Post by Joneseh on 2011-07-08
I GOT IT!! 

After typing out a reply saying I dont know what you mean, It hit me... in the face...
It took some time to figure out what it all meant thou :D 
But a better link would have been:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and scroll down to: Configuring GRUB 2


So to do a once OS boot it follows:
In order to use the command:
**grub-reboot "(insert number)"**

**GRUB_DEFAULT= **Had to be set as (using Grub Customizer>Preferences>Advanced):
**GRUB_DEFAULT=saved**

It took a while to see that connection...
HOWEVER!!
On restarting the computer after the reboot worked well, ubuntu was not the default OS... the reboot option was.... 
I have a feeling it is cos of the saved option.... I dont know. Ill play around some more now that I have gotten this far.

I have to final coding now:
1) Make sure GRUB_DEFAULT is ="saved". You can use Grub Customizer for that part.

2) Copy below code and save to a file like .bat:
[INDENT][FONT=Arial]**#!/bin/bash**[/FONT]
[FONT=Arial]** sudo grub-set-default "Ubuntu, with Linux 2.6.32-28-generic"**[/FONT]
[FONT=Arial]** sudo grub-reboot "Windows 7 (loader) (on /dev/sda1)"**[/FONT]
[FONT=Arial]** sudo update-grub**[/FONT]
[FONT=Arial]** sudo reboot**[/FONT]
[/INDENT] 
_**Note: Change to your needs. Ubuntu and windows 7 are my options. You can find out your OS names by Grub Customizer.**_

3) Make that file an excutable by right clicking file > Propertise > Permissions Tick "Allow excuting file as program"

You can now click it and run it.

My only problem now is to run the file Default as just "run" and not pop up that menu asking how to run the file. That is my next bit of research.

---

