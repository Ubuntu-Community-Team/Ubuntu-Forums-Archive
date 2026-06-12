---
title: "Slow boot with wireless card"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by dbeckler on 2006-09-07
So I have had problem with the system pausing on **Configuring networks** since I have installed my wireless card.  The card is using ndiswrapper for driver support and the card runs fine 99% of the time.  

After booting and getting through the **Configuring networks** part, which I usually ctrl+c out of, the network is unresponsive.  So I go to System--> Administration--> Networking. I go into the wireless connection properties, which is still set up perfectly.  Next I select the network name drop down and change it from my connection to another one in the area, and with out hitting ok I change it back to my network, click ok, then ok again and everything is working.

Now during that whole process I didn't change any of my network settings as they were correct on startup.  Its just that the essid name is not connect even under **iwconfig**.  If anyone has any clue as to what the problem is help would be appreciated.  I have looked at other guides on here, installed a bunch of wireless network utilities, none of which helped.

---

### Post by neocookie on 2006-09-24
I've got exactly the same problem during boot, however, if I turn on my wireless card as soon as that entry comes up my system only hangs for about a minute. If I fail to do this, it doesn't boot.

I've found this really strange, as I have just re-installed Dapper (after another problem which caused hard-locks), before the re-install it would boot fine (and actually faster than XP! < 30 seconds).

Any ideas how I can resolve this?

---

### Post by neocookie on 2006-09-26
Nobody able to help with this one?

---

### Post by neocookie on 2006-10-25
Update: I uninstalled the drivers completely, uninstalled ndiswrapper completely, and also the linux headers for my kernel, threw in a network cable, and re-installed everything from scratch using synaptic (rather than downloads from wiki). Worked a treat. Boot-time back to around 30 seconds.

---

### Post by matt_risi on 2007-01-25
I'm finding this only happens to me when I ave my computer in a new network environment and I boot it up, for example at school. Boot up time is well over a minute, it's very much a nuisance. I'm sure it has to do with ndiswrapper trying to connect the card to a wireless network that doesn't exist at the time.

---

### Post by AlienPlanet on 2007-07-25
I used to have the same problem until a few mintues ago. I think the problem may have been the alias wlan0 ndiswrapper entry in the ndiswrapper file under /etc/modprobe.d/. dmesg showed a wait of more than 1.5 minute just after ndiswrapper wrote some error entries. After the changes that I made below, the total boot time is around 34 seconds instead of the 150 seconds I had before.

I uninstalled ndiswrapper and installed the latest version (followed the steps here: [COLOR="Blue"]https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty[/COLOR]) except for the part where it says to run **ndiswrapper-m** and I got the 1.47 version from ndiswrapper.sourceforge.net instead of 143 mentioned in the guide above). I then deleted the ndiswrapper file from /etc/modprobe.d/ directory. After this, I edited the /etc/modules file and added the word ndiswrapper at the end of it.

I think what was going on was when wlan0 was initialized before I made the changes, it used to load ndiswrapper automatically (because of "alias wlan0 ndiswrapper" under modprobe.d) and tried to find a network. Now, it just loads the ndiswrapper module, and does not bother to look for a network when it tries to bring up wlan0 interface. I'm not exactly sure that this is what is going on, but in any case it solved my long boot time and I'm happy.

---

### Post by slack42 on 2007-07-26
I am having the same problem. I have a system76 laptop that I updated to fiesty and even with the drivers that system76 provides I still get the slow boot time because of the restricted wireless driver. I've been looking around the forums to try and find a solution when I came across your post. I also found this bug report [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112931](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112931). In it he said that moving the initscript right before gdm starts worked for him. But how do you move the initscript to before gdm boots? And I thought that ubuntu doesn't have a init script anymore.

---

### Post by slack42 on 2007-07-26
After some more searching I found a solution....for me at least. I found this over on the system76 forums where someone was asking about a unrelated wireless problem. And he was told to go to /etc/network and in the file interfaces comment out everything except:

auto lo
iface lo inet loopback

I did this and rebooted and my boot time was about 30 seconds. I don't know if this will work for you but it worked great for me. Hope this helps.

---

