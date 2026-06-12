---
title: "Wireless connection shows but doesn't work"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Ceciljchen on 2007-12-04
I've just installed Gutsy on an Acer Aspire 1350 laptop (40 GB HDD, 256 MB RAM, AMD Athlon XP). Everything installed fine (had a slight problem with the paritioning tho since i wanted to have dual boot XP and Ubuntu, but i managed to figure it out). With Gutsy running, i wanted to hook the machine up to my home network. The icon shows in the system tray but has an exclamation mark in a red triangle on it and the tolltip text says no network connection. It shows that i have a wireless network and indicates (what i think) is a signal strength and the radio button next to it is selected. 
I use a Linksys wireless router WRT54GS v5.1 (no security). Broadcast enabled. And on the laptop i've plugged in a Belkin wireles USB (FSD7050 v2). Belkin's support site doesnt seem to have a Linux driver for this product. Why can't i connect to the network if it picks up its presence? Am i missing something (apart from knowledge and experience) Yes, i'm a newbie when it comes to Linux, but i like tyring out new things and i finally got the chance to try Linux. Help would be appreciated.

I've gone through forum posts and the help manuals as well as checked the troubleshooting links but cant find anything to help (btw the help files mention something about a Device Manager in the Systems > Administration menu but i dont see it, just the Restricted Drivers Manager. Is that odd?)

PS. before i installed Ubuntu, i installed Kubuntu first, so i've actually got a triple boot system (WinXP, Kubuntu and Ubuntu). I dont even know where the connection settings and stuff in Kubuntu are but will get to that later.. Right now i'm more interested in exploring Ubuntu for the time being.
Thanks.

---

### Post by VaporTrace on 2007-12-04
Just a note that with no security, your neighbor could easily mimic your wireless broadcast, capture your wireless attention thus having you connect to his instead and capture everything you send or receive out your notebook.

Enable the restricted universal repositories and reload the repository list in package manager. Then update your system if you havent already. Its a heafty update.

Secondly, most drivers in linux are chip based and ususally are not supported by manufacturers in source code so different variants of drivers can be built for different variants of linux. Ubuntu uses Debian which I believe is the most stable and fastest of the full featured flavors of linux.
Since the manufacturers don't divulge the intricate details of their products and are reluctant to be frowned on by Microsoft in specific drivers for linux OS this problem isn't going away soon until someone developes a complete fool proof driver conversion utility designed for the fore mentioned bunch.

The last 3 years has been akin to light years in milage for linux for the average user.

Ubuntu has done a lot of work fine tuning the quirks that arise out of code coming from all portions of our solar system.
Ubuntu has been more than reliable in fixes and updates than Microsoft has ever boasted in (let alone actually doing so) to newly discovered vulnerabilities.

Stay tuned cause the tide is beginning to turn.

---

### Post by Ceciljchen on 2007-12-05
> **VaporTrace said:**
> Just a note that with no security, your neighbor could easily mimic your wireless broadcast, capture your wireless attention thus having you connect to his instead and capture everything you send or receive out your notebook.

Oh i'm aware of the securiy issues and i usually have WEP enabled and broadcasting off, in addition to allowing only specified MAC addresses, but i disabled ALL security features on the router just to eliminate any hurdles to my Linux experience (haha, right! :P). In any case i'm not really worried cuz the wireless wignals dont extend beyond 2 rooms, nevermind outside the house (and yeah, no signals. I checked). I'm paranoid like that. The thing is, i know at least straight off that it was router security messing with going online with my Ubuntu.

> **VaporTrace said:**
> Enable the restricted universal repositories and reload the repository list in package manager. Then update your system if you havent already. Its a heafty update.

*whooosh* That was the sound it made flying over my head :-s I'm sorry but i'm literally a Linux newbie, short of reading Instalation procedures ifrom magazine articles several years ago, I've only recently had the time and opportunity on my hands to try Linux. *sheepishly* first-time Ubuntu user here.
Where is this restricted universal repositories (the only thing i saw remotely similar was Restricted Drivers Manager in the Administration menu) and how do i go about doing what you said? I assumed from the next sentence that i would need to go online from Ubuntu to update, yes? so that means once i enable said repository thing, it should work? Could you (or anyone else who reads this) please elaborate on procedures i should follow?

> **VaporTrace said:**
> Secondly, most drivers in linux are chip based and ususally are not supported by manufacturers in source code so different variants of drivers can be built for different variants of linux. Ubuntu uses Debian which I believe is the most stable and fastest of the full featured flavors of linux.
Since the manufacturers don't divulge the intricate details of their products and are reluctant to be frowned on by Microsoft in specific drivers for linux OS this problem isn't going away soon until someone developes a complete fool proof driver conversion utility designed for the fore mentioned bunch.

The last 3 years has been akin to light years in milage for linux for the average user.

