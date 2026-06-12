---
title: "can't get ndiswrapper to work with D-Link DWL-G122"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by ncumming on 2007-06-30
I'm trying to get my desktop running with feisty, and i can't get my wireless adapter working.  It is a D-Link DWL-G122 rev B1 USB adapter.  I've read the how-to's on installing ndiswrapper, and after searching and searching the only drivers i could find to install were the latest windows xp drivers.  I tried installing these via the instructions in the how-to's, but when i code

ndiswrapper-l 

in the terminal i get:

netrtusb : invalid driver! 
netrusb : invalid driver!

Can anyone help me figure out what is going on here?  My linux experience is pretty limited, so it is definitely possible i screwed something up...

thanks

---

### Post by kevdog on 2007-07-01
Lets check a few things before jumping right in:

1. Ndiswrapper installation --
At command line type and post for me:
ndiswrapper -v

How did you attempt to install ndiswrapper?/

2. Lets find out more about your USB device:
Post the output of:
lsusb

3. Keep the drivers handy, we will need them.  Cross your fingers and hope they will work!

---

### Post by ncumming on 2007-07-01
ndiswrapper -v

utils Error: no version specified!
driver version:     1.38
vermagic:    2.6.20-15-generic SMP mod_unload 586

lsusb

Bus 005 Device 004:  ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ra link]
 *(other usb devices omitted to save myself typing....)*  

I should probably note that I'm typing this output in, not cutting and pasting, so the syntax might not be 100% correct but i think i got it right.  

another potentially useful detail is that when i boot the machine up to XP (seperate hard drive), the wireless device works fine, so it isn't a hardware failure. 

As far as how I installed ndiswrapper, i followed the instructions in this how to:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Since i didn't have intenet access on that computer, i followed the instructions in 2.3 "without internet access" and installed ndis through the synaptic package manager off of the 7.04 alternate install cd.  I later downloaded the ndisgtk package through windows and installed that from the command line per the instructions in 2.2.  

Thanks so much for you help, I truly appreciate it.  Some day i hope to understand this stuff well enough to make good on the debts I'm racking up on the forums!  :wink:

I

---

### Post by kevdog on 2007-07-01
Onto ndiswrapper
Your version has an error and is not installed properly:

> 
utils Error: no version specified!

So first uninstall ndiswrapper. You probably used Synaptic, so use Synaptic to uninstall ndiswrapper

Next we are going to reinstall ndiswrapper -- but from source

Lets do some setup work first - If you have a wired ethernet connection that you can download files, skip to step #4
1. Stick ubuntu cd-rom into driver and wait to become ready
2. At command line type: sudo apt-cdrom add
3. Then: sudo aptitude update
4. Then: sudo aptitude install build-essential

At command line, do the following:
cd ~
mkdir ndiswrapper

