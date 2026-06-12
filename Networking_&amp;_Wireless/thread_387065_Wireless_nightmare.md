---
title: "Wireless nightmare"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by DiscoKiller on 2007-03-17
hi all, 

i`m having a bit of a nightmare with my wireless card, it would appear that every time i wish to use it i have to sudo into my wireless lan assistant and also open another terminal, sudo modprobe bcm43xx then sudo dhclient....

thats a heck of an effort when in my last install, all i did was install ndiswrapper and it worked every time. i was wondering if anyone could tell me how to tell ubuntu to wake the lan card up and connect automatically on boot up, i miss the good old days of my last install

let me know if there is more info i can supply to solve this riddle, i`ve searched the forums enough for now!!

cheers


DK

---

### Post by gradedcheese on 2007-03-17
Post the contents of your /etc/network/interfaces file, that would be helpful.  By the way, you have a Broadcom card and Broadcom is one of the three worst chipsets for Linux.  If you can, replace it with a card from a better chipset company and you'll have a much more pleasant time.  You can read [this article I wrote]("http://andrey.thedotcommune.com/wireless.html") for more information, if that interests you.

---

### Post by DiscoKiller on 2007-03-17
here is the output

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth0



iface eth1 inet dhcp
wireless-essid belkin

auto eth1

unfortunately i am too poor to get a new card :(

thanks for your help tho

DK

---

### Post by gradedcheese on 2007-03-17
Which is the name of your real wifi interface?  You can run:

```

iwconfig

```

to see what has wireless extensions.  Is it wlan0?  eth1?  You can delete the lines having to do with ath0 as well as eth2 for starters.  Edit that file with sudo (ex: "gksudo gedit /etc/network/interfaces" should work)

---

### Post by DiscoKiller on 2007-03-17
here is the result if the iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"belkin54g"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:12:BF:48:34:7B   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=48/100  Signal level=-68 dBm  Noise level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


thats with everything up and running. 

i`ve edited the interfaces file accordingly

---

### Post by gradedcheese on 2007-03-17
Ok, so now all you need is for "bcm43xx" to get modprobed by default when you boot (the network scripts will take things from there).  To check if that is not the case, reboot and run lsmod.  You can force it if you want to try that, just add "bcm43xx" on its own line in /etc/modules and reboot.

---

### Post by DiscoKiller on 2007-03-17
i do have bcm43x in my modules list already, the problem now lies with having to run sudo dhclient in order to connect to the wireless network

i can cope for now

thanks for all our help dude, if u think of anything then i`d reall appreciate your views

cheers

DK

---

### Post by gradedcheese on 2007-03-17
Hmm, this part of /etc/network/interfaces tells dhclient to run:

```

iface eth1 inet dhcp
wireless-essid belkin

```

Now, you are absolutely sure that the module got loaded at bootup?  If you boot up and run:

```

lsmod | grep bcm

```

...it shows the loaded module?  If that's the case then I am not sure why dhclient would have to be run manually, it should happen when /etc/init.d/networking runs...

---

### Post by DiscoKiller on 2007-03-18
> ~$ lsmod | grep bcm
bcm43xx               127252  0 
ieee80211softmac       33792  1 bcm43xx
ieee80211              35272  2 bcm43xx,ieee80211softmac


all looks above board to me, it seems necessary to run dhclient and my wireless assistant together in order to connect to the network....odd eh?


cheers 

DK

---

### Post by chili555 on 2007-03-18
I believe the problem is that this part: ```
iface eth1 inet dhcp
wireless-essid belkin
```really should read ```
auto eth1
iface eth1 inet dhcp
wireless-essid belkin**54g**
``` I assume the omission of 54g was a typo?

sudo gedit /etc/network/interfaces to amend and reboot and let us know.

---

### Post by DiscoKiller on 2007-03-18
thank you both for your time!

i edited my interfaces file as you said chili555 and it worked a treat!

not sure how i didn't spot that but i suppose I`ve stared at it long enough to not notice!!

thanks again to both of you

i`m happy again....

cheers

DK

---

