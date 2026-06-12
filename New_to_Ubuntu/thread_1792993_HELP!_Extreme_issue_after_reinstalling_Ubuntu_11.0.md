---
title: "HELP! Extreme issue after reinstalling Ubuntu 11.04!"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by courage1919 on 2011-06-28
Okay! So I reinstalled my Ubuntu 11.04 this morning with a Live CD and after it was finished, y'know, remove the installation disc from the tray, then pressing enter for the computer to restart, well, it booted up Ubuntu as how a normal computer would, then the startup came up and it was just BLANK! Like, the mouse, it's fine and everything, I can move it accross the monitor and stuff, but its like the navigation bar isn't there, nothing is there, just plain BLANK of the wallpaper and the mouse! This is really irritating me and I hope you understand what's up!:(

---

### Post by dFlyer on 2011-06-28
Can you open a terminal with ctl-alt t and paste the following command into it and post back:

/usr/lib/nux/unity_support_test -p

---

### Post by courage1919 on 2011-06-28
> **dFlyer said:**
> Can you open a terminal with ctl-alt t and paste the following command into it and post back:
 
/usr/lib/nux/unity_support_test -p
 The keyboard doesn't work at the startup! I can't access the terminal because the whole thing is just blank of the wallpaper with nothing on it!:confused:
 
 
P.S. If your wondering how I'm on here right now, I'm using my laptop to communicate here.

---

### Post by slooksterpsv on 2011-06-28
Try this:

CTRL+ALT+F1

Type in your username (it was lowercase you set it up during installation), press Enter, then type in  your password (NOTE: password won't show anything as you type it), press Enter when you've typed it in.

Now type in /usr/lib/nux/unity_support_test -p

Also you could try restarting gdm via:

sudo killall gdm-binary
sudo gdm &

And seeing if the login screen comes up, if it did before, try changing (at the bottom after you click on your user) from Unity to Classic.

---

### Post by dFlyer on 2011-06-28
Can you get to the login screen. Click on your name and select ubuntu classic on the bottom panel bar to see if you can at least use gnome?

---

### Post by courage1919 on 2011-06-28
> **slooksterpsv said:**
> Try this:
 
CTRL+ALT+F1
 
Type in your username (it was lowercase you set it up during installation), press Enter, then type in your password (NOTE: password won't show anything as you type it), press Enter when you've typed it in.
 
Now type in /usr/lib/nux/unity_support_test -p
 
Also you could try restarting gdm via:
 
sudo killall gdm-binary
sudo gdm &
 
And seeing if the login screen comes up, if it did before, try changing (at the bottom after you click on your user) from Unity to Classic.
Waitt wuuuuut?!?! How do I do that?

---

### Post by courage1919 on 2011-06-28
> **dFlyer said:**
> Can you get to the login screen. Click on your name and select ubuntu classic on the bottom panel bar to see if you can at least use gnome?
 I could access the login screen, yes. No, I have not tried that yet, though. Should I?

---

### Post by dFlyer on 2011-06-28
Go ahead and try gnome classic and enter the above command. You just need to copy and paste it in a terminal and press enter.

---

### Post by courage1919 on 2011-06-28
The one that slooksterpsv said? Okay! I did it and it's just stuck on a black screen with words saying:
```

* Starting CUPS printing spooler/server                     [ OK ]
                                                                                        * Checking battery state...              [ OK ]
 
Stopping System V runlevel compatibility                   [ OK ]
```
 
What now? It's been staying here for quite a while now...

---

### Post by courage1919 on 2011-06-28
Bump!

---

### Post by dFlyer on 2011-06-28
Can you do a ctl-alt f2 and enter the following command at a terminal:

/usr/lib/nux/unity_support_test -p

Also when you burned your iso did you check the md5sum to make sure it matched the checksum md5sum on the web page you download the file from.

---

### Post by courage1919 on 2011-06-28
> **dFlyer said:**
> Can you do a ctl-alt f2 and enter the following command at a terminal:
 
/usr/lib/nux/unity_support_test -p
 
Also when you burned your iso did you check the md5sum to make sure it matched the checksum md5sum on the web page you download the file from.
 When I type it and press enter, an error shows up saying "unable to open display"
And no, I did not check the md5sum or whatever. Please guys, I need you guys to be more specific with this because I'm just a newbie to this Ubuntu stuff but I am on the right track because I'm trying to bear with ya.

---

### Post by dFlyer on 2011-06-28
I'm going to assume you downloaded the Ubuntu Live CD using windows. Do you still have a copy of the iso, if so you will need to do a google search for md5sum.exe and download that file to the same directory you downloaded the ubuntu iso. From there you will have to open a windows terminal cd to the directory where the md5sum.exe and iso are and enter the following command at the command line.

md5sum.exe "EnterTheNameOfTheUbuntuFile.iso" without the quotes and press enter.

after a few seconds it will list an alpha/numeral checksum. This checksum needs to match the MD5SUM file from the web page you downloaded. If this does than there is a good chance your download was good, if it doesn't you will have to redownload the file and burn a new cd.

Any information you can provide about your computers hardware will also help, including other OS's, Video Card, Network Cards, Hard drive size just about anything you can think of will help.

One last thing, before you installed your system did you test drive the ubuntu live desktop to make sure all you hardware worked. If not you may want to do so after making sure the md5sum was good for the iso.

---

### Post by courage1919 on 2011-06-28
> **dFlyer said:**
> I'm going to assume you downloaded the Ubuntu Live CD using windows. Do you still have a copy of the iso, if so you will need to do a google search for md5sum.exe and download that file to the same directory you downloaded the ubuntu iso. From there you will have to open a windows terminal cd to the directory where the md5sum.exe and iso are and enter the following command at the command line.
 
md5sum.exe "EnterTheNameOfTheUbuntuFile.iso" without the quotes and press enter.
 
after a few seconds it will list an alpha/numeral checksum. This checksum needs to match the MD5SUM file from the web page you downloaded. If this does than there is a good chance your download was good, if it doesn't you will have to redownload the file and burn a new cd.
 
Any information you can provide about your computers hardware will also help, including other OS's, Video Card, Network Cards, Hard drive size just about anything you can think of will help.
 
One last thing, before you installed your system did you test drive the ubuntu live desktop to make sure all you hardware worked. If not you may want to do so after making sure the md5sum was good for the iso.
 Oh, okay. Yes, I still do have the .iso file that I downloaded from the website that's in my other desktop computer that is Windows 7 Professional. I was surfing through YouTube and a couple other sites while I was downloading the .iso file. So, you mean, I'm going to have to burn the .iso again on another blank CD just this once with it being checked with md5sum? And when will I know when it's ready to be burnt?

---

### Post by dFlyer on 2011-06-28
No you don't need to download another iso or burn another cd yet. A google search for md5sum.exe will lead you to a download of the md5sum.exe file. You will need to download md5sum.exe file to the same directory you saved your ubuntu iso to. Once you have the md5sum.exe you will need to run the below command from the directory that contains both the md5sum.exe and ubuntu iso. After a few minutes depending how fast your computer is it will produce an alph/numeral checksum. This checksum needs to match the checksum for your download. Below is a list of all the checksums for ubuntu cd's. Make sure the checksum matches the one you downloaded.

8468300a61ea1e3b7607f46f7643b57a *ubuntu-11.04-alternate-amd64.iso
e6a29ce3dccb0ab12332036dcff7d9e4 *ubuntu-11.04-alternate-i386.iso
7de611b50c283c1755b4007a4feb0379 *ubuntu-11.04-desktop-amd64.iso
8b1085bed498b82ef1485ef19074c281 *ubuntu-11.04-desktop-i386.iso
355ca2417522cb4a77e0295bf45c5cd5 *ubuntu-11.04-server-amd64.iso
b1a479c6593a90029414d201cb83a9cc *ubuntu-11.04-server-i386.iso

if you downloaded the i386 file you would enter:

md5sum.exe ubuntu-11.04-desktop-i386.iso and press enter. 

If you downloaded a different version you would enter that ubuntu version and find the above checksum and make sure they match.

---

### Post by courage1919 on 2011-06-28
> **dFlyer said:**
> No you don't need to download another iso or burn another cd yet. A google search for md5sum.exe will lead you to a download of the md5sum.exe file. You will need to download md5sum.exe file to the same directory you saved your ubuntu iso to. Once you have the md5sum.exe you will need to run the below command from the directory that contains both the md5sum.exe and ubuntu iso. After a few minutes depending how fast your computer is it will produce an alph/numeral checksum. This checksum needs to match the checksum for your download. Below is a list of all the checksums for ubuntu cd's. Make sure the checksum matches the one you downloaded.
 
8468300a61ea1e3b7607f46f7643b57a *ubuntu-11.04-alternate-amd64.iso
e6a29ce3dccb0ab12332036dcff7d9e4 *ubuntu-11.04-alternate-i386.iso
7de611b50c283c1755b4007a4feb0379 *ubuntu-11.04-desktop-amd64.iso
8b1085bed498b82ef1485ef19074c281 *ubuntu-11.04-desktop-i386.iso
355ca2417522cb4a77e0295bf45c5cd5 *ubuntu-11.04-server-amd64.iso
b1a479c6593a90029414d201cb83a9cc *ubuntu-11.04-server-i386.iso
 
if you downloaded the i386 file you would enter:
 
md5sum.exe ubuntu-11.04-desktop-i386.iso and press enter. 
 
If you downloaded a different version you would enter that ubuntu version and find the above checksum and make sure they match.
 Is it compatible with Windows 7?

---

### Post by dFlyer on 2011-06-28
yes, md5sum.exe is a windows based command line program.

---

### Post by courage1919 on 2011-06-28
Oookay. But a quick question: How do I get out of the Ctrl+Alt+F1 terminal?

---

### Post by dFlyer on 2011-06-28
You can try ctl c to cancel any running program. If that works just type:

sudo halt

enter your password and that will shut your computer down. If control c doesn't work, you can try ctl-alt f2, login with your name and enter name and password and then the above command.

if this doesn't work try pressing alt-sysreg (print screen) reisub keys on the keyboard, which will reboot the computer.

If this doesn't work you can just turn off the computer if everything is frozen, but do this only as a last result.

---

### Post by courage1919 on 2011-06-28
What do I do once the checkup with the MD5SUM.exe is complete?

---

### Post by dFlyer on 2011-06-28
If the checksums match the numbers I posted above good. You will not have to download again. If they don't match you will have to download another iso file again. If they match move the the next step.

The next step will be to boot off the cd you burned and when you see a little man figure at the bottom of the screen press the spacebar which will bring up a grub menu. From there you should be able to select check cd or something like that. Select that and let it check your burn. It will take a while to check the disk, hopefully it checks okay. If it doesn't you will have to reburn the cd.

---

### Post by courage1919 on 2011-06-29
> **dFlyer said:**
> If the checksums match the numbers I posted above good. You will not have to download again. If they don't match you will have to download another iso file again. If they match move the the next step.
 
The next step will be to boot off the cd you burned and when you see a little man figure at the bottom of the screen press the spacebar which will bring up a grub menu. From there you should be able to select check cd or something like that. Select that and let it check your burn. It will take a while to check the disk, hopefully it checks okay. If it doesn't you will have to reburn the cd.
 Everything's good. I did what you told me to do and it said check has found no errors on disc or something like that. Now what?

---

### Post by dFlyer on 2011-06-29
Now boot off the live desktop cd and test it on your system to be sure all your hardware works. To do this place cd in the drive and boot off the cd drive. When the screen says Try or Install select Try to make sure all your hardware works, including network, wifi if you it and video.

---

