---
title: "Having troubles installing Netgear WG111v2 in Feisty"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by ~vel on 2007-04-19
I tried following the instructions given [here]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111") and I skip down to the bottom and start with the directions given for Edgy and I'm unable to install build-essentials, let alone knowing how to compile the .tar.gz. Help anyone?

---

### Post by cody50 on 2007-04-19
I was having troubles too. It could see the network but when it tried to connect it wouldnt go through. It worked fine in the feisty beta but not so much the release. I thought it was something with my router so i'm still working through some things.

---

### Post by ~vel on 2007-04-19
For me I can't even see it in Network Manager, I just see an option for a dial up modem which I don't have and my Ethernet as eth0, but that's it.

---

### Post by cody50 on 2007-04-19
now mine won't even work in the beta. That is wierd. It worked like a week ago fine on the beta live cd. no ndiswrapper or anything. i guess that is what i will try next.

---

### Post by cody50 on 2007-04-19
Anyone know if the edgy tutorial to use ndiswrapper would work in feisty?

---

### Post by Daniel Rehm on 2007-04-19
Contrary to doc, gtkndis and ndiswrapper do not appear to be included on the CD this time?

---

### Post by ~vel on 2007-04-19
correct. 

can someone please help? right now i'm stuck at installing build-essential, mainly its dependancies. i'm unable to install libc6-dev because the only version i can find is 2.3.6 and the version installed on fieisty is 2.5 something and it won't install with the newer version. i'm seriously about to give up on this, i've been restarting, switching between windows and ubuntu trying to work this out on my own (and i'm very new to linux) for 2 hours and no matter what i do i hit a dead end. is there any alternative to installing ndiswrapper from a tar.gz without using build-essential? maybe a different program with less dependencies?

---

### Post by vak on 2007-04-20
Looks for me like in fresh deployed Ubuntu7 the WPA2 for NETGEAR wg111v2 is not supported, maybe WPA too. But the WEP support seems to be OK and SSIDs are gathered from air at least.

---

### Post by JohnUK89 on 2007-04-20
WPA is supported in Feisty using the native module, you just need to configure it manually, instead of using NetworkManager.

The way I did it was this:

EDIT: You shouldn't need to remove NetworkManager for this to work. I didn't, and it works perfectly. I just had to remove the applet from my startup.

1. Generate WPA key

```
wpa_passphrase <SSID> <ASCII-Key>
```

Where <SSID> is the SSID of your router/access point and <ASCII-Key> is the WPA key you would normally enter.

2. Copy the output from that into /etc/wpa_supplicant.conf. You should have something like this: (If the proto and key_mgmt lines aren't there add them exactly as shown) 

```
  network={
        ssid="SSID"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=945609a382413e64d57daef00eb5fab3ae228716e1e440981c004bc61dccc98c
  }

```

3. Edit your /etc/network/interfaces file to include the following:

```
auto wlan0
inet wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

```

4. Restart networking:

```
sudo /etc/init.d/networking restart
```

5. Enjoy your wireless! :) 

I am not sure about WPA2 support, I'm unable to test it due to not having any WPA2 capable access points.

---

### Post by ~vel on 2007-04-20
i'm not using any sort of security, my network is completely open. ubuntu isn't even showing anything for wlan0

---

### Post by cody50 on 2007-04-20
I just tried my same adapter from the 7.04 live cd at a different WAP and everything worked perfectly out of the box (no encryption). I guess I have to do something with my router.

---

### Post by JohnUK89 on 2007-04-20
> **~vel said:**
> i'm not using any sort of security, my network is completely open. ubuntu isn't even showing anything for wlan0

You could try ndiswrapper then, you'll need the Windows ME drivers for the card and the packages ndiswrapper-common and ndiswrapper-utils-1.9 installed. The packages are attached, and the drivers can be found at [ftp://downloads.netgear.com/files/wg111v2_1_4_0.zip](ftp://downloads.netgear.com/files/wg111v2_1_4_0.zip)

1. Extract the drivers from the zip file

2. Blacklist the modules for the card. 

```
gksudo gedit /etc/modprobe.d/blacklist
```

Add the following to the end of the file:

```
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist r8187
```

3. Install the driver into ndiswrapper

```
sudo ndiswrapper -i /path/to/driver/Driver/WINME/net111v2.inf
```

4. Check the driver has installed correctly

