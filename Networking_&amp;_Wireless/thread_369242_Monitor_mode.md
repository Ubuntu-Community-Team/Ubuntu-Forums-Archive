---
title: "Monitor mode"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by kuro2ck on 2007-02-24
Hey. had an awesome install, everything worked first time except ati. but then got that going within 10 mins. but when i come to use aircrack/airsnort etc. i need to put my wifi card in monitor mode. when i use airmon to do this all i get is the below permission denied. anyone had this before?


$ \airmon-ng stop etc etc...........

interface              chipset              driver
ath0                atheros                mad-wifi-ng VAP (parent: wifi10)
SIOCSIFFLAGS: permission denied
wifi0                atheros                mad-wifi-ng


cheers,

Craig.      and yeah i've tried it with sudo before the command :)

---

### Post by chili555 on 2007-02-24
I would try, before you run aircrack, sudo iwconfig wifi0 mode monitor. And after, sudo iwconfig wifi0 mode managed.

A number of these programs seem to have a bit of difficulty automagically putting any and every card in monitor mode and then back in managed mode as they close.

---

### Post by kuro2ck on 2007-02-24
thanks for quick reply i get the below

$ sudo iwconfig wifi0(also tried ath0) mode monitor
Error for wireless request "Set Mode" (8B06)   :
      SET failed on device wifi0 ; Invalid argument.


thanks. 


as you can tell i aint the best with linux. only just really started.

---

### Post by kuro2ck on 2007-02-24
should i be using the drivers that got installed with ubuntu or should i use ndiswrapper and try use xp drivers?

---

### Post by spd106 on 2007-02-24
For the Atheros cards on Edgy you need the wlanconfig tool, sadly this isn't included so you will have to install the madwifi-tools debian package (see [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)).

If you stand to wait a few days the package is being backported from Feisty.

---

### Post by kuro2ck on 2007-02-24
What command follows this to get it into monitor mode?  i installed the packacge, but when i do the sudo iwconfig ath0 mode monitor      it doesnt recognise it, it does up to mode and seems to take intergers after that.

could wait for feisty if i have to, just owuld like a work around for now :)

---

### Post by kuro2ck on 2007-02-24
will also take managed after mode but not monitor.

---

### Post by spd106 on 2007-02-24
I strongly urge you to read the documentation on [http://madwifi.org](http://madwifi.org), it's not very long.

Basically, you have to destroy ath0 and create a new ath0 in monitor mode. This is a slightly more complicated way of doing things, but it brings about some advantages.

To get you started try these commands:
```
sudo ifconfig down ath0
sudo wlanconfig ath0 destroy
sudo wlanconfig ath create wlandev wifi0 wlanmode monitor
sudo ifconfig ath0 up
```

---

### Post by kuro2ck on 2007-02-24
can i just say you are a :KS    :) 

i wasnt reading it right, destroying the interface and creating another worked a treat. 

now onto using airodump correctly lol, was easy enough on windoze.

thanks

---

### Post by obelisk on 2007-02-26
I guess I'm having a similar issue and I tried the fix but it's not recognizing the wlanconfig tool and I read through the madwifi site but I didn't see any mention of this issue. Any ideas?

---

### Post by Funkwheat on 2007-04-19
I'm having a similar problem.  I'm not able to switch my atheros card into Monitor mode either.  I've been trying to read up on it but can't find much info on this particular issue.  I tried following these instructions here:  [http://www.aircrack-ng.org/doku.php?id=airmon-ng](http://www.aircrack-ng.org/doku.php?id=airmon-ng) exactly, but whenever I do that I end up with an ath1 and no ath0; then ath0 comes up as nonexistant when I try to bring it back up (Using ifconfig OR airmon-ng)... Ath1 does show up in monitor mode, but it doesn't detect any networks at all.

> **spd106 said:**
> I strongly urge you to read the documentation on [http://madwifi.org](http://madwifi.org), it's not very long.

Basically, you have to destroy ath0 and create a new ath0 in monitor mode. This is a slightly more complicated way of doing things, but it brings about some advantages.

To get you started try these commands:
```
sudo ifconfig down ath0
sudo wlanconfig ath0 destroy
sudo wlanconfig ath create wlandev wifi0 wlanmode monitor
sudo ifconfig ath0 up
```

I also tried this out, and still no dice.  Ended up with an ath1 again.  :confused: 
And yes I did note the typo on line 1 :lolflag: 

I also might add, that the only way I even know of to fix this right now is rebooting the entire computer.

Any ideas anyone?  Any help would be appreciated!  thanks :D

I am using the most recent version of Ubuntu (7.0.4 I believe?)...yeah the one that came out today.

---

### Post by Funkwheat on 2007-04-20
Anybody got any info on this?  ;)

Please excuse the bump! ;)

---

### Post by tturrisi on 2007-04-20
How I got aircrack-ng to work.

