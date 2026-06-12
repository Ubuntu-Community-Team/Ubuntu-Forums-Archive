---
title: "Zydas ZD1211 - Anybody got it working?"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Yoeri on 2007-04-25
Same problem as a few other Feisty-users ... hardware is supported, network manager shows wireless networks but I cannot connect. I have a Zydas1211 chipset ... Asus WL-169

Help would be appreciated

---

### Post by psyke83 on 2007-04-27
Yoeri,

I posted a partial fix a while ago, see here: [http://ubuntuforums.org/showthread.php?t=405489&highlight=zd1211](http://ubuntuforums.org/showthread.php?t=405489&highlight=zd1211)

---

### Post by shof2k on 2007-04-29
I'm using a safecom SWLU-5400 with the ZD1211 chipset.  Feisty works with the ZD1211RW driver, although it's at a slower speed.  Is your problem specific to the ZD1211B chipset?

---

### Post by Yoeri on 2007-04-29
it is the ZD1211 chipset. I already downgraded back to Edgy because I was not able to solve the problem...

---

### Post by shof2k on 2007-04-29
Can you ping an address or connect to an unsectured network.

If you can ping, then the network stack is fine.

If you can connect to an unsecured network, then the wpa_supplicant is at fault.

---

### Post by Yoeri on 2007-04-30
Hardware is fine, I can see that everything gets initialized correctly (dmesg).

I can scan for wireless networks (iwlist scan). I cannot ping a network neither I can connect to an unsecured network. Is there a difference between the zd1211rw and the "normal" zd1211 drivers?

---

### Post by BatPenguin on 2007-05-19
Hello,
I thought I'd try asking for help here: I'm trying to get my zydas zd1211 wireless USB adaptor to connect at 54 Mb/s. It's connecting fine at 11 Mb/s but so far I'm not getting anywhere with faster connections. It's plugged into a USB 2.0 port and should work fine, I believe, but so far nothing. Does the zd1211rw driver only support 11 Mb/s?

The adapter is: 
Bus 005 Device 002: ID 0ace:1215 ZyDAS

and I'm using Feisty. It's pretty much working out of the box with the zd1211rw driver, only problem is this connection speed. I used to have it plugged into a USB 1.1 port so that could be the problem -- maybe it's "remembering" to connect at 11 Mb/s or something like that? I installed a new USB 2 add-on card for this, should be working fine I believe.

I'd really appreciate help on getting the speed up to 54 Mb/s. This machine is going to be a Mythtv frontend and I need the extra speed for playback. I'd be happy to give extra information! Thanks a lot.

---

### Post by logos34 on 2007-05-22
> **BatPenguin said:**
> Hello,
I thought I'd try asking for help here: I'm trying to get my zydas zd1211 wireless USB adaptor to connect at 54 Mb/s. **It's connecting fine at 11 Mb/s** but so far I'm not getting anywhere with faster connections. It's plugged into a USB 2.0 port and should work fine, I believe, but so far nothing. Does the zd1211rw driver only support 11 Mb/s?

The adapter is: 
Bus 005 Device 002: ID 0ace:1215 ZyDAS

and I'm using Feisty. It's pretty much working out of the box with the zd1211rw driver, only problem is this connection speed. I used to have it plugged into a USB 1.1 port so that could be the problem -- maybe it's "remembering" to connect at 11 Mb/s or something like that? I installed a new USB 2 add-on card for this, should be working fine I believe.

I'd really appreciate help on getting the speed up to 54 Mb/s. This machine is going to be a Mythtv frontend and I need the extra speed for playback. I'd be happy to give extra information! Thanks a lot.

I noticed that too (though while running the liveCD).   

You can try changing it manually like this:

**sudo iwconfig wlan0 rate 54M**

---

### Post by BatPenguin on 2007-05-23
> I noticed that too (though while running the liveCD).

You can try changing it manually like this:

sudo iwconfig wlan0 rate 54M

Thanks for the reply! I really appericiate it. 

I tried doing this and got 

Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; No such device.

It seems like my wireless is eht1...and when i try setting that for it, nothing happens. No erros but also no change in the speed. I've tried disabling it and setting that again...no change. Any ideas?

---

### Post by shof2k on 2007-05-23
>   sudo iwconfig eth1 rate 54M


Worked here.  You need to change 'eth1' to whatever your interface is called.  It is usually eth1 or wlan0.  Typing 'iwconfig' afterwards should confirm if the change has worked.

I've no idea if this really has changed the link speed as I'm on a 2Mb connection, but things appear faster.

---

### Post by BatPenguin on 2007-05-24
OK, thanks...with "iwconfig" I can confirm that it did accept the 54M speed. But won't work...I can still see the wireless network but it won't connect. Connects fine when I set it back to 11M. Strange.

Is there a way to set it to permanently use the 54M speed? Like a config file somewhere that says that...I'd like to see if it would work on the first try -- now I have to see if connect at 11M, enable 54M, and see how it fails at connecting. Would be nice to see if it'd work on the first try connecting at 54M. Thanks again.

---

### Post by logos34 on 2007-05-25
> Is there a way to set it to permanently use the 54M speed?

Open up **/etc/network/interfaces**

try adding this line:

**wireless-rate 54M**

---