```
ndiswrapper -l
```

This should output the following:

```
net111v2 driver installed, hardware present
```

You're mainly looking for the driver installed, hardware present part. if that's there continue to step 5. If not make sure no modules are loaded for the card and try again.

5. Install the ndiswrapper module:

```
sudo ndiswrapper -m
```

This will add the interface to your configuration.

6. Add ndiswrapper to your modules file:

```
gksudo gedit /etc/modules
```

Add the word ndiswrapper to the bottom of this file

7. Reboot and try NetworkManager again.

EDIT: Oops, forgot to attach .debs, they're there now

---

### Post by vak on 2007-04-20
> **JohnUK89 said:**
> WPA is supported in Feisty using the native module, you just need to configure it manually, instead of using NetworkManager.
...

unfortunately didn't work for me. well, i ve made few changes which were logical to my undestanding, but with no final success:

1. 

```

auto wlan0
inet wlan0 inet dhcp

```

to

```

auto wmaster0
iface wmaster0 inet dhcp

```

2. tried to change  "proto=WPA" to  "proto=RSN"

anyway no success.

meanwhile i get error message like: "wmaster0: unknown hardware address type 801"

---

### Post by ~vel on 2007-04-20
I managed to get ndiswrapper installed as well as the drivers but when i do ndiswrapper -l it only says net111v2 driver installed. it doesn't say hardware present at all and my dongle won't light up.

---

### Post by ~vel on 2007-04-20
bump

---

### Post by anarchron on 2007-04-20
Hey guys, so from what I gather, Network Manager & WPA is broken for wg511 using ndiswrapper ?

Thanks

---

### Post by JohnUK89 on 2007-04-28
> **~vel said:**
> I managed to get ndiswrapper installed as well as the drivers but when i do ndiswrapper -l it only says net111v2 driver installed. it doesn't say hardware present at all and my dongle won't light up.