I'm running Etch using latest madwifi drivers, compiled & installed using module-assistant.
Downloaded aircrack-ng from its site, untared and ran make & make install.
Then followed the tutorial here:
[http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)
It works!

ubuntu users should be able to just follow that tutorial and be in business.

---

### Post by Funkwheat on 2007-04-20
That's actually the same guide I'm using...  Just for some reason as soon as I start wifi0 back up, it starts an ath1 instead of ath0.  Then I can't ever get ath0 back up without rebooting (and ath1 does not function)....  Any ideas? :(

---

### Post by tturrisi on 2007-04-20
ubuntu may still need the madwifi patches to work with aircrack-ng
[http://www.cus-productions.com/index.php?option=com_content&task=view&id=69&Itemid=34](http://www.cus-productions.com/index.php?option=com_content&task=view&id=69&Itemid=34)

---

### Post by SamChameleon on 2007-06-13
Hello all,
I face the same problem as Funkwheat, except that I can create ath0 again and use it in managed mode. Perhaps this helps for you, too, Funkwheat:

You have to "destroy" ath1 and create a new ath0:
```

wlanconfig ath1 destroy
wlanconfig ath create wlandev wifi0 wlanmode sta

```

But why there is no ath0 in monitor mode and why airodump does not find anything I cannot tell.

---

### Post by sloeren on 2007-07-09
Has anyone found a solution to this problem?
And how about the SIOCSIFFLAGS permission denied message Kuro2ck originally reported...
I'm having the exact same problems: no ath0 in monitor mode, but ath1 instead, etc. etc.
Anyone, anything... ?

---

### Post by xerxesdaphat on 2007-11-04
Here's what I did.

So you've got your ath0 happily connected to the access point, you're connected properly and can use the internet and everything. Leave ath0 as it is.

Run this: [FONT="Courier New"]**sudo wlanconfig ath create wlandev wifi0 wlanmode monito**[/FONT]r

Now you've got another wireless interface -- ath1, which is in monitor mode. However, ath0 is still there! Don't worry. It's still connected too -- can surf the internet, do whatever you like.

Bring it up [FONT="Courier New"]**sudo ifconfig ath1 up**[/FONT] .

Now go into Wireshark, Aircrack, whatever you like, and for the device you're monitoring on choose ath1. The advantage of this method is that you can still happily remain connected and use your connection like normal via the ath0 interface, whilst monitoring and cracking on ath1. Can be different APs or whatever.

---

### Post by ajkirchner on 2007-11-27
after: sudo ifconfig ath1 up

i get... ath1: ERROR while getting interface flags: No such device

---

### Post by xerxesdaphat on 2007-11-27
Check that ath1 was the actual device created. Type iwconfig to list the interfaces and find the new interface that was created -- substitute ath2 or ath3 or whatever.

---

### Post by techflat on 2008-06-25
> **xerxesdaphat said:**
> Here's what I did.

So you've got your ath0 happily connected to the access point, you're connected properly and can use the internet and everything. Leave ath0 as it is.

Run this: [FONT="Courier New"]**sudo wlanconfig ath create wlandev wifi0 wlanmode monito**[/FONT]r

Now you've got another wireless interface -- ath1, which is in monitor mode. However, ath0 is still there! Don't worry. It's still connected too -- can surf the internet, do whatever you like.

Bring it up [FONT="Courier New"]**sudo ifconfig ath1 up**[/FONT] .

Now go into Wireshark, Aircrack, whatever you like, and for the device you're monitoring on choose ath1. The advantage of this method is that you can still happily remain connected and use your connection like normal via the ath0 interface, whilst monitoring and cracking on ath1. Can be different APs or whatever.

Hey ther xerxesdaphat

I tried that, and did a tcpdump with ath1 and with ath0, it seems that I get fuller information with ath0. (Keep in mind I'm new at this...)

Then, when I do iwconfig, this is the output:
```

ath0      IEEE 802.11g  ESSID:"xxx"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:xx:xx:xx:xx:xx   
          Bit Rate:12 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/70  Signal level=-74 dBm  Noise level=-88 dBm
          Rx invalid nwid:473  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Frequency:2.417 GHz  Access Point: 0A:xx:xx:xx:xx:xx   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/70  Signal level=-74 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
This makes me think that it's bound to a channel, is it? The tcpdump output apparently is about the network I am connected. How can I unbound ath1 of the network I am connected?

Is there some more configuration you didn't post about this needed prior to doing anything else?

Thanks in advance.
Cheers




**Edit**: The mac addresses for ath0 and aht1 in the iwconfig output are different but I changed them with xx for security purposes, you never know who's watching.

**Edit**: When I do (iwconfig ath1 channel 4) it changes on both interfaces, ath0 and ath1 so I'm supposing ath1 can only scan on the same frequency ath0 is scanning.



PS: Does anybody know some link about some tutorial on this, I mean iwconfig, wlanconfig and the interfaces creations and structure?

---

