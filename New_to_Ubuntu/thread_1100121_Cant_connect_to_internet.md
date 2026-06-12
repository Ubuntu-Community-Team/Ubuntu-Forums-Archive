---
title: "Cant connect to internet"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by PuddingKnife on 2009-03-18
So a friend liked the way my computer worked.  Long story short, he brings me his lap top today and I install 8.10 on it for him.

Installation went smoothly, then I tried to connect to the internet. It doesnt see my wireless network.  So I tried to connect directly by unplugging the cord from my router and into the lap top. It doesnt detect a wired connection either ..

The laptop in question is an HP Pavilion dv8000.

I did an hour long search and nothing looked helpful for this particular issue.  

As I am still a total newb, I have no idea how to handle this issue.  When I installed it on my laptop it just worked out of the box.  :(

---

### Post by RedSingularity on 2009-03-18
Just out of curiosity, who is your Internet provider??

---

### Post by lkraemer on 2009-03-18
Open a Terminal Window:

```

lshw -C network
ndiswrapper -l

```

post the output of each.

After we get the results there will be two ways to proceed.
Use the Windows Wifi Drivers with ndiswrapper or (use Broadcom firmware
or the madwifi software) depending on what hardware you have.

Wired LAN should have worked from the start.  8.04 LTS worked for me on
powerup and connecting.

lkraemer

---

### Post by mathgeek2008 on 2009-03-18
> **PuddingKnife said:**
> So a friend liked the way my computer worked.  ...  ***So I tried to connect directly by unplugging the cord from my router and into the lap top***. 

Hmm: Clarification -- What happens if you plug the PC into the LAN ports on the Router? -- Not the Port on the Cable or DSL modem. Do you get a DHCP address? -- Is there a speed issue, - not sure where it is in Linux but can you fix the Network Adapter speed to 10MBs or 100MBs , not auto?

---

### Post by PuddingKnife on 2009-03-19
> **lkraemer said:**
> Open a Terminal Window:

```

lshw -C network
ndiswrapper -l

```

post the output of each.

After we get the results there will be two ways to proceed.
Use the Windows Wifi Drivers with ndiswrapper or (use Broadcom firmware
or the madwifi software) depending on what hardware you have.

Wired LAN should have worked from the start.  8.04 LTS worked for me on
powerup and connecting.

lkraemer

Thanks for the reply!  

<lshw -C network>

> WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:3e:a6:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:c4:8b:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: ea:34:45:17:ca:30
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


<ndiswrapper -l>

> The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

---

### Post by lkraemer on 2009-03-19
OK, go here and download the b43-all-fw.tar.gz file:
[http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)

You are getting the Broadcom Firmware.

I assume you will be saving the file to your Desktop.
In your GUI copy the downloaded file to a folder under
/home/yourloginname/
Let's assume it's larry.

In a Terminal window do:
```

cd /
cd /home/loginname/larry
tar zxvf b43-all-fw.tar.gz

```

Copy the files to /lib/firmware
```

cd /b43
sudo cp *.fw /lib/firmware
cd /

```
This won't copy the Legacy folder, but you shouldn't need it.

You should be able to get your wireless functional.
```

iwconfig

```
This will tell you the Wifi's identification....wlan0, ath0, wifi0, etc.

Assume your ID is wlan0...so substitute wlan0 everywhere there is a
<interface> in the code below. Turn on your Wifi switch if there is one,
or use CNTL F2 or whatever keystrokes enable your Wifi. Insert your
essid (UPPERCASE or lowercase specific)
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>

```

You should be able to surf, even though your LED for Wifi isn't "ON".


ref URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

If you are using WEP or WPA or WPA2 see URL above.

another ref URL:
[http://ubuntuforums.org/showthread.php?t=607410](http://ubuntuforums.org/showthread.php?t=607410)

lkraemer

---

### Post by PuddingKnife on 2009-03-19
i seemed to be getting somewhere until i got here:

> cp *.fw /lib/firmware
cd /

then the output says:

cp: cannot stat '*.fw' : No such file or directory
cp: omitting directory '/lib/firmware'
cp: cannot stat `cd': No such fire or directory



this is such a pain in the *** .. if I didnt love Ubuntu,  lol.  thanks for your continuing help  :)

---

### Post by lkraemer on 2009-03-19
OK, open a terminal window and do:
```

cd /
cd /home/loginname/larry
ls -alt

```
Now this is assuming that you are using larry as the temporary
folder, and you extracted there.
 
