---
title: "How to install Eicon DIVA ADSL USB???"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by vreemde eend on 2005-07-02
hi,

I installed Ubuntu, no problems, except that I can't connect the internet. I can't install Eicon DIVA ADSL USB modem. Any thaughts?

thanks,

vreemde eend

---

### Post by vreemde eend on 2005-07-02
I'm already a little bit closer:

1. [http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe)

2. dpkg -i eciadsl-usermode_0.10-1_i386.deb

(the latter is a driver I got from [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/) )

I get the following error (or something like this) 
package pppoe is needed, but isn't installed.

I really don't know what I have to do now.

Help,

thanks.

---

### Post by vreemde eend on 2005-07-03
[This](http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2947) helped me to come a little bit closer to my goal, but I still can't connect internet. I hope someone can help me out. Here are some messages:

```


[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

eciadsl-firmware: success
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

Progress indicator is 01 No Signal !
Progress indicator is a0 No Signal !
Progress indicator is a1 Training...
Progress indicator is a1 Training...
Progress indicator is 43 Training...
Progress indicator is a4 Training...
Progress indicator is a4 Training...
Progress indicator is 74 Training...
Progress indicator is a6 Training...
Progress indicator is 77 Training...
Progress indicator is 75 Training...
Progress indicator is aa Training...
Progress indicator is 72 Training...
Progress indicator is ad Training...
eciadsl-synch: success
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 3
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <magic 0x9af4b277>]
rcvd [LCP ConfReq id=0x47 <mru 1500> <auth chap MD5> <magic 0x6815b471>]
sent [LCP ConfAck id=0x47 <mru 1500> <auth chap MD5> <magic 0x6815b471>]
rcvd [LCP ConfAck id=0x1 <magic 0x9af4b277>]
rcvd [CHAP Challenge id=0x3 <497256d93144fc2646bd924552f3ddf1>, name = "BAS-GENT"]
sent [CHAP Response id=0x3 <a0bb545e245e1d7c46966b093e11c31c>, name = "agwi0004@tiscali.be"]
rcvd [CHAP Success id=0x3 "CHAP authentication success, unit 12197"]
CHAP authentication succeeded: CHAP authentication success, unit 12197
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0xc0 <addr 83.134.71.1>]
sent [IPCP ConfAck id=0xc0 <addr 83.134.71.1>]
rcvd [IPCP ConfNak id=0x1 <addr 83.134.71.228> <ms-dns1 62.235.14.4> <ms-dns3 62.235.13.199>]
sent [IPCP ConfReq id=0x2 <addr 83.134.71.228> <ms-dns1 62.235.14.4> <ms-dns3 62.235.13.199>]
rcvd [IPCP ConfAck id=0x2 <addr 83.134.71.228> <ms-dns1 62.235.14.4> <ms-dns3 62.235.13.199>]
local  IP address 83.134.71.228
remote IP address 83.134.71.1
primary   DNS address 62.235.14.4
secondary DNS address 62.235.13.199
Connection successful

[EciAdsl 5/5] Setting up route table...

Waiting for ppp0... 
Adding default route... default route to ppp0 already exists


```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
83.134.72.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         83.134.72.1     0.0.0.0         UG    0      0        0 ppp0

```

```

ppp0      Link encap:Point-to-Point Protocol
          inet addr:83.134.72.181  P-t-P:83.134.72.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:5966 (5.8 KiB)  TX bytes:6811 (6.6 KiB)

```

---

### Post by vreemde eend on 2005-07-03
We keep talking to ourselves... . I was able to ping to my remote ip-address and to google. There should be a DNS-problem. Anybody knows how to resolve this?

thanks a lot,

vreemde eend

---

### Post by vreemde eend on 2005-07-03
I was able to ping to [www.google.com](www.google.com) (the domain, not the ip-address). Firefox doesn't react on ip-addresses, neither on domain-names... . Anybody knows what could be going wrong????

---

### Post by vreemde eend on 2005-07-03
Problem solved!

apt-get update
apt-get upgrade

nothing less, nothing more

---

### Post by vreemde eend on 2005-07-03
Problem popped up again. I can ping ip-address and domain names (both as root or as normal user). I can't:
1. apt-get update
2. use firefox
3. gaim hangs on authentification
4. evolution hangs on: receiving message 1 of 3

I rebooted and disconnected/connected so may times, that I can't count it anymore. As it worked once, I'm quite close to having Internet with Ubuntu. Any suggestion what might be the cause?

help!!!!!

---

### Post by vreemde eend on 2005-07-04
I was using the wrong synchonisation file, should use synch05.bin.

---

### Post by Strapatzer on 2005-07-14
Vreemde eend, 
Could you specify what needs to be done after the installation ?
Fist of all get the driver, I guess. (Probably fits on  a floppy)
And then install rp-pppoe > how ? 
And then ?

---

### Post by GTvulse on 2005-07-14
I'm not Vreemde eend, but I did it for a Xavi 8005QII , which is an USB ADSL bridge, just like the Eicon DIVA, but with a GlobeSpan 7470 chipset, a.k.a. "Nortek" because the author of the port for that usermode driver owns a Nortek 2021 brand USB ADSL bridge. Same Xavi ADSL bridge I'm using to establish this connection from Ubuntu... The original driver is called eciadsl btw, because the original author uses an ECI brand USB ADSL bridge (mostly sold by France Telecom).

[list]
[*] Go to [http://packages.ubuntu.com](http://packages.ubuntu.com). If you are using an ADSL bridge with an older GlobeSpan chipset (such as the DIVA) download the eciadsl debfile available in Universe. Install it. Configure following instructions at [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/) 
[*] If you have an ADSL bridge with a "Nortek" chipset (GlobeSpan GS7070 or GS7470) grab the deb file for checkinstall from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install build-essentials from your installation CD. Go to [http://eciadsl.flashtux.org](http://eciadsl.flashtux.org) and download the nortek "alpha" sourcecode. **Do not** download the deb file, as it contains a **bogus** dependency to rp-pppoe. Unpack the source code file, configure and install:
```

