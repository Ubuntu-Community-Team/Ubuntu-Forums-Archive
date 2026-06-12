---
title: "TV Tuner Problem: MSI Vox ii USB"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by adventure man on 2009-06-05
Hi guys I have the "vox ii MSI usb TV Tuner".  I plugged it in, connected the cable line and tried various programs that show television on the pc (mythtv, tvtime and kaffiene).  Unfortunately none of these programs can find my tv tuner.  I recieve the same error that I do not in fact have a tv tuner connected to a usb slot.  I had a few headaches connecting this tv tuner to a windows xp machine, but I managed to get it to work with MSI's tv software suite.  Is there any way to make a hardware check to see why the tuner is not registering with these programs?  Anything I have done wrong?

Thanks!:D

---

### Post by wwazman on 2009-06-05
newbie here.. I ran mythdora a couple months ago and ran into similar problems. One version saw the tuner and then dropped it on the next reboot. :( So I finally gave up.. however, perhaps the (may have the wrong name here).. ndiwswan..ndiswrapper? Perhaps one of those will let it use Windows drivers and work better? I know it worked for a pci wifi card in Ubuntu 9.04 for me. 

Course I'm sure there's others here that have lots better info! Good luck!

---

### Post by adventure man on 2009-06-05
> **wwazman said:**
> newbie here.. I ran mythdora a couple months ago and ran into similar problems. One version saw the tuner and then dropped it on the next reboot. :( So I finally gave up.. however, perhaps the (may have the wrong name here).. ndiwswan..ndiswrapper? Perhaps one of those will let it use Windows drivers and work better? I know it worked for a pci wifi card in Ubuntu 9.04 for me. 

Course I'm sure there's others here that have lots better info! Good luck!


mythdora just seems a bit much as I don't watch too much tv, maybe twice a week.  ndiswrapper seems interesting, I'll give it a try.  Thanks for the help.

---

### Post by LowSky on 2009-06-05
ndiswrapper yeah that wont work... sorry just letting you know


I assume this is the tuner
[http://www.msi.com/index.php?func=proddesc&maincat_no=132&prod_no=1081](http://www.msi.com/index.php?func=proddesc&maincat_no=132&prod_no=1081)


can you do me a favor with the tuner card pluged in, can you open a terminal and post the results of this command

```
lsusb
```

it might give the chipset and help us get it running

---

### Post by adventure man on 2009-06-05
> **LowSky said:**
> ndiswrapper yeah that wont work... sorry just letting you know


I assume this is the tuner
[http://www.msi.com/index.php?func=proddesc&maincat_no=132&prod_no=1081](http://www.msi.com/index.php?func=proddesc&maincat_no=132&prod_no=1081)


can you do me a favor with the tuner card pluged in, can you open a terminal and post the results of this command

```
lsusb
```it might give the chipset and help us get it running


This is the tv tuner:

[http://www.msi.com/index.php?func=proddesc&maincat_no=132&prod_no=1043](http://www.msi.com/index.php?func=proddesc&maincat_no=132&prod_no=1043)

I'll go ahead and do that and post up results thanks :D

---

### Post by adventure man on 2009-06-05
ok here are the results from Terminal:

Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 6000:0001  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1241:1203 Belkin 
Bus 001 Device 001: ID 0000:0000  

I have 3 USB devices connected.  My mouse, keyboard and the tv tuner.  Hope this helps. :D

---

### Post by LowSky on 2009-06-06
Bus 003 Device 004: ID 6000:0001 
that has to be the tuner, and unfortunate that it doesn't reconize it by name or chipset.
I have scoured the web and found little if anything that may be usefull..
[http://www.mail-archive.com/linux-dvb@linuxtv.org/msg22855.html](http://www.mail-archive.com/linux-dvb@linuxtv.org/msg22855.html)

Also, on June 12 it will not be recieving any NTSC signals in the US, because of the digital switch over. as of right now some stations have gone completely digital already and you wont get any signal  on the device.

---

### Post by xeticus on 2009-06-06
Try this link here. i followed the instructions and I was able to get my tv tuner to work easily with kaffeine. [http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

---

### Post by adventure man on 2009-06-08
> **xeticus said:**
> Try this link here. i followed the instructions and I was able to get my tv tuner to work easily with kaffeine. [http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)


Thanks xeticus, I'm having problems with this section though:

**"IMPORTANT:** Download the file into /lib/firmware, then extract them with sudo tar zxvf filename.tar.gz
  	**Getting and installing the driver**
Create a folder somewhere convenient.
mkdir driver Now, go into that directory and type
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel) Which will download a copy of the driver sources to your directory.
  	Compiling: 
  	cd v4l-dvb-kernel make sudo make install"


I download firmware ver. 2 but Ubuntu 8.04 won't allow me to write into that directory that he says to (lib/firmware).  Any idea how to allow this?

---

### Post by LowSky on 2009-06-08
download the file to the desktop then open nautilus as root using terminal
```
gksu nautilus
```
now moved the files to /lib/firmware and extract the file like it is said above, easist way is to right click and and choose to extract. to the same folder

---

### Post by adventure man on 2009-06-08
thanks lowsky, managed to do that.  Now I'm having trouble with this section:

"Create a folder somewhere convenient.
mkdir driver Now, go into that directory and type
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel) Which will download a copy of the driver sources to your directory.  	Compiling: 
  	cd v4l-dvb-kernel make sudo make install"


it says to go to that directory? and then type that command.  But after creating that folder, say in "Documents" folder named "Tvdriver", how do I go in that directory and type that command?

---

### Post by adventure man on 2009-06-10
I've scoured the web still don't get how to create this folder and then type that command in it's directory :(

---

### Post by LowSky on 2009-06-10
very easy

```
cd /home/*your user name*/documents/Tvdriver
```

remember to use the correct letters, capital letter can be another directory if you know what I mean
example
/Home
/home
are two different folders in Linux, so know the name correctly

---

### Post by adventure man on 2009-06-10
Now, go into that directory and type
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel) Which will download a copy of the driver sources to your directory.


^^^how do i go about doing that?  I just went in documents and created "Tvdriver" folder manually, that command kept giving me an error. lol

thanks :D

---

### Post by LowSky on 2009-06-10
ok Im going to rewrite the directions by hand to help you

make sure to install the packages you need to install, everything required should already be installed as per a normal ubuntu installation , here is how in terminal

```
sudo apt-get install mercurial build-essential
```
press y for yes when it asks you to install


next step
download this file
[http://konstantin.filtschew.de/v4l-firmware/firmware_v2.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v2.tgz)
save it where ever
now this is important, close out all nautilus (file managers) and open terminal and type ```
gksu nautilus
```
find the folder ```
/lib/firmware
```
copy the file you downloaded to there, then close nautilus 

in terminal type

```
sudo tar zxvf /lib/firmware/filename_v2.tgz
```

now run
```
hg clone http://mcentral.de/hg/~mrec/v4l-dvb-kernel
```

now change to the directory
```
cd v4l-dvb-kernel
```

then run make
```
make
```

that will take some time, go grab a drink and wait it out, when it completes run this command
```
sudo make install
```

wait for that to complete and reboot
from the command line
```
sudo reboot
```

that should do it, assuming the firmware is correct

---

### Post by mrbiggbrain on 2009-06-10
```
sudo reboot **now**
```

---

### Post by adventure man on 2009-06-10
well I followed that to the T Lowsky.  Made the install, rebooted, still same issue...it doesn't see my video device as installed.  Any other suggestions guys?:popcorn:

---

### Post by adventure man on 2009-06-11
A better question would be, is there any way to check if I did this whole procedure correctly?  Everything seems to have gone as written, but still ubuntu does not register my tv tuner as connected into a usb slot on my pc.  Also the Kaffeine program offers no DVB area in the player.  When I check the tv tuner with vlc media player/tv time/myth tv they simply say** "no video source" and "no signal"**.     I tested the tv tuner on a windows xp machine and it shows up in the control panels hardware section.  :(

---

### Post by LowSky on 2009-06-11
ok I did some sleuthing around... I think your MSI Vox II tuner card is based on this chipset called the Em28xx (the xx being which model number), which I have no idea, because no one has info on this tuner's chipset

[http://www.linuxtv.org/wiki/index.php/Em28xx_devices](http://www.linuxtv.org/wiki/index.php/Em28xx_devices)

unfortunately Your device doesn't show up on that list, so I dont know if it will work at all.

I'm sorry but not all hardware will work, and with the US going all digital on June 12, I dont even know how many channels you will even be able to watch after tomorrow.

I know you want this thing to work, but it doesn't seem like a popular tv tuner card, and without popularity no one has written anything about it

It seems like windows might be your only option, otherwise check the web for as much info as you can, maybe there is something I missed.


Just to let you know not having supported hardware is really a bummer, and I know your pain,
[this is my tv tuner card]("http://www.mythtv.org/wiki/Hauppauge_HVR-2250"), which until about a month ago didn't work in Linux

---

### Post by adventure man on 2009-06-11
Alright, what can ya do, at least my webcam works ;)

I appreciate all your help with this lowsky :D Thank you!

---

