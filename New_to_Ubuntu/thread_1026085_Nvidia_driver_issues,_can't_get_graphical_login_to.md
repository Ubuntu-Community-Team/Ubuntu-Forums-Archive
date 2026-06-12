---
title: "Nvidia driver issues, can't get graphical login to load"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by sprinj76 on 2008-12-30
Hi all,

I am brand new to Ubuntu. The only experience I have with linux was a week playing around on my bothers computer with fedora 4, many years ago (when fedora 4 was first released).

System specs:
Ubuntu 8.10 64 bit version
AMD AM2 5000 BE @ 3.2 Ghz (1.425V)
Cooler Master Hyper 212
Foxconn C51XEM2AA- 8EKRS2H 590 SLI mobo
4 x 1GB G.Skill DDR2-6400 @ 800 MHz (4-4-4-12)
2 x BFG 8800 GT OC2 SLI
CORSAIR CMPSU-750TX 750W PSU 
Seagate 500GB HDD 
RC-690-KKN1-GP Case
BenQ FP222WH 22" widescreen LCD
Logitech Z-2300 2.1 speakers

My issue, I just installed nvidia drivers V173 via the System -> Administration -> Hardware Drivers method. Everything downloaded and installed without issue. I restarted my computer and while booting the graphical loading screen appears but then after loading is complete it switches back to graphical mode. The only graphical screen I see is the loading bar, after that nothing.

Things I've done to attempt to fix:
1) Tried to hit crtl+alt+F7, goes to a black screen.

2) Tried:
sudo /etc/init.d/gdm start
Nothing happening after it said OK

3) I got the V177 drivers via:
sudo apt get- install nvidia-glx-177
Which installed the new drivers without issue. After restart I had the same issue.

I am very new to linux and know almost no commands in the terminal/non-graphical linux screens. I've tried to reinstall unbuntu fresh three times now with the same results. 

The only thing I can think that may be causing an issue is I am running SLI, could this be a possibility?

Thanks for any help.

---

### Post by sprinj76 on 2008-12-30
I also tried pully offin the SLI connector, which did not help.

---

### Post by tuxxy on 2008-12-30
ok it seems you would be best to reconfigure your xorg but as you cant seem to access the desktop and im guessing a terminal window either then you would be best to try and enter recovery mode and fix it form here.

To enter recovery mode reboot the system and as it boots at the GRUB prompt you need to hit ESC there will be a list appear and you select the one that says recovery mode next to it, once it loads select the xfix option and after its finished select continue with normal boot and should be done but be careful with installting them v173 drivers again hehe

---

### Post by sprinj76 on 2008-12-30
tuxxy thanks for the reply.

I tried what you suggested via recovery mode but had no luck. I still can't get gnome to load.

---

### Post by tuxxy on 2008-12-30
Once you get to the black screen which should be a login screen press CTRL + ALT + F2 and enter your username and password in the new window, now enter this

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then you need to reboot the machine

```
sudo shutdown -r now
```

---

### Post by cb34 on 2008-12-30
edit-> i would try the post above me first to reconfigure xorg before you do anything i suggest..LoL :p
-----

if i was stuck at the command prompt, im not so good, but my first thought is to also check the /etc/X11/xorg.conf file, and your vid driver install..

if i was stuck, i would purge all nvidia drivers, and and xorg, after backing up the xorg.conf just in case you need to look at it.. then make sure all nvidia files and drivers/modules are all gone completely and not loaded by searching for anything with nvidia or nv related files/links.. then reinstall drivers and xorg and see if something maybe was left over when you were trying before.. i had wierd problems like that too a while ago.. and removing or purging nvidia drivers was not enough when i was dealing with drivers, i had to hunt down and delete by hand some left over nvidia stuff before next driver install magically worked.
this may not be your solution, just MAYBE what might work.. i'm a semi-newbie keep in mind..LoL

good luck.

---

### Post by sprinj76 on 2008-12-30
I tired entering:
sudo nvidia-xconfig

This is what I got:
using x configuration file: "etc/X11/xorg.conf".

Validation error: data incomplete in file /etc/X11/xorg.conf. Device section "configured video device" must have a driver line.

Then it says something about saving the x.org.conf file, I have to write all this down and then load into vista to put on here.