-$ ./configure --prefix=/usr
-$ make
-$ sudo checkinstall 

```
Follow the checkinstall script instructions. Next time you open Synaptic, you'll have a group entry called checkinstall that will allow you to remove the eciadsl-nortek driver.

Copy the synch files from the GS7470_SynchFiles directory to /etc/eciadsl and run the configuration script following the instructions in the website mentioned above. The eciadsl deb file for older chipsets available in the Universe repository already includes the synch files, (which are different to the "Nortek" ones).
[/list]
** Again, rp-pppoe is not necessary, really.** As well, you can know with a large degree of certainty what kind of modem you have by consulting the online database at the eciadsl website.

---

### Post by vreemde eend on 2005-07-14
The poster above knows a lot more about the subject than I do, but I'll just try to explain how i got it working. 

(I think rp-pppoe is indeed useless.)

1. check wether your modem is supported by eciadsl: [http://eciadsl.flashtux.org/modems.php?lang=en](http://eciadsl.flashtux.org/modems.php?lang=en) . Important: pay attention to the reccomendent synchronisation file! First I was using the default, wich didn't work for me. 
2. download [http://packages.ubuntu.com/hoary/net/pppoe](http://packages.ubuntu.com/hoary/net/pppoe) (you probably have to click on i386, just in case you wouldn't know (powerpc -> apple))
3. download eciadsl (debian i386(?)) AND the extra synchronisation files 
4. sudo dpkg --install pppoe_3.5-4ubuntu1_i386.deb
(your password)
5. sudo dpkg --install eciadsl-usermode_0.10-1_i386.deb
6. sudo eciadsl-config-text (VPI: 8 VCI: 35 (is het nummer dat je in Windows moet bellen (configuratie)))
7. sudo eciadsl-start | tee log.txt (start modem)
!!Als het niet meteen lukt: modem unpluggen (even zonder stroom zetten)!!!

I hope this was clear, if you stille have problems: just post them, maybe I or someone else can help you.

---

### Post by bertvkb on 2006-11-02
hello,

I have just done a Ubuntu install, and I'm now trying to install the Eicon Diva USB Modem on it.
I have done everything "Vreemde eend" has explained, and when I start the modem (the last command in the row) this gives me that there are 5 steps to go through. The first 3 work just fine (the 3th, synchronization, is really slow but eventually it works..)

The 4th step is the problem: he can't connect.
I investigated the problem on my pc a bit:
the script tries to link the ppp0 interface with some channels I guess (channels 1 .. 10 ~ /dev/pts/1..10). but it just doesn't work. There are a couple of possibilities of what could be the problem:
* when I go to Management / Network it says eth0 is active, but ppp0 is not configured.
* when I inspect /dev/pts there is only one file with the name 0, and a size of 0 bytes, and this file is not selected as channel in the 4th step of the modem-start-script.

Maybe somebody who knows what the problem is and what to do about it?

---

### Post by vreemde eend on 2006-11-03
some things I could think of that might have gone wrong:

1. do you use the right synchronisation file (I thought that it was nr 5 for DIVA ADSL)
2. download [http://packages.ubuntu.com/hoary/net/pppoe](http://packages.ubuntu.com/hoary/net/pppoe) this is for Ubuntu Hoary! I think you need [http://packages.ubuntu.com/dapper/net/pppoe](http://packages.ubuntu.com/dapper/net/pppoe) or [http://packages.ubuntu.com/edgy/net/pppoe](http://packages.ubuntu.com/edgy/net/pppoe)
6. (VPI: 8 VCI: 35 -> these numbers are for Belgium, together they form the number you have to call in Windows (8,35 in my case))
7. sorry, there was something written in Dutch: if it doens't succeed: unplug the modem (te power cable) and try again

As most thing succeed the I think the problem could be that your connection settings or synchronisation file is wrong

Maybe you could post the output, so people can see what happens and help you (don't expect much from my side, I'm not an expert).

---

### Post by bertvkb on 2006-11-03
1) I have taken nr synch05 as in the spec on eciadsl
2) I have indeed downloaded the hoary packages, but actually I don't realy know which version of Ubuntu I have :confused:. I just ordered a ubuntu cd about 6 months ago. In which way could I find out the version of my installation?
6) Belgian too ;) 
7) Understood and tried it...

---

### Post by bertvkb on 2006-11-03
Ok, already found on the ubuntuguide site how to know the version of ubuntu I installed..

thanks anyway ;)

---

