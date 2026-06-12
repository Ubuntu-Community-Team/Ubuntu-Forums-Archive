---
title: "wusb54g using rt2500 - can connect to wireless netrwors but signal level not detected"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by boz on 2006-11-03
I have a Linksys WUSB54G using the rt2500 open driver.  The driver works great.  I have a fast internet connection, but no signal level is detected.  Here is my output from iwconfig:

```
          rausb0 RT2500USB WLAN ESSID:"*******"
          Mode:Managed  Frequency=2.462 GHz  Access Point: ************
          Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-71 dBm  Noise level:-202 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I know this is the connection that I'm using so no need to ask the obvious question:  Is he a dumb @** who doesn't realize he's connected to a wired network as well?  lol.

This is obviously not a huge issue, but it would be nice if I could use network manager.  I know this driver is still a bit buggy so I probably wouldn't be able to connect to a network through any graphical means, but I would at least be able to see the name of a network when I roam.  For instance, my wife changed the name of our wireless network at home and didn't bother to mention it to me.  I kept iwconfig'ing the old network name and beating my head against the wall when I couldn't connect.

Anyway, thanks in advance for any advice/suggestions.

---

### Post by wieman01 on 2006-11-03
I have a WUSB54G (V4) & I ditched RT2570 completely. The driver has a number issues. I would try "ndiswrapper" together with the Windows driver instead. See the last post of this:

[http://www.ubuntuforums.org/showthread.php?t=280176&page=2]("http://www.ubuntuforums.org/showthread.php?t=280176&page=2")

You will still be able to use the networking applet (Gnome), no problem.

_**EDIT:**_
The "real" howto from wiki: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by cantormath on 2006-11-03
> **boz said:**
> I have a Linksys WUSB54G using the rt2500 open driver.  

That card is evil, ditch it.......](*,)

---

### Post by wieman01 on 2006-11-03
> **cantormath said:**
> That card is evil, ditch it.......](*,)
It's not when you know how to make use of "ndiwrapper". If you perfer a native Linux driver, it's indeed a hassle.

_**EDIT:**_
Mine runs fine with WPA2 enabled. No issues at all (not anymore at least).

---

### Post by boz on 2006-11-05
Thanks for the advice, but I don't think I'll be ditching the card unless I become overwhelmingly frustrated.  I'm ditching the rt2570 driver and I'm going to try ndiswrapper.  I'm actually in the middle of doing so and I've already ran into some problems.  After I install the driver I can config the device on the command line, but it doesn't come up in the GUI at all.  Also, Network Manager doesn't recognize it, even after a restart.  Here's my output from iwconfig:

```

wlan0     IEEE 802.11g  ESSID:"tsunami"
          Mode:Auto  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by wieman01 on 2006-11-05
Have you blacklisted the Linux driver: rt2570?

Perhaps it is necessary taking a glance at this file:
> sudo gedit /etc/network/interfaces
Please post the contents.

Then scan for your network:
> iwlist scan
Also post the results. Then we'll see.

---

### Post by boz on 2006-11-05
Thanks.  I've through that song-and-dance routine a thousand times.  I finally decided to ditch this version of the Windows driver and downloaded one from a different source/date.  This one works fine.  I still haven't tried WEP with it, but it detects the signal level and it doesn't freeze.  It's already better than RT2570.

---

### Post by wieman01 on 2006-11-06
As I have said, I have the same device & it works with WEP as well as WPA... Here is a documentation on WPA2 and WPA1:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

I have tested WEP as well. No issues at all.

---

### Post by boz on 2006-11-06
Great how-to.  Thanks for the help.  My problem is that I take my laptop between school and work.  The network at school is open and my network at home uses WEP.  I'm not sure if my router is capable of WPA, but I'll check it out.  I tried connecting to my router at home last night, but nothin' doin'.  I think my wife may have changed the passcode without my knowledge, probably when she was drunk because she doesn't remember doing it either.  But I do know that the essid has changed mysteriously, so the key is probably different now as well.  But just to make sure I'm doing it right, let's say I set up my key to be all 9's from Windows about 2 years ago, as follows:

9999999999

I no longer use Windows, but I'm guessing I should be able to type the following:

sudo iwconfig wlan0 essid <My network> key 9999999999

Am I right?  I tried that last night and I couldn't connect.  If my wife changed the key, is there a way to change it back?  How can I tell?  I executed:

sudo iwlist wlan0 key

and it listed my old key, but it said two are available and didn't list the second.  It also listed the old essid as well as what I assume to be the new one when I executed:

sudo iwlist wlan0 scanning

By the way, I did ask my neighbors if they have a wireless network and they don't.  Besides, I know my wife well and the name of the new network suits her well.  I did notice, however, that this Windows driver is a bit particular.  I connected earlier this morning, forgot to disconnect, and came back an hour later.  It had disconnected from the network for some reason.  I executed ifup wlan0 and it didn't reconnect.  But then I disconnected the USB cable and reconnected it and it then connected to the network.  I didn't try that last night, so I'll try that again later tonight and see what happens.

Thanks again.  I'll see if my router supports WPA and try that how to after I get this mess at home cleaned up.

---

### Post by wieman01 on 2006-11-06
Yeah, it's kind of hard to advise if you don't really know the password & the other particulars of your network. I suggest you reset the router (there must be a switch on the back of the device) & start all over again. I am sure your router supports WPA (perhaps not WPA2 though). That done, simply post your interfaces file:

> sudo gedit /etc/network/interfaces
That a good way to start.

As for the disconnecting issue, we'll see to that later. I had the same problem with my card but could resolve it by change the router's settings for wireless.

---

### Post by boz on 2006-11-10
After I updated the router's firmware and reconfigured the wireless settings, everything worked fine.  I had tried the correct essid and wep before and I could get no connection until I updated the firmware.  That was kind of weird, but oh well.  It works and that's all that matters.

---