Download the ndiswrapper source files and place in the ~/ndiswrapper directory:
[http://sourceforge.net/project/showf...group_id=93482](http://sourceforge.net/project/showf...group_id=93482)

cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install

Ok great, now lets check ndiswrapper installation to see if it correct:
ndiswrapper -v

You should see no errors!
Something like this
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586


```

---

### Post by ncumming on 2007-07-01
I got a 404 error from the link for the source files, so i downloaded them from here:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
I assume that was right...  ndiswrapper -v gives me the exact output you had specified.  I'm guessing my next step is to try to reinstall the windows drivers, now that ndiswrapper is installed correctly...

---

### Post by kevdog on 2007-07-01
Yes you are correct.

Make sure before installing you completely delete any old installations with the command
sudo rm -R /etc/ndiswrapper *

Then install windows drivers
sudo ndiswrapper -i ****.inf  <--- Make sure .inf and .sys files are in the same working directory

Verify installation with
ndiswrapper -l

Then insert ndiswrapper module into kernel
sudo depmod -a
sudo modprobe -i ndiswrapper

Verify successful insertion with
dmesg | more
Look for ndiswrapper and make sure there are no errors

Make ndiswrapper module load at boot
sudo ndiswrapper -m

Reboot
Everything might work at this point, however in many cases there are just a couple more tweaks.  If yours works -- Congratulations

---

### Post by ncumming on 2007-07-01
ok i've really done it now ](*,)

i tried installing the drivers i previously downloaded, and it said the driver was already installed.  I did ndiswrapper-l, and it listed two invalid drivers.  So i did ndiswrapper-v again, and now it seems to be all messed up again.  Here is everything from the terminal from the time i checked to make sure ndiswrapper was installed correctly the first time to where I am now.  I hope i haven't screwed this up even worse!

nick@officemachine:~/ndiswrapper/ndiswrapper-1.47$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 
nick@officemachine:~/ndiswrapper/ndiswrapper-1.47$ cd ~
nick@officemachine:~$ sudo ndiswrapper -i /~drivers/NetRTUSB.inf
driver netrtusb is already installed
nick@officemachine:~$ ndiswrapper -l
netrtusb : invalid driver!
netrusb : invalid driver!
nick@officemachine:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
nick@officemachine:~$

---

### Post by ncumming on 2007-07-01
unfortunately i did all this before i read your previous post which said to make sure everything from the old installation was cleared out.  Can i do that now and then reinstall the drivers, or do i need to remove ndiswrapper and start over again?  If so, how do i remove ndiswrapper since i installed from source instead of through the package manager?

---

### Post by kevdog on 2007-07-01
Make sure before installing you completely delete any old installations with the command
sudo rm -R /etc/ndiswrapper/*

This should remove all the old drivers
You can check with ndiswrapper -l
Nothing should be listed

Then try installing driver again.
Then list output of 
ndiswrapper -l

---

### Post by ncumming on 2007-07-01
ok i think we're closing in on it:

ndiswrapper -l
netrtusb : driver installed
        device (2001:3C00) present (alternate driver:  rt2570)

proceeding with the rest of your instructions...

---

### Post by ncumming on 2007-07-01
only strange thing was this:

sudo ndiswrapper - m
module configuration already contains alias directive

I'm going to reboot and see what happens...

---

### Post by ncumming on 2007-07-01
....still doesn't seem to work.  We seem to have gotten somewhere because when i opened up the network manager, the lights on my adapter flashed a few times, but then went back out.  

When I open the network manager, it lists the ESSIDs of the 3 networks in my area (mine and my neighbor's, but lists 0% by each one for signal.

when i do ndiswrapper -v at the terminal, i get:

nick@officemachine:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

---

### Post by ncumming on 2007-07-01
at this point i'd assume i need to start over again.  How do i remove NDIS wrapper, given that i installed it via the terminal using the source files?  I tried add/remove programs and syanptic and neither show ndiswrapper as being installed.

Or am i not as screwed up as i thought?

---

### Post by kevdog on 2007-07-01
Im not sure what you did

Uninstall from source is easy

Change into the directory where the source files are located, possibly like this:
cd ~/ndiswrapper/ndiswrapper-1.47

then just type
sudo rm -R /etc/ndiswrapper/*
sudo make uninstall

Thats it.
Check ndiswrapper -v
Nothing should show up.

---

### Post by kevdog on 2007-07-01
After uninstalling I would do the following

sudo make distclean
sudo make
sudo make install

That will install it again if you want

---

### Post by Beaucephus on 2007-07-02
If it helps to know that this is possible, I had a DWL-G122 working through ndiswrapper before.  

Some general advice.  
Wireless devices frequently change chipsets.  Check your version for driver compatability. 
Make sure you are trying to use the right driver when compiling.
Document the steps you take because when it does work, you want to be able to repeat it.

---

### Post by ncumming on 2007-07-02
SUCCESS!!!

Sort of.  I got the adapter working now, just uninstalling and re-installing.  But it seems to drop in and out.  Sometimes I'll log in and it works great, other times it won't work at all, others it will stop working and I'll have to reboot to get it working again.

I guess the saga continues...

---

### Post by kevdog on 2007-07-02
Just things to try:

1. Disable IPV6 - 
gsku gedit /etc/modprobe.d/blacklist
blacklist ipv6  <<---This line may already be there, if not add it!

2. Try another driver with ndiswrapper (if you can find one, in some cases you can not!).

---

### Post by ncumming on 2007-07-02
ok i added it to the blacklist.  no problems so far... the connection has been working for about an hour now.

keeping my fingers crossed -

thanks so much for all of your help!  Its great to finally get this up and running!

---

### Post by kevdog on 2007-07-02
Maybe you should change the title of the thread to "CAN get ndiswrapper to work with ....."

---