I will try what you suggested tuxxy.

---

### Post by cb34 on 2008-12-30
from what you just said.. when it didn't let you continue.. maybe if there was no xorg.conf file in existence in the first place, when you ran nvidia-xconfig, it will just create a new working one.. you could try that fairly quickly by first backing up your xorg.conf file somewhere else, and then delete xorg.conf from /etc/X11 and try nvidia-xconfig again with no pre-existing xorg.conf there..

---

### Post by sprinj76 on 2008-12-30
> **cb34 said:**
> from what you just said.. when it didn't let you continue.. maybe if there was no xorg.conf file in existence in the first place, when you ran nvidia-xconfig, it will just create a new working one.. you could try that fairly quickly by first backing up your xorg.conf file somewhere else, and then delete xorg.conf from /etc/X11 and try nvidia-xconfig again with no pre-existing xorg.conf there..

Thanks for the suggestion cb34. I don't know how to do this via command lines. The only way I know what to type is via suggestions and I'm reading as many threads on nvidia drivers issues as I can. Any way you could walk me through how to do this? 

tuxxy I tried what you suggested but it did not change anything for me, after the graphical bar goes all the way it goes to a screen where it stops on checking battery status or something like that . . . I have to hit crlt+alt+F1 or crlt+alt+F2 to be able to type any commands. Thanks again for your help and any other ideas you might have would be awesome!

---

### Post by cb34 on 2008-12-30
hmm.. it stops when it checks the battery.. i have no clue what im sayin here..LoL.. but could this be somethin i read about when loading the kernel to pass an argument acpi=off to the kernel, please dont write that command or try to copy it or use it somewhere before you understand what it does, i dont.. just remember hearing about it and it came to mind, but a quick search and you'll find info on that.. MAYBE it has something to do with it.

---

### Post by sprinj76 on 2008-12-30
I tired another fresh install this time installing the 180.06 drivers manually which seemed to go really well, but I had the same results.

I think I'm going to download the 32 bit version of ubuntu and see if I have the same issues.

This really sucks, anyone know how to get me back to square one and remove all nvidia drivers and restore and files?

Thanks

---

### Post by cb34 on 2008-12-30
it depends if you installed the nvidia driver from a .tar.gz from their site, or using jockey/synaptic/apt-get?

to purge everything.. i dont like to use synaptic for anything more than looking at the info and names, then i just go to the terminal to do the work.. so i would go into synaptic.. not using the quick search , but using the real search button, and serach for everything nvidia, all those modules, and kernel this and that, every nvidia package in synaptic i removed in the terminal using apt-get purge package1 package2 package3 etc. so it does a full purge of these things.. be careful!!!!!!!!!!! then in terminal i did:
sudo updatedb && locate nvidia
you dont have to remove every single nvidia file like man pages you may find or similar documents, but everything else nvidia.. carefully not to screw up.. just what locate finds, copy'n'paste the whole line of the file you wanna delete and put "sudo rm" before it.. hope you know what i mean.

if you installed from the script that comes in the tar.gz from nvidia's site, you have to go to the directory where you installed script in the first place, and type instead of ./nvidia-installer(or whatever it was called) to run the script and install the drivers you do the same but add a --uninstall to the end of the command when running that script.
./nvidia-installer --uninstall

thats the other way to do it, if you installed it that way.. i prefer it this way using drivers straight from nvidia site.

i think you can just move or delete xorg.conf and no need to remove all of xorg program.. but you could if you want by doing: sudo apt-get purge xorg
"sudo apt-get install xorg" to install
but try that later on maybe if all of this doesn't work, cuz i really think its unnecessary but who knows your problem right, so try that later maybe.
or you could try to purge all nvidia, and purge xorg, then reboot, then start fresh by installing xorg, then the nvidia driver again and have it configure xorg for you.
---

i would download the driver from nvidia, unzip it to a dir you will keep in case you want to --uninstall the driver. then just run the script included in the tar file, it will install the driver easily, follow the instructions and build a kernel module when it says to. and if im not mistaken i think it will configure you xorg for you.. so allow it to.

i kind of wrote this all confusing but just ask if anything... im not so pro at the tech support stylez.. :p

