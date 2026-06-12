---
title: "Howto: setup Zydas (zd1201) based adapters"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by rum_n_coke on 2005-07-14
[SIZE="5"]Setting up a wireless adapter with a Zydas (zd1201) chipset on Linux[/SIZE]

*last updated:July 30, 2005*

This tutorial was made to help make your Zydas (zd1201) wireless adapter work under Linux (tested with Ubuntu/Debian).  
I decided to write this after reading so many forums and mailing lists with people absolutely clueless on how to make their 
zd1201 based adapters work under Linux.  [Google]("http://www.google.com/") your adapter if you're not sure what 
chip it contains.  Note that it also make take some work that isn't written here to get this to work, because as you may know by now, Linux is like wrestling a 500 pound gorilla at times.

[B][U]*note-I take ABSOLUTELY no responsibility if you 
crash your system without backing-up, poison your kernel or otherwise "majorly **** up".  USE AT YOUR OWN RISK.[/U][/B]
--------------------
**Step 1: Recompile to 2.6.12 or higher**
OK, not to be mean, but you're gonna to need to recompile the kernel :) .  It's not that hard if you don't know how, 
just google on how to do it.  Just make sure that the zd1201 module is selected in USB network devices.

--------------------------------
**Step 2: after re-compilation, reboot and edit */etc/network/interfaces* as a superuser**
Be sure to backup as *interfaces.old* or something, and add the follow to the bottom of *interfaces*...

```
map wlan0
auto wlan0
iface wlan0 inet dhcp
wireless mode Managed
wireless-essid *_name of wireless point_*
```

when you've written this, save changes and exit your text editor.

-----------------------

**Step 3: Install the firmware**
Download the latest firmware at [http://linux-lc100020.sourceforge.net]("http://linux-lc100020.sourceforge.net")
Move the newly downloaded file to the desktop, and then open a terminal...
```

**nate@zephyr:~/Desktop$** tar -xvzf zd1201-0.14-fw.tar.gz

**nate@zephyr:~/Desktop$** cd zd1201-0.14-fw

**nate@zephyr:~/Desktop/zd1201/zd1201-0.14-fw$**make
INSTALL zd1201.fw zd1201-ap.fw => /usr/lib/hotplug/firmware/

**nate@zephyr:~/Desktop/zd1201/zd1201-0.14-fw$**cd .. && rm -rf zd1201-0.14-fw

**nate@zephyr:~/Desktop$**rm -rf zd1201-0.14-fw.tar.gz
```

if it didn't return any errors, then it_should_have been successful, and you can delete the folder and tarball.
-------------
**Step 4: initializing the stick**
With your terminal window...
```

**nate@zephyr:~/Desktop$** sudo rmmod zd1201
**nate@zephyr:~/Desktop$** sudo modprobe zd1201
**nate@zephyr:~/Desktop$** sudo rmmod zd1201
**nate@zephyr:~/Desktop$** sudo modprobe zd1201
```

Now, you may wonder why you have to reload this module twice.  Just a issue with the driver and hardware getting along or something.  
The above commands *must* be done after every boot (if the stick is attached) or when reinserting the adapter to have the adapter to work.

---

### Post by Futures on 2005-10-05
Hello,

im new in this forum and i wanna say hello to everyone :)

my english is pretty bad so if you dont understand something just tell me and i'll try to describe it.
Another thing is, that im not that experienced in linux =)

so my problem is, that i have a notebook with ubuntu hoary installed on it and ive got this Zyxel Zyair B-120 wireless card with the zydas 1201 chipset on it.
But somehow these two things do not match very well :)

so i need youre guide but its temporary offline..

could anybody give me some help ? 


thanks, cya

---

### Post by rum_n_coke on 2005-10-05
Sorry about that dude, fixed now.  Cheers!

---

### Post by vega113 on 2005-11-29
my zd1201 usb card would not automatically reconnect after loss of connection to router. i reconnect manually by deactivating it with networking, and activating again. how this could be solved?

---

### Post by rum_n_coke on 2005-12-03
To be honest I have this same problem too though I am sure a cron job or a small shell script could fix this with a little imagination. #-o

---

### Post by nikro on 2006-05-31
Hi i'm using the Zyxel Zyair B-120 and Dapper Drake.

My Problem is, that my Card uses the same Chip but its a PCMCIA and no  USB device.. is there any solution or workaround?


greetings sven

---

### Post by yossman on 2006-07-16
i've just successfully enabled the GigaFast USB wireless adapter under Ubuntu 6.06, after a few hours of screwing around.  this thread was one of the best we found to help, but, the missing piece of information for us was WHERE to copy the .fw files (firmware) that we got from [http://linux-lc100020.sourceforge.net/](http://linux-lc100020.sourceforge.net/).

copying all the .fw firmware files to /lib/firmware/2.6.15-23-386/ was what really fixed it -- after unplugging the USB wifi adapter and re-plugging it back in again, the rest of the instructions about modifying /etc/network/interfaces worked exactly right.  thanks to this guy for the information re: firmware:  [http://oase.uci.ru.nl/~bradaa/nerdnotes.org/index.php ](http://oase.uci.ru.nl/~bradaa/nerdnotes.org/index.php ).

you can also use 'wireless-key xxxxxxxxxx' in /etc/network/interfaces under 'wlan0' in case you are running WEP; replace 'xxxxxxxxxx' with your 10 digit hex key for simple WEP 64.

thanks for the assist guys, ttys. ;-)