Ubuntu has done a lot of work fine tuning the quirks that arise out of code coming from all portions of our solar system.
Ubuntu has been more than reliable in fixes and updates than Microsoft has ever boasted in (let alone actually doing so) to newly discovered vulnerabilities.

Stay tuned cause the tide is beginning to turn.

Man, yeh that whole evil, proprietary "let's not share jack* with the world" attitude really pisses me off. Ya want people to use your stuff, make it more accessible. I have faith in the Open Source community though.

---

### Post by Ceciljchen on 2007-12-05
Oh and just in case i've strayed from the topic, i'm still not able to go online, same problems as stated above :( 
Help?

---

### Post by GSF1200S on 2007-12-05
> **Ceciljchen said:**
> Oh and just in case i've strayed from the topic, i'm still not able to go online, same problems as stated above :( 
Help?

Ehh.. weird. Ok, open up a terminal and type in these commands-

```
iwlist scanning
```

```
iwconfig
```


and post the results here...

---

### Post by Ceciljchen on 2007-12-05
Thanks. I'm at work right now but i'll be able to post the results up here in about an hour and a half.

---

### Post by Ceciljchen on 2007-12-05
> **GSF1200S said:**
> Ehh.. weird. Ok, open up a terminal and type in these commands-

```
iwlist scanning
```

```

lo               Interface doesn't support scanning
eth0          Interface doesn't support scanning
wmaster0  Interface doesn't support scanning
wlan0        No scan results

```

```
iwconfig
```

```

lo               no wireless extensions.
eth0           no wireless extensions.
wmaster0   no wireless extensions.
wlan0         IEEE 802.11g ESSID:" "
                  Mode:Managed     Frequency:2.48 GHz    Access Point: Not-Associated
                  Retry min limit:7      RTS thr:off      Fragment thr=2346 B
                  Link Quality:0         Signal level:0           Noise level:0
                  Rx invalid nwid:0        Rx invalid crypt:0              Rx invalid frag:0
                  Tx excessive retries:0         Invalid misc:0         Missed beascon:0

```

So that's what i got.

---

### Post by Ceciljchen on 2007-12-05
btw, i also ran an lspci command and that revealed:
.
.
.
00:12.0 Ethernet Controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
.
.

but no network controller or IEEE 802.11g or anything that i could make out was the wireless USB dongle.

I hope that helps in determining what's up with this thing.

---

### Post by kevdog on 2007-12-05
I want you to find the chipset out of your device - you will have to google for it.  This is the name of the microprocessor inside the device that actually does the wireless modulation.  Possible names for it would be Atheros, Broadcom, Ra (rtxxxx), intel, or something else.  By discovering the chipset, we can find the correct driver you are supposed to use for your device.  Also post the following:

lsmod

---

### Post by GSF1200S on 2007-12-05
> **Ceciljchen said:**
> ```

lo               Interface doesn't support scanning
eth0          Interface doesn't support scanning
wmaster0  Interface doesn't support scanning
wlan0        No scan results

```

```
iwconfig
```

```

lo               no wireless extensions.
eth0           no wireless extensions.
wmaster0   no wireless extensions.
wlan0         IEEE 802.11g ESSID:" "
                  Mode:Managed     Frequency:2.48 GHz    Access Point: Not-Associated
                  Retry min limit:7      RTS thr:off      Fragment thr=2346 B
                  Link Quality:0         Signal level:0           Noise level:0
                  Rx invalid nwid:0        Rx invalid crypt:0              Rx invalid frag:0
                  Tx excessive retries:0         Invalid misc:0         Missed beascon:0

```

So that's what i got.

Ok, just to see whats up, input these commands..

```
sudo ifdown wlan0
sudo ifup wlan0
iwlist scanning
```

If it returns results, then input the following:

```
sudo iwconfig wlan0 essid networkname
sudo iwconfig wlan0 key networkkey123
sudo dhclient wlan0
```
Remember to substitute networkname and networkkey123 with your actual wireless network and wep key, respectively. If you dont have a WEP network, dont put in the key part. If you run WPA, well thats a completely different animal... 

You should get a dhcp offer and be bound back to an IP address.

---

### Post by Ceciljchen on 2007-12-05
Turns out that my chipset is this:


Card: Belkin F5D7050 (USB 2.0 Adaptor 802.11g 54Mbps)
Chipset: RT2500
usbid: 050d:7050
Driver: Install the drivers for windows included in the box and fetch the .inf files from the installation directory.
Other: Works fine. When entering in resume mode, freeze the system.


As for the commands, well i'm off to work now so will have to get back in the evening to do that :(

dangit, i hate this ridiculous time difference.

---

### Post by kevdog on 2007-12-05
Ok for the rt2500 card, you basically have two choices -- either serial monkey or ndiswrapper.  Ubuntu ships with built-in drivers for the card (not sure if these are from ra), however they do not really work that well.  Id probably suggest the serialmonkey drivers since they are native linux drivers, however the ndiswrapper(windows driver) combination will also work.

---