Post the output of the last command. (ls -alt)
You should see all the files ending with .fw
If not then you need to find out where you actually extracted them.
Then they need to be copied to /lib/firmware

You can also type the following in a Terminal window:
```

history

```
Do it, then cut and paste the results here.
 
lkraemer

---

### Post by ugm6hr on 2009-03-19
This should sort out the wifi issue:
[http://ubuntuforums.org/showthread.php?p=6028741#post6028741](http://ubuntuforums.org/showthread.php?p=6028741#post6028741)

As for wired... I thought that Realtek card was supported?

Perhaps a previous Windows installation used the power-saving feature to turn off netowrk cards?  See the Wifi help? link for an explanation.

---

### Post by PuddingKnife on 2009-03-20
> **lkraemer said:**
> OK, open a terminal window and do:
```

cd /
cd /home/loginname/larry
ls -alt

```
Now this is assuming that you are using larry as the temporary
folder, and you extracted there.
 
Post the output of the last command. (ls -alt)
You should see all the files ending with .fw
If not then you need to find out where you actually extracted them.
Then they need to be copied to /lib/firmware

You can also type the following in a Terminal window:
```

history

```
Do it, then cut and paste the results here.
 
lkraemer


Ok, I feel like Im making some progress!  Thank you so much.  Not out of the woods yet, though.

When I do ```
ls -alt
``` in /home/adam/adam i get:

> total 16
drwxr-xr-x  4 adam adam 4096 (date+time)
drwxr-xr-x 26 adam adam ""     ""
drwxr-xr-x  2 adam adam ""     "" b43
drwxr-xr-x  2 adam adam ""     "" b43legacy

Should I put the contents of b43 into the adam temporary folder?

---

### Post by PuddingKnife on 2009-03-20
> **ugm6hr said:**
> This should sort out the wifi issue:
[http://ubuntuforums.org/showthread.php?p=6028741#post6028741](http://ubuntuforums.org/showthread.php?p=6028741#post6028741)

As for wired... I thought that Realtek card was supported?

Perhaps a previous Windows installation used the power-saving feature to turn off netowrk cards?  See the Wifi help? link for an explanation.


Ok, why not.  Im giving that a try as well, but when I get to the part where I have to copy the wl_apsta & broadcom-wl files to my home directory, it says Permission Denied.  

::confused::

---

### Post by Pro75357 on 2009-03-20
I thought the wireless firmware extraction and crap was done for you, in the "Hardware Drivers" thingy... 

Found under Menu>System>Administration>Hardware Drivers (or something like that)

Good luck

---

### Post by ugm6hr on 2009-03-20
> **PuddingKnife said:**
> Ok, why not.  Im giving that a try as well, but when I get to the part where I have to copy the wl_apsta & broadcom-wl files to my home directory, it says Permission Denied. 

Why don't you have permission to write to your own home directory?

---

### Post by lkraemer on 2009-03-20
OK, you have two directories:
b43
b43legacy
noted by the first d in the listing.

do this:
```

cd /b43
ls -alt

```
You should see the *.fw files.

if so, do the following:
```

cp *.fw /lib/firmware

```

This will copy the firmware to /lib/firmware, assuming that
/lib/firmware exists.......and it should.

At this point, I would reboot and try the following in a Terminal:
```

iwconfig

```

This should give you the name of the Wifi......wlan0, ath0, wifi0, etc....

Then follow the instructions on my post #6.  You should be online.
Just make sure your Wifi switch is "ON" or your Wifi is turned on
by certain keystrokes (like the CNTRL F2 on a Gateway).  Even if
your LED os "OFF" your Wifi should work.

lkraemer

---

### Post by PuddingKnife on 2009-03-21
> **ugm6hr said:**
> Why don't you have permission to write to your own home directory?

I have no idea.  So I gave up last night.  Tried it again first thing this morning, and I was able to for some reason.

So I continued following the directions on the link you provided, and I now have a working wireless connection!  

Ikraemer and ugm6hr thank you two SO much for helping out and sticking with me. I would be banging my head on the desk were it not for you guys.  You made my day! 

::dances a little jig::  

On top of it all, I became much more acquainted with the command line and feel like I can actually perform some important jobs with it now.  

:D

EDIT: How do I add the 'solved' tag to the first post?

---

### Post by RedSingularity on 2009-03-21
Cant anymore, the admins disabled that.

---