Probably because I forgot a module you needed to blacklist (d'oh!)

You need to add blacklist rtl8187 to the end of your module blacklist file (same method as above)

---

### Post by nicolas314 on 2007-04-30
For what it's worth: I succeeded in making my WG111v2 USB dongle work on Ubuntu, both Edgy and Feisty after I upgraded. It took me easily half a day, so I will try to document my steps as clearly as I can.

First: the dongle. Netgear apparently releases several different pieces of hardware under the same name, so your WG111v2 is probably not the same as mine. This does not make things easier. Maybe I was just unlucky but the CD that was included in the box had the wrong drivers for my dongle, so the thing did not even work under Windoze. Several hours of Googling later, I was trying a bunch of drivers downloaded here and there from the Net and finally got the stuff working on Windoze. At least I knew it was no hardware fault.

Back to Ubuntu: Windoze interestingly taught me I had a RealTek 8187 in the box so I went and installed all relevant drivers I could find on Ubuntu. None worked, so I turned to ndiswrapper, but the version provided on Edgy did not cut it either. A search on this forum showed that there were bugs in the distributed version so I ended up downloading the ndiswrapper source code and installed from scratch. That got ndiswrapper working.

Then I tried all possible Windoze drivers I could put my hands on and finally got it working with an old Win98 driver. The dongle is now working perfectly (netrtuw.inf). After a dist-upgrade to feisty, the thing is still working. I am still using the off-the-shelf version for ndiswrapper instead of the packaged Ubuntu version though.

You may want to have a look at the ndiswrapper web site:
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

Check out their Wiki in the List of supported cards. If you search for WG111v2 you will find lots of people have tried various drivers. I found the one I am currently using in this list somewhere, though I do not remember where.

Hope it helps putting you into the right direction

---

### Post by jharrop on 2007-05-27
Just wanted to report the above.

After spending several hours trying to get the ndiswrapper approach working, inspired by some of the comments of JohnUK89 above, I just went with the rtl8187 driver.  (I should have done this in the first place, given that ifconfig reported wlan0 before i tried any of the ndiswrapper shananigans).

I did have the WG111v2 dongle attached when i installed Ubuntu (x86_64).

So in the end all i had to do to make it work was create a wpa_supplicant.conf file, and put into /etc/network/interfaces:

```
pre-up wpa_supplicant -dd -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
```

What made me give up on the ndiswrapper approach was getting the following (despite having all the appropriate entries in the blacklist file):

```
ndiswrapper -l
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)

```

with this in /var/log/messages:

```
loadndisdriver: loadndisdriver: load_driver(359): couldn't load driver net111v2 
```

Hope this helps someone.

cheers

Jason

---

### Post by domz76 on 2007-06-27
Hi,

I also managed to get WG111v2 instaled in Fiesty using - 
ndiswrapper (the version supplied with fiesty)
a win98 driver

i know the correct drivers are used as now under the network manager dropdown > connect to other wireless network > [enter network name SSIS], wireless security >...

the WPA options are now listed (whereas only the WEP options were listed using the wg111 without ndiswrapper and the 98 drivers]

My main problem is that i can NEVER connect to my WPA network, just seems to time out!

My question is,  do we know for sure that the WLAN device supports WPA protocol???? Has anyone else made it work using WPA??

If not can someone rocommend a wLAN device for fiesty. This is my second try, the previous car which cam highly recommended (Orinnoco classic gold) does not work at all. I haven't ruled out the possibilty that my PCMCIA slot is faulty too, but ultimately a USB solution would be better...

Thanks
Dom

---

### Post by nicolas314 on 2007-06-27
Just wanted to bring confirmation: my WG111v2 USB interface is working perfectly well with Win98 drivers encapsulated in ndiswrapper, WPA mode. I am not using NetworkManager to handle connections though. All configuration definitions are stored into /etc/network/interfaces and /etc/wpa_supplicant.conf, and I start the network manually with /etc/init.d/networking restart.

You may want to try starting wpa_supplicant manually to check if it is successful in logging onto your network?

---

### Post by madeleine2383 on 2007-06-30
I am very new to Ubuntu and really don't understand how to do anything. I went out and bought the WG111v2 because i read it works out of the box. When i do lsusb it shows up. But from here i am lost!!!! the network manager wlan0 already is shown but i still can't connect. How do I get my card to work? If someone could break it down step by step and explain everything that would be great!!!!! I have been trying to get this to work for days and am about ready to pull all my hair out

---

### Post by nicolas314 on 2007-07-01
You will find attached the drivers I am currently using for my WG111v2 dongle. As mentioned above, they are Win98 drivers but as long as they work fine, no questions asked. Using the latest ndiswrapper version should get your card recognized. Check if you can do:

% iwlist wlan0 scanning

Next step is getting WPA to work. What I did was:
Edit /etc/network/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-ssid [Insert your network SSID here]
        wpa-ap-scan 1
        wpa-proto WPA
        wpa-pairwise TKIP
        wpa-group TKIP
        wpa-key-mgmt WPA-PSK
        wpa-psk [Insert your network encrypted key here]

```

You generate your key (wpa-psk) using wpa_passphrase.

It is important to specify 'wext' as driver for wpa_supplicant, even if your driver is ndiswrapper. I read that somewhere in the wpa_supplicant and lost a lot of time trying to get it to work with wpa-driver ndiswrapper.

The above configuration for /etc/network/interfaces should also work with other drivers. This is now the Debian (and Ubuntu) way of specifying WPA keys.

---

### Post by smoocat on 2007-07-06
Hi.  Relative newbie here.  I too have been trying to get my WG111v2 to work properly under Kubuntu Feisty.  

The native RTL8187 driver worked fairly well for me at the beginning, despite the light on my dongle not lighting up.  My main issue was that it would sporadically drop the connection, forcing me to reestablish the connection or unplug/replug the dongle.  (I checked to make sure it wasn't an ISP issue, as the PC connected directly to the DSL modem works perfectly fine.  This problem also didn't occur under XP.)

I decided to try out the ndiswrapper approach to see if it would resolve the issue.  I tried the XP, which ended up not working.  Then I tried both the Win98 and ME drivers from my Netgear cdrom, which showed up with the "device present" message.  The lights began blinking (yay!), but the KNetworkManager status bar never moved past "configuring device" status (around 20%), and never reached connectivity.  Now I'm left with no choice but to use Windows until I can resolve this issue (grrr..).  

I'm tempted to revert back to RTL8187, but the situation there was far from ideal.  That, and I sorta kinda deleted the files instead of backing them up/renaming them (I know, bad move), to avoid the "alternate driver:.." message in ndiswrapper.

Any advice would be greatly appreciated!

Good weekend to you all--

---

### Post by Krandog on 2007-07-15
I am an old timer when it comes to pay-to-play OS, but am only 3 days old for Linux, so forgive me if I am way off base here.  I chose Ubuntu for its supposed ease of use and stability.  When I built the system the other day, I didn't have an adapter, so I grabbed one off my TIVO box knowing that it would work with Linux.  It happened to be a Netgear MA111v1, and with very little tweaking using the following link
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111), I was able to get the adapter to work.  The next day I was off to the local Fry's to purchase the WG111v2 as I read that it worked out of the box and was similar to the MA111.  Like many of you I had problems.  At this point my adapter was showing up, but not showing that it saw the network. I was just about to use the ndiswrapper and blacklist my other drivers technique, when I got the idea to try something.  I changed the managed system form OpenSystem to SharedKey in the /etc/network/interface file. Unplugged/Replugged the adapter. I used manual configuration... to set up the network as that was my only option, and was told the interface file was updated. The network window still did not show that I was connected to a network,  as my MA111 did, but when launching firefox, it did connected to the internet.

It bothers me a little that Ubuntu does not show that I am connected to a network with the WG111 and that it would not work with OpenSystem as the MA111; but then again it bothers me less than not actually being able to connect to the network.  By the way, I am using WEP and used the Hex-passphrase in my configurations. Also the adapter has the RTL8187 chip

I don't know if this will help or not just one more WG111 frustrated users experience

---

### Post by musky on 2007-07-15
> **Daniel Rehm said:**
> Contrary to doc, gtkndis and ndiswrapper do not appear to be included on the CD this time?

Anyone know if this is correct? Not sure cuz quite clueless about ubuntu & fiddlin with wifi but don't seem to have ndiswrapper installed with Feisty, but it seems that others do? (or is there an easy way to check?)

At any rate, looks like I found a thread that will help me with the wg111v2 & with this note am up to 3 beans:)

---

### Post by musky on 2007-07-15
> **Krandog said:**
> I The next day I was off to the local Fry's to purchase the WG111v2 as I read that it worked out of the box 
Me too (& so did someone else in this thread message #22) 
Info is here
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

Mines not showin up at all (yet) :( ..bit of a bummer

---

### Post by musky on 2007-07-16
Maaaan! BINGO =D>Dun it just last night & got a wifi connection with feisty..my first Ubuntu. What a distro so far.:D

Bit of a story. Lost count of the # of days spent tryin to sort out the wifi & was really startin to be a royal pia:mad: Had what appeared to be 2 promising usb adapters kickin about one being the netgear wg111v2 which is advertised as plug & play.

Well..turns out it is but with a twist. Seems to be working out that way right now, the only thing is I have to **plug it in after the 'pute boots up**. If I boot the 'pute with the usb dongle plugged in..nothing, nada, doesn't even show up.

Plug & play folks,\\:D/ no fiddlin..at least on this emachines c3060

Maan..I still can't believe I got the wifi goin:guitar:

Cheers!

EDIT- Connection just dropped:(..oh well, prob  some fine tweakin stuff (hope..):)..i gather from the ton a readin I dun so far..seem to be alota scenarios..
Never seen this before (may be normal in Ubuntu..dunno) but in the Network Settings GUI, 2 wifi interfaces show up. One sez 'Wireless connection (master0)' & the other sez 'Wireless connection (wlan0)'. I'm still fiddlin but seemed to work by only havin the wlan0 checked off. Also interesting is that the wifi light on the usb dongle doesn't seem to light up when the wifi is connected. Do get a brief flash when I plug it in.
EDIT-Ok, reboot, plugged in the usb, hada punch a few things & got the wifi back.:) See what happens..

---

### Post by musky on 2007-07-17
Update - lost the signal a few times now but good long stretches (~6- 8 hrs straight) that it's workin out.:)
Been able to get the connection back a few times without a reboot. Dunno what to make of this double wifi interface showin in the network GUI that shows 'master' & 'wlan0'. Seems to work better (or only) sometimes with just wlan0 checked off & other times with both checked off.
EDIT - works great for long stretches but acts up...needs to be sorted out. Dunno how to go about it myself but quite thrilled to be runnin wifi with fiesty :)..for now..

---

### Post by AscendedDaniel on 2007-08-02
Kubuntu (feisty) seems to recognize the device right away. However, when I try to connect to a wireless network, it stalls at 28% - configuring device. But it can see the networks just fine. Any ideas how to fix this?

---

