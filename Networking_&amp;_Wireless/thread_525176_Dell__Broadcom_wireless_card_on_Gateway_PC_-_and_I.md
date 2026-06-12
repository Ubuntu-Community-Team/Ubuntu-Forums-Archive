---
title: "Dell / Broadcom wireless card on Gateway PC - and I'm TOTALLY lost!!!"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by bluepowder7 on 2007-08-14
hi guys.

i'm totally new to linux, and quite honestly i'm struggling with getting my wireless card set up.  iv've tried to follow two tutorials, to no avail (usually around mid-way, sending a command to the console gets me a message that i'm specifying an invalid file or something equally "nope, sorry, can't do that.").

the laptop is a Gateway MX8711.  the wireless chipset is a Broadcom / Dell 1390.  i've downloaded two files so far (that ndiswrapper-1.47 and the R151517.EXE from Dell).

so, um, being that i'm totally stupid when it comes to doing ANYTHING on linux at this point, can someone walk me through the steps to get the driver actually installed?  pretend for a moment that i haven't yet figured out how the directory structures work!

thank you!!!

---

### Post by kevdog on 2007-08-14
For the .exe file that you downloaded Im not sure what kind of format the file is in.  It could be truly a .exe file, or a self extracting zip archive (probably the later).  Suggestions on how to get the Winxp drivers with the .sys and .inf files out of the .exe file:

1. (Easiest method) - Put the .exe on windows machine, open up with winzip (if you can), and then simply extract the .sys. inf and possibly .bin files to a USB stick and transfer back to Ubuntu
2. If no windows machine is possible, you can try to open the exe (if it is a zip fle), with archive manager (at command line)
/usr/bin/file-roller <****.exe>

Or if it is in the rare circumstance a cab file.
cabextract <******.exe>

Once you get the drivers out of this archive, do the following to install ndiswrapper and the drivers:

Here are my "universal installation instructions" for ndiswrapper:

First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.

---

### Post by bluepowder7 on 2007-08-14
hmm, i got as far as moving the .inf and .sys drivers into that driver directory (the exe file was a self-extracting archive).

when i do the "sudo ndiswrapper -i bcmwl5.inf" command, the console replies with "driver bcmwl5 is already installed".  when i then do the "ndiswrapper -l" command to verify, i get a reply that says "bcmwl5: invalid driver!"

:(

and this is where i stop since it seems that something just isn't going right.  everything else up until that point seems to be going well and i'm getting the same type of responses from the console as you indicated.

how can i roll everything back to blow away or undo the stuff i've done so far, and start with a clean slate?  i got stuck at the same location the other two times before, and got the same type of "invalid driver" responses, so maybe my repeated efforts ended up screwing things up.

:confused:


i've got a WinXP box set up here as well, and a wired internet connection on this laptop, so resources are plentiful!  hmm, don't have a USB memory stick, though - gave the last one away since it was only a 256meg!  :P

---

### Post by kevdog on 2007-08-14
This message usually means that you have installed the driver two or more times.  (Cant install multiple copies -- hmmm the program should be modified to look if driver is installed and if not install it, if it is, do not install it).

Anyway do the following then install the driver again

sudo /etc/ndiswrapper -R *

Basically you want to make sure that the /etc/ndiswrapper directory is totally empty -- no files, no folders.

---

### Post by bmartin on 2007-08-14
Here, [this]("http://ubuntuforums.org/showthread.php?t=405990") is much simpler.

You simply download one file, extract it, then run a file. It's all graphical. You don't have to download anything else. It handles all of the ndiswrapper stuff for you.

One thing I do recommend is that you use the **wifi-radar** program to connect to your WAP. Enable the universe repository (you can do this from Synaptic or from the Administration menu)... then install the package from a terminal:
```
sudo apt-get install wifi-radar
```

---

### Post by bluepowder7 on 2007-08-15
update time:

kevdog - i followed your instructions (along with figuring out how to log in as root and blowing away that /etc/ndiswrapper/ directory) and got it to install and get all the right responses right to the end!

yay!

i'm going to turn off all the router encryption and see if i get basic wireless connectivity.  if that works, i recall some steps that i can take for running ubuntu with WPA (which is what the router is currently set up for).

hopefully, i learned something along the way!

thanks a lot for all your help!  woo-hoo!!!

---

### Post by bluepowder7 on 2007-08-15
update #2:

i cheated, and went right to wireless with WPA (since the pulldown menu already had it from my previous attempts)

AND IT WORKS!!!

yay!

thanks, guys!  the laptop is now FREE!!!  no more ethernet cable tying me down.

thanks again!


:guitar:

---

