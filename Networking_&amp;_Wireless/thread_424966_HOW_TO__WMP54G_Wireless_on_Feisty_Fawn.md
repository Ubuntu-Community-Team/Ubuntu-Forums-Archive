---
title: "HOW TO:  WMP54G Wireless on Feisty Fawn"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by Jorsher on 2007-04-27
I tried to compile ndiswrapper again, and to my surprise it worked.  YES!  I downloaded the latest drivers for my network adapter for linux, and after a few tries I got it installed with ndiswrapper.  On a sidenote, why does Linksys, who's routers use a form of linux, not have linux drivers?  I guess because it's a broadcom chip, but anywho.  The installed driver STILL did not work.

I later installed the GUI for ndiswrapper, and that showed that the driver was installed, but said hardware wasn't present.  What??  I went to the device manager, found the network adapter, and saw that it was still using the bcm43xx driver.  It's supposed to use bcmwl5 :(  Unfortunately, it wouldn't use the bcmwl5 driver without some work.

I banged my head on the wall a few more times.  Realized there was no chance of sleep before work today, and continued my search.  I came across a link that showed how to install the adapter on a different version of Ubuntu.  Would it help?  Couldn't hurt!  So, onto the good stuff!  I'm going to list step by step instructions, and hopefully help the (many) people I saw having problems with this adapter.  I hope it helps people get some sleep instead of staying up all night like some, and hope it will prevent people from straying from linux like I almost did!

1.  Download [ndiswrapper]("http://ndiswrapper.sourceforge.net/") and save on the harddrive.  I always save to the desktop to make it easy to find.
2.  Download [build-essential]("http://packages.debian.org/unstable/devel/build-essential") to the harddrive.  Go to the link, and choose your architecture.  In most cases, i386.
3.  Download the drivers for the networking card from [Linksys]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843981&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4398140888B07&displaypage=download").
3.  If you open build-essential, it'll install for you without much trouble!
4.  Now compile ndiswrapper by typing the following code in terminal, if you don't have it on your desktop you'll have to change the directory on the first line:

```

cd ~/Desktop/ndiswrapper-1.42
sudo make uninstall
sudo make
sudo make install

```

5.  You should see a lot of things scroll, but shouldn't get errors or warnings.  Great!  The following code will start out with getting rid of the crappy non-working driver.

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
```

6.  Goodbye crappy driver!  OK, let's install ndiswrapper and make a good driver!

```
sudo apt-get install ndiswrapper-common
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
sudo modprobe ndiswrapper
```

7.  I wish I could find the link to where I got it, I would give them a hug!  I had to change some things, they were using an older version of Ubuntu, and the ndiswrapper is now ndiswrapper-common instead of ndiswrapper-utils.

8.  This is where it gets weird!  Click the network icon near the time, or go to System > Administration > Network.  Remove the check from wired connection, it will say "changing interface configuration," or it may not.

9.  Make sure that wireless is checkmarked, and go to it's properties.  Remove the checkmark from "enable roaming."  For some reason, I could not get this to work!  Put in your settings manually.  In my case, "dd-wrt" for the ssid, no encryption (that's next!), and DHCP.

10.  Ctrl + Alt + Backspace to log out, and log back in.  ONCE I got it to show the signal strength, but every other time it will just show the two computers like if it were an ethernet connection.  It checkmarked wired connection again, but I don't have a wire ran to the computer, and internet is working great ;)  If you are OCD like me, you can remove the checkmark and log out/in.

If anyone can figure out how to make the signal strength stay there, please let me know so I can update this!  Thanks to the person who's code I got ideas from to get this going!  If anyone has ideas to clean the code up, or improve this "trick," just let me know and I'll update.

Hope this helped some people out!

NOTE: I just saw the sticky for the other linksys adapter on Dapper Drake.  Not sure if that method will work here, but if it does, disregard all this :P

---

### Post by Niila on 2007-04-27
Hi! RT61 is supported in feisty as default.. no need for ndiswrapper..at least in my case. You can get the driver from ralinks website easily.

Heres my problem: [http://ubuntuforums.org/showthread.php?t=422632]("http://ubuntuforums.org/showthread.php?t=422632")

I downloaded wicd wlan tool and got the link up with the router. but i still cant use internet..something is wrong.

---

### Post by Jorsher on 2007-04-27
> **Niila said:**
> Hi! RT61 is supported in feisty as default.. no need for ndiswrapper..at least in my case. You can get the driver from ralinks website easily.

Ah, well I'm pretty sure the WMP54G uses a broadcom chip, soooo this is still necessary....right?

I could not, for the life of me, get it to work.

---

### Post by Jorsher on 2007-04-27
So is there an easier way?  This is the only way I could get it to work for me with the WMP54G VER 1.0 adapter.

Would be nice if there was a simpler way...

---

### Post by marksman7328 on 2007-04-29
Thank you for the nice walkthrough finally!

I am a Ubuntu/Linux nub. I started with Edgy, but quit because my wireless card (WMP54G v4.1) would not work. Thanks to your nice walkthrough I am able to get my card to detect and connect to my router, however I still have no internet. Is there anything more I need to do besides what is in this walkthrough?

Notes:

The only problem I had with the code was when I reached the spot that says:

```
sudo rmmod bcm43xx
```

Here the terminal said something like "Error no such module" (idk if that is exact because I am typing this in Windows)

Another question I have is what are the Linksys drivers for? Nowhere in this tutorial does it say what to do with them other than download them.

---

### Post by Jorsher on 2007-04-29
> **marksman7328 said:**
> Thank you for the nice walkthrough finally!

I am a Ubuntu/Linux nub. I started with Edgy, but quit because my wireless card (WMP54G v4.1) would not work. Thanks to your nice walkthrough I am able to get my card to detect and connect to my router, however I still have no internet. Is there anything more I need to do besides what is in this walkthrough?

Notes:

The only problem I had with the code was when I reached the spot that says:

```
sudo rmmod bcm43xx
```

Here the terminal said something like "Error no such module" (idk if that is exact because I am typing this in Windows)

Another question I have is what are the Linksys drivers for? Nowhere in this tutorial does it say what to do with them other than download them.


I'm not sure why you still wouldn't be able to connect to the internet.

I haven't tried this on the v4.1 adapter, only on the v1.0.  Step 6 tells what the linux drivers are for.  "bcmwl5" is the new driver that you need to use with ndiswrapper to get the adapter working.  The driver for version 4.1 might be named different, and I'm not sure if it'll work with these instructions.

For the code "sudo rmmod bcm43xx" your driver might be something else.  You will have to find out what driver is being used and remove it to replace with the ndiswrapper'ed linksys driver.

---

### Post by marksman7328 on 2007-04-29
how would I find out what driver is being used?

---

### Post by sclement on 2007-04-30
After several days of fiddling, I then followed these instructions to the letter, and I got connected onto my wireless network with WEP enabled - GREAT !

Unfortunately I then shut the system down and re-booted a few hours later, and I no longer have connectivity.  Also the wireless connection has dishappeared from the network manager.

I am running the 64 bit version of feisty,  I wonder if it is something to do with that ?

---

### Post by sclement on 2007-05-01
I found I had to include the step

sudo gedit /etc/modules
Add the word ndiswrapper. Then save and exit file.

After the "sudo ndiswrapper -m" step to get ndiswrapper to start on boot-up

---

### Post by SamsLembas on 2007-05-05
I get the following error when attempting to install build-essential:

Error: Dependency is not satisfiable: libc-6|libc-dev


Anyone know a way to fix this? I have no way of accessing the internet dirrectly on this computer, but I can tranfer files to it.

---

### Post by vir3nt on 2007-05-10
Solution for WMP54G v4.1 with Feisty Fawn:

The rt2500 driver in Feisty works fine with the v4.1 version of the card (only version i have to test).
The problem is with the Network-Manager not being able to work well with the Ralink driver. You must connect manually. :) 

The following will connect you to the network:

```
sudo ifconfig ra0 down

sudo iwconfig ra0 essid "XXXXXXX" key XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX

sudo ifconfig ra0 up

sudo dhclient ra0 
```


Add this to /etc/network/interfaces to get it to automatically connect on login:
Leave out any pre-ups that you don't need (encryption/passphrase etc).

```

[...]
iface ra0 inet dhcp
pre-up iwpriv ra0 set NetworkType=Infra
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid Networkname
pre-up iwpriv ra0 set WPAPSK="passphrase"
auto ra0
```

If this works with other versions of the card, please let the people know!
Hopefully the gnome network-manager will get this bug fixed soon!

Good luck!

---

### Post by dragonlor20 on 2007-05-14
I also have the v4.1 and on a fresh install of Feisty, the roaming mode was doing some very odd things. It would show the networks that *should* be shown, but the strength bars were empty. Stranger was that the one network I normally use actually DID have a working strength bar, but the card would not connect under the roaming mode.

Uncheck the roaming mode and input your info manually under System>Administration>Networking>Wireless and it should connect you pretty much right away. Be sure to pay attention to whether you use the ASCII or the HEX system and adjust that appropriately. (If you aren't sure then it isn't going to hurt you to try both) If that doesn't work, make sure to go ahead and reboot after you change the network settings.

While this is an annoying work-around, it isn't all THAT annoying. The v4.1 LinkSys card is not made for notebook computers, so you are most likely connecting with a desktop computer... hence, you aren't going to be doing a lot of jumping around on different networks, and when you do move your huge desktop around, you can simply change the manual settings.

This fix should work, and you shouldn't have to use the command line to do it. Make sure you have a fresh install (I am running an upgraded version of Feisty from Edgy and a fresh install of Feisty (the desktop over here) and I can tell you that there are some odd differences between the two installs.

The new linux kernel is supposed to include some fairly significant wireless changes if the RCs are any indicator, so we can always continue to hope that the broadcom chips are going to eventually get the attention they deserve. Wireless issues should be moving up to the top of the priority list sometime soon.

---