edit-> oops, just realized you cant look in synaptic..haha.. sorry... to purge all nvidia package.. all. type:
sudo apt-get purge nvidia*
and just for you to know.. by using the -s flag in apt-get like this
sudo apt-get -s purge nvidia*
the -s mean to simulate what would have happened, so u can run apt-get and see before you really run it what it'll do.. simulation mode ;)

---

### Post by sprinj76 on 2008-12-30
Thanks for the info cb34, but I can't get gnome to load at all. I am using text commands only. 

I installed 180.06 drivers via downloading the drivers from nvidia. Saved them to my desktop. The file was NVIDIA-Linux-x86_64-180.06-pkg2.run. I then ctrl+alt+F2, logged in. Then typed
```
sudo /etc/init.d/gdm stop
```

Changed directories to my desktop, and typed this to install:
```
sudo sh NVIDIA-Linux-x86_64-180.06-pkg2.run
```

I answered the questions the nvidia software asked and attempted to restart graphical typing:
```
sudo /etc/init.d/gdm start
```

It then said something about rebuilding deamon . . . . and nothing happened. I tried to restart and I'm right back to where I started and can't get gnome to load.

Extremely frustrated with this, spend about 2 days straight just trying to get this to work . . . not sure why I'm having so many problems.

---

### Post by cb34 on 2008-12-30
ok.. where you ran the nvidia script to install it.. go back there and run the same command but with --uninstall at the end of it.

sudo sh NVIDIA-Linux-x86_64-180.06-pkg2.run --uninstall

run it twice even.. it should say the drivers have been uninstalled ok.

then also using apt-get purge all nvidia packages

sudo apt-get purge nvidia*

then look for any remaining nvidia crap

sudo updatedb && locate nvidia
look through this carefully and anything that looks meaningful to do with running nvidia stuff, delete it with rm command.

then purge xorg off the system (backup your /etc/X11/xorg.conf file if you want/need to)

sudo apt-get purge xorg

then reboot

then install xorg again when you login

sudo apt-get install xorg

reboot again (i dont know why, just throwin this in here for good measure - what i would do)

next install the nvidia script you want again the way you did it, and it should want to modify xorg.conf, allow it to not merge or anything like that, but allow it to replace the xorg with its own nvidia version.. it will back it up.

this should work or be very close to a working system with maybe some tweaking needed..

then you got
startx
gnome-session
/etc/init.d/gdm start
to try out and see if something helps. or reboot again then try so the modules are loaded properly if they arent already.

at this point theres dealing with the xorg.conf file if it doesn't work, then, im lost, cuz it should work.. but im only going through what i went through a bunch of times already and when building a new arch linux system, same process.. there may be more to it than this, this is all i know im basically tryin to say.. hehe.. really hope you get it working man.

---

### Post by cb34 on 2008-12-30
if all else fails, dont give up, maybe move onto a different driver instead of 180.06, maybe it's the 180.06 x64 driver that is not workin out for you. ?? just a thought..

edit-> another quick thought.. i think to get everything back to normal and not use nvidia drover, you can modify the xorg.conf original file that you should have backed up, and change where it says "nvidia" to "vesa" save and reboot, and i think you'll get somewhere.
and maybe you'll have to start X manually after you login.. probably.

---

### Post by tuxxy on 2008-12-30
Did you select to use the v177 drivers though as it might still be stuck on the v173 if you activated them first.

---

### Post by sprinj76 on 2008-12-30
Thanks for the write up cb34. I will have to try it out tomorrow.

I can't believe this is so difficult. I haven't read anyone else having problems even close to mine, and I can't figure out why.

I might give up linux till they get some of these major issues worked out, I can't believe how much still relies on non-gui based commands. I'm a bit let down by linux.

---

### Post by sprinj76 on 2008-12-31
I pulled my second vid card and it's working now. Drivers installed well and I am playing left 4 dead. 

Now I need to figure out how to get both cards installed and SLI working.

Thanks to tuxxy and cb34 for all their time and help!

---

### Post by cb34 on 2008-12-31
im happy you got things going man! :D:D:D

---

### Post by tuxxy on 2008-12-31
Now you have it running try loading nvidia-settings to setup the SLI, however it isnt popular so I would not bank on it automatically configuring dual cards.  Check the readme on the Nvidia site, it should help you set up your xorg

---