yossman

---

### Post by BooVeMan on 2006-11-23
Geeeee!!! Thanks a million yossman!!!! Was about to dump that old stick...

---

### Post by sputnik2012 on 2007-01-18
I've got it working fine for WEP encrypted connections.  No idea how to get it working with wpa_supplicant, any ideas?

Thanks,
  Rob.

---

### Post by DarkN00b on 2007-01-18
Wow. That's a lot of trouble. I just install the .deb I found of the firmware drivers, plug in my adapter, configure my connection and I'm connected. That's all you *ever* have to do.

I'll even attach the firmware for you.

.deb attached.

---

### Post by nilsw on 2007-01-19
I have tried to make a Zyair B-120 PCMCIA card work on Ubunto 6.10 with ndiswrapper using the driver for XP (and 2K) downloaded from Zyxel but I get the following result:

~$ sudo ndiswrapper -i ZD1201COBM.inf
Installing zd1201cobm
~$ ndiswrapper -l
Installed drivers:
zd1201cobm       invalid driver!
~$

Is there anything more to do, or shall I shop  for a more up to date WLAN device? 

(I downloaded Unbunto 2 days ago on an old laptop that only has the mentioned connection to the outside, it installed very smothly. The .deb file provided by DarkN00b installed itself to my great surprise but did not help much so far.)

---

### Post by biodiesel-bri on 2007-02-23
Thanks Darkn00b, that quest is at an end!

---

### Post by DarkN00b on 2007-02-24
> **nilsw said:**
> I have tried to make a Zyair B-120 PCMCIA card work on Ubunto 6.10 with ndiswrapper using the driver for XP (and 2K) downloaded from Zyxel but I get the following result:

~$ sudo ndiswrapper -i ZD1201COBM.inf
Installing zd1201cobm
~$ ndiswrapper -l
Installed drivers:
zd1201cobm       invalid driver!
~$

Is there anything more to do, or shall I shop  for a more up to date WLAN device? 

(I downloaded Unbunto 2 days ago on an old laptop that only has the mentioned connection to the outside, it installed very smothly. The .deb file provided by DarkN00b installed itself to my great surprise but did not help much so far.)

I think the ZyDas 1201 drivers are in the Edgy repos now. The driver I provided is for the Prism2 chipset in the ZyXel B-220 USB adapter and may not work with your PCMCIA card.

---

### Post by infinito on 2007-02-28
I'm trying to get this _damn_ usb dongle on egdy server (2.6.17-11-server), but it's impossible to connect to any AP. The firmware seems to load ok, but the dongle can connect to any ap, event if it sees them with iwlist scan... Any idea? Has anyone get this working?

---

### Post by infinito on 2007-02-28
I'm having this on syslog:
Feb 28 22:02:52 kernel: [42949563.590000] usb 1-1: zd1201 firmware upload failed: -110
Feb 28 22:02:52 kernel: [42949563.590000] zd1201: probe of 1-1:1.0 failed with error -110
Feb 28 22:02:52 kernel: [42949563.590000] usbcore: registered new driver zd1201

---

### Post by maarten80 on 2007-06-16
thanks for the .deb!

works perfectly for my old topcom skyracer wireless usb stick 11b V2 that I had lying around

I can now see all networks around, but am unable to connect... which seems to be a more common problem. Hope this is fixed soon!
[see this thread]("http://ubuntuforums.org/showthread.php?t=414793&highlight=unable+to+connect+to+wifi+network")

---

### Post by maarten80 on 2007-06-28
update: I got it to work perfectly! (Xubuntu 7.04)

The deb of DarkN00b worked perfectly. After that it was a matter of configuring /etc/network/interfaces, using the correct pass-key ](*,) :-\" (yeah I know), and playing with the sudo ifup and ifdown commands.

Mind that I'm using WEP for the moment (university dorm). I will have to take a look at WPA though as that's what we're using at home.

As a workaround for using my laptop on different known places I configured /etc/network/interfaces manually for a location, brought up the connection (ifup) and checked that the internet was working. Then I opened the network manager (sudo network-admin) and saved the present configuration as a location. Did the same thing for my other locations. So next time it's a matter of opening the network manager and changing locations (I hope I don't need the ifup anymore then). Still need to test this, although switching locations did alter the /etc/network/interfaces to the one I configured for the particular location. So I guess it should be allright.

(I also tried wifi-radar but that did not work)

Remaining problem: how to see/find out how strong the connections are?

---

### Post by maltman on 2007-08-23
> **DarkN00b said:**
> Wow. That's a lot of trouble. I just install the .deb I found of the firmware drivers, plug in my adapter, configure my connection and I'm connected. That's all you *ever* have to do.

I'll even attach the firmware for you.

.deb attached.

Thanks DarkN00b! That was simple and worked perfectly.
I've been trying everything else I've been reading on the forums, but ndiswrapper didn't work at all.
The deb you provided did the trick instantly.

---

### Post by Linuxgenius on 2007-12-24
im having the same problem and im a new user to ubunutu can u help me configure my wireless network i dont know where to start

---

