---
title: "Wireless Problem"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by FuMangChu on 2007-06-18
Hi guys I am extremely new to Ubuntu and need a bit of hand holding so bare with me. I have a IEEE 802.11g Turbo Mode Wireless LAN PCI adapter made by Edimax. When I use it in windows it works fine. When I use it in Fiesty it recognizes the networks, but the one I use has an empty bar beside it. I am assuming that means no signal. However right now I am on a laptop right next to the desktop I am trying to troubleshoot, and using windows and I am on that network. 

I was told by another user in the beginner forum to post this:"sudo lshw -C network although I have no idea where he got it from. I have been using fiesty for all of 10 min now so i am really in the dark. THank you for your help.

---

### Post by charleseddy on 2007-06-18
When you're given a command like that, enter it into the terminal, which is found in the applications menu.  Try it and let me know.

---

### Post by FuMangChu on 2007-06-18
I got pages of output. What would you like to know?

Also for a brief second the bar next to the router I use was half full. However everynow and again with linux when I click on ANYTHING it thinks for a minute (does the little spinny thing) and then does nothing. So I reset the computer, and now I can do stuff but the signal bar is empty again. The reception on this laptop is unchanging.

---

### Post by charleseddy on 2007-06-18
Save the output as a text file and attach it as a reply using the manage attachments function of the forum.

---

### Post by FuMangChu on 2007-06-18
Would love to, however...

1) I am on a different computer right now (laptop) and the computer with the problem (desktop) has no way of sending information over a network hence we are here.

2) I am currently not using a real mouse because linux gives my microsoft mouse the finger for some reason. Therefore I have to use the number pad to navigate my cursor and have no idea how to select text to copy and paste.

3) I have been using Ubuntu for all of 30 minutes now and the only way I would have a prayer of a chance of writing data would be to a cd. I do not have burning software.

If you know of other options please let me know.

Sorry for the noobiness.

FMC

---

### Post by charleseddy on 2007-06-18
Then the part starting with "description: Wireless interface" until the line reading "resources".

ce

---

### Post by tcrroadie on 2007-06-18
If you could possibly connect the desktop pc you are troubleshooting to your network with an ethernet cable, we can help troubleshoot your wireless problem much faster.  

We need to be able to see complete screen output that you recieve when you are asked to run a command string in a terminal such as the command "lshw".  lshw (List Hardware) will tell us what networking devices are installed in your computer and the chipsets that they contain.  

If you can connect your desktop pc to your network with a cable than you would easily be able to copy and past the screen output you recieve in your terminal to the forums here, so we can help you more easily.

---

### Post by FuMangChu on 2007-06-18
description: wireless interface
product: RT2561/RT61 802.11g PCI
vendor: Ralink
physical ID: 8
bus info: pci@01:08.0
logical name: ral
version: 00
serial: 00:0e:2e:8a:9c:3b
width: 32 bits
clock: 33Mhz
capabilities: bus_master cap_list ethernet physical wireless
configuration: boradcast=yes driver=RT61STA driverversion1.1.0 CVS latency=32 link=yes multicast=yes wireless=RT61 wireless
resources: iomemory:38000000-e8007fff irq:20

whew! hope it helps and thank you for your patience

---

### Post by FuMangChu on 2007-06-18
> **tcrroadie said:**
> If you could possibly connect the desktop pc you are troubleshooting to your network with an ethernet cable, we can help troubleshoot your wireless problem much faster.  

We need to be able to see complete screen output that you recieve when you are asked to run a command string in a terminal such as the command "lshw".  lshw (List Hardware) will tell us what networking devices are installed in your computer and the chipsets that they contain.  

If you can connect your desktop pc to your network with a cable than you would easily be able to copy and past the screen output you recieve in your terminal to the forums here, so we can help you more easily.

Will that require a crossover, or will any ethernet cable do? For that matter is there a difference? Hopefully I will get this wireless problem fixed soon and then we will not have to worry about it as I will be on these forums with the same computer I am having issues with. However if you forsee this being a long process that is definately and option I will look into.

I really do appreciate all the help guys. I have never had this kind of tech support from M$.  ;)

---

### Post by charleseddy on 2007-06-18
LOL glad to hear that.  Anyways, that would require an ethernet cable.  A crossover cable is PC to PC or switch to router (but only on the old routers).  A $5 cat-5 ethernet cable would do it.  It would help, though, if you *were* able to get it hooked up that way.

It'll take me some time to figure out what could be wrong there. . . .

---

### Post by handaxe on 2007-06-18
OK, after that sharp brief intro to the Linux CLI (Command Line Interface) :p

Firstly, you mentioned Feisty yet the driver indicated by "lshw" is rt61STA.  AFAIK, that is not the stock rt61 driver under Feisty but it was under Edgy (the previous Ubuntu version).  Weird! My Feisty has the rt61pci and rt61 (legacy) driver and not STA (in the dir  "/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/").

Search your computer (under "places" menu) for rt61 - selecting "File System"  under the "look in folder" option.

See if the rt61pci and plain rt61 are listed as well as the rt61STA.

If they are, try the following:

In the CLI, ```
sudo gedit /etc/modprobe.d/blacklist
```

At the bottom of the file enter rt61STA in the manner of other entries. (SAVE!!!!:D)

Reboot.

See if that makes a difference. Briefly, what you will have done, is prevented the suspect rt61STA driver from loading and given the other a chance to do so.

Test if it has at the CLI:
```
 sudo lsmod | grep rt61
``` (basically: list the loaded  modules containing phrase rt61)

If nothing returned (ie no rt61pci or such), then:

```
sudo modprobe rt61pci
```

If no errors, try wireless.  if errors try rt61 in place of rt61pci.

If all this fails, then (shudder!!), these two posts refer:

[http://ubuntuforums.org/showthread.php?t=477742](http://ubuntuforums.org/showthread.php?t=477742)

[http://ubuntuforums.org/showthread.php?t=419709](http://ubuntuforums.org/showthread.php?t=419709)

For a noob, a little daunting but a great way to learn the ropes.  However, you really need that ethernet cable linkup for the lappie so that you can try the various options.

HA

---

### Post by charleseddy on 2007-06-18
Good suggestions, handaxe.  Glad you have a similar wireless card.  I was stumping myself over what could be wrong, lol.

---

### Post by handaxe on 2007-06-18
Actually, I don't... I originally explained that but it read long winded so "DEL"..., I simply searched to see what names came up under rt61, and no rt61sta popped up. Elsewhere I read that rt61sta was part of Edgy and would not compile under Feisty.

Wireless under Feisty seems to present regressions in a number of instances - cards half working etc: can see AP no connect (groan!)

HA

---

### Post by tcrroadie on 2007-06-18
I noticed that know one else has asked, but have you checked your wireless security settings?  You may want to disable your wireless security temporarily for testing purposes, until you have your wireless card up and running.  WPA has been a little finnicky to set up on Feisty for some users.  

Once you get your ethernet cable connected, you can also run some other tools to check the status of the wireless card in your desktop computer by running some wireless command line tools such as "iwconfig" and "iwlist".

---

### Post by FuMangChu on 2007-06-19
When I search for the rt61 file there is nothing that says rt61STA.  Only rt61 and rt61pci...

TCR how do change the security settings. I am looking but not finding it.

---

### Post by handaxe on 2007-06-19
Ok, that means that presumably the rt61pci identifies itself as rt61STA. One of those threads that I posted indicates that there may be problems with the stock Feisty driver and you may have bumped into that.  If so, only solution is to follow the advice in those threads.

A search i the networking & wireless forum on rt61 will also bring up a load of threads which may offer more advice.

What tcrroadie refers to is disabling security on your router , if you own it. That way you proceed step-wise. Confirm the ability to connect in an open system first, and then set WEP encryption and then WPA. Cards can have problems with one and not the other.

This prolly is not a good advertisement of Linux for you .... stick with it if you can.

regards,

HA

---

### Post by FuMangChu on 2007-06-19
Downloading the driver will not help my cause correct? If the driver is going to present itself as an 'STA' then it will do so even if redownloaded right. Also on the second link you posted when I am in the terminal my computer does not recognize any kind of device identified by ra0. What should I do about that?

Also how do i find my WPAPSK and what does it mean?

---

### Post by tcrroadie on 2007-06-19
> **FuMangChu said:**
>  Also on the second link you posted when I am in the terminal my computer does not recognize any kind of device identified by ra0. What should I do about that?

Your wireless card may be defined as another device, such as eth1.  For example your wired network card is usually defined as eth0.  As in my case on my laptop, my wireless card is defined as eth1, which may be the case with your desktop computer.  

The command line tool iwconfig will list this information for you.  

You can also use the command line tool iwlist to receive information on available wireless networks in your area.  You can also use iwlist to help give you an idea if your card is even working at all with its current configuration. 

As an example use of iwlist, my screen output on my laptop looks like this when scanning for available networks.

In a terminal type 

```
sudo iwlist eth1 scanning
```

Assuming eth1 is your wireless card.

An example of what I receive with iwlist
```

eth1      Scan completed :
          Cell 01 - Address: 00:12:17:A9:E3:EC
                    ESSID:"Homer"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-25 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 24ms ago
```

The output above displays information about my wireless network, the name of my router (Homer) and the channel it is broadcasting/receiving on (channel 9).  It also shows that my wireless encryption is on. 

Have you been able to connect your desktop pc to network with a cable?  Once you do this, we can really move on solving your wireless issue.

---

### Post by FuMangChu on 2007-06-19
I have the cable connected but do not know where to go from there. I did not get any notifications that either computer recognized the connection to pop up.  I think I just really need someone to lead me along at this stage in the game as I am very new to not only Ubuntu but terminal work altogether.

I found my wireless to be assigned to ra1 but got lost when he started talking about WPAPSK. :(

---

### Post by handaxe on 2007-06-19
(Note that I was typing and did not see your reply above.... at first)

In order of your questions:

Downloading the driver may indeed help. The rt61sta issue may be a red herring now - simply, given that I do not have your card in my lappie, I was surprised to see that come up in "lshw" as I had read that the rt61sta driver was part of Ubuntu 6.10 and it was not in my Feisty directory. 

So, given where we are now, no issue - what is, is why you can see the Access Point (AP) yet have no signal strength under the stock Feisty driver.

The ra0 issue: if you look at that output you posted you will read "logical name: ral". This is a typo and ismeant to be ra1 , ie that is a ralink interface no 1. So where you read ra0 is the post assume ra1.  Give the process in the post a bash. (Now that I re-read, the first post is not all that helpful).

Also NB, is the mention in the second post that the driver WILL NOT work with Network Manager that comes with Feisty and puts that icon in your tray area.

HA

PS the WPAPSK is the pass phrase required to access a WPA encrypted Access Point. That info comes from your router or whoever administers it, if WPA is what it uses.  It could be WEP, another encryption standard.

---

### Post by handaxe on 2007-06-19
Wired connection:

Clip in and then go to "System" -> "Administration" -> "Network"

Your wired connection should show up.  Select it and the "properties".

Select the "enable this connection" box and Automatic under "Configuration".

"OK".

Your connection should now work.
```
 sudo ifconfig
``` should show an IP no. assigned.

HA

---

### Post by FuMangChu on 2007-06-19
so if the router is unsecured that WPAPSK is negligable correct? (It is not mine but right now I am just using it for the sake of simplicity.)

 Note that the one with the connections (laptop) is connected to the same router that I am trying to connect to with the one without the working connection. (desktop)

I cannot enable this connection as there is no where to check that. The only check box I have is 'enable roaming mode'...same thing?

i did ifconfig with that checked and unchecked and did not see an 'ip'. I did see what appears to be a mac address if that helps.

eth0              Link encap: Ethernet   HWaddr   00:50:8D:E5:14:75
                     UP BROADCAST MULITCAST   MTU:1500   METRIC:1
                     RX packets:0 errors:0 dropped:0 overruns:0  frame:0
                     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                     collisions: 0 txqueuelen:1000
                     RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
                     Interrupt:16 Base  address 0x6000

I have eth0, lo, and ra1 but eth0 seems to be the wired connection so that is the only one I displayed...

---

### Post by handaxe on 2007-06-19
Get that wired card working.

Post the outputs of:
```
sudo ifconfig
``` and ```
sudo iwconfig
``` and ```
sudo iwlist ra1 scan
```.

HA

---

### Post by handaxe on 2007-06-19
In case I am confusing things here (and I find this thread a little mixed up anyhow :) )

It is advisable to try wired and wireless separately, ie do not try to connect to both at the same time. If you try wireless, unclip the ethernet cable.

Those commands I posted are about trying to assess what your cards are seeing, both wired and wireless.

HA

---

### Post by FuMangChu on 2007-06-19
sudo ifconfig:

eth0
Link encap: Ethernet HWaddr 00:50:8D:E5:14:75
UP BROADCAST MULITCAST MTU:1500 METRIC:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16 Base address 0x6000

lo
Link encap: Local Loopback
inet addr:127.0.0.1   Mask:255.0.0.0
inet6 addr: ::1/128 Scope Host
UP LOOPBACK RUNNING   MTU:16436   Metric:1
RX packets:34 errors:0 dropped:0 overruns:0 frame:0
TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 txqueuelen:0
RX bytes:2260 (2.2 KiB)   TX bytes: 2260 (2.2 KiB)

ra1
Link encap: Ethernet   HWaddr   00:2E:8A:9C:3B
inet6 addr: fe80::20e:2eff:fe8a:9c3b/64  Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500   Metric:1
RX packets:78714 errors:0 dropped:0 overruns:0 frame:0
TX packets:31674 errors:12 dropped:12 overruns:0 carrier:0
collisions: 79 txqueuelen:1000
RX bytes:6807116 (6.4 KiB)   TX bytes: 19176 (18.7 KiB)

---

### Post by FuMangChu on 2007-06-19
sudo iwconfig:

lo
no wireless extensions

eth0
no wireless extensions

ra1
RT61 Wireless   ESSID:"linksys_OW_26669"   Nickname:" "
Mode: Managed   Frequency:2.442 GHz   Access Point: 00:14:BF:37:BD:D0
Bit Rate=12 Mb/s
RTS thr: off   Fragment thr: off
Encryption key: off
Link Quality=56/100   Signal level:-79 dBm   Noise level:-111 dBm
Rx invalid nwid: 0   Rx invalid crypt: 0   Rx invalid frag: 0
Tx excessive retries: 0   Invalid misc: 0   Missed beacon: 0

[B^Note this is not the router I have been trying to connect to^[/B]

---

### Post by FuMangChu on 2007-06-19
sudo iwlist ra1 scan
 Scan completed:
Cell 01 - Address:  00:14:BF:37:BD:D0
ESSID:"linksys_OW_26669"
Mode: Managed
Channel: 7
Encryption key: off
Quality 55/100   Signal level:-72 dBm   Noise level:-256 dBm

Cell 02 - Address 00:11:24:0D:79:DB
ESSID:"Apple Network 0d79db
Mode: Managed
Channel: 1
Encryption key: off
Quality 0/100   Signal Level:-80 dBm  Noise Level:-256 dBm

**The one I want**
Cell 03 - Address 00:18:F8:EE:76:D9
ESSID:"Linksys"
Mode: Managed
Channel: 6
Encryption Key: off
Quality:0/100   Signal Level:-80 dBm   Noise Level: -256 dBm

Cell 04 - Address: 00:14:C1:0B:D4:00
ESSID-"Mystic Bone"
Mode:Managed
Channel: 11
Encryption Key: on
Quality:0/100   Signal level:-72 dBm   Noise Level:-256 dBm

---

### Post by handaxe on 2007-06-19
Ironically, your wireless card seems in better shape than your wired!

A wired interface should be there under "Network". Clip in and try a reboot and see once more.

Wireless: (without ethernet attachment!):

Don't enable roaming in "Network" for the wireless connection. Under properties make sure that "enable this connection" is checked. Click on the "essid" drop-down. Do you see the AP you want and can you select it? If you can, then it should allow you to connect (assuming it is configured for automatic / DHCP) but may freeze /halt during activation.

If not successful, go to the CLI and enter each line in sequence :
```
sudo ifconfig ra1 down
sudo iwconfig ra1 essid "Linksys"
sudo iwconfig ra1 channel 6
sudo iwconfig ra1 key open
sudo iwconfig ra1 Mode managed
```Follow this ```
sudo ifup ra1
```If this is working then

```
sudo iwconfig 
``` should show linksys as the attached essid and the signal strength should be >0.

```
sudo ifconfig
``` should show an inet address associated with ra1.  If so, you should be good to go.

If no inet (or IP) address, try ```
sudo dhclient ra1
```

HA

---

### Post by tcrroadie on 2007-06-19
FuMangChu, 

I don't mean to break up the great job handaxe is doing at helping you out, but I was wondering If you were able to connect and use the network "linksys_OW_26669" that you listed, since the encryption on it appears to be turned off?  ***Just for testing purposes ***,to see if your card is working properly.  

Notice the signal strength readings listed from iwlist.
```

Cell 01 - Address: 00:14:BF:37:BD0
ESSID:"linksys_OW_26669"
Mode: Managed
Channel: 7
Encryption key: off
[COLOR="Red"]Quality 55/100[/COLOR] Signal level:-72 dBm Noise level:-256 dBm
[B]
The one I want[/B]
Cell 03 - Address 00:18:F8:EE:769
ESSID:"Linksys"
Mode: Managed
Channel: 6
Encryption Key: off
[COLOR="Red"]Quality:0/100[/COLOR] Signal Level:-80 dBm Noise Level: -256 dBm
```

I also suggest making sure that the network that you are trying to connect to "Linksys" is configured for both wireless B and G standards (802.11b & 802.11g).  There may be the possibility that the driver being used for your wireless card in your desktop pc may not be able to connect to wireless G only networks.

Hope this helps.  Hang in there, your doing a great job so far.  :)

---

### Post by handaxe on 2007-06-20
glad to have any help tcrroadie!

Good point about the AP, tho' s/he does not "own" it.

HA

---

### Post by FuMangChu on 2007-06-20
I am happy to report that I am posting this from my desktop computer. Just for a little side note hand axe the word "mode" in the command line is not capitalized. No worries though I got it working  . Thank you so much for your patience. However be warned this is the first of many trials to come.

Like this one. I rebooted and no more wireless. Do I need to save the changes I made? If so how would I do that?  Thanks again guys.

---

### Post by tcrroadie on 2007-06-21
To have your wireless network settings applied automatically at startup, you will need to edit a file and add your wireless network settings to it.  We will use a text editor called Gedit. 

Open a terminal and launch Gedit, listing the file to open. 

```
sudo gedit /etc/network/interfaces 
```

Page down to were your wireless device "ral" is listed.  Should be at the bottom of the file. 

Simply add the wireless network options need to this section.  Should look something like this.  Edit as needed. 

```
iface ra1 inet dhcp
wireless-essid Linksys
wireless-channel 6
wireless-key open
wireless-mode managed

auto ral
```

Make sure auto ral is listed at the bottom of your file or your wireless card will not come up automatically.  

For more information, you can read the manual for "interfaces" in a terminal by running 

```
man interfaces
```

Good to hear you have your wireless card working.  :)

---

### Post by FuMangChu on 2007-06-21
Well I had it working...

Instead of dhcp though I put in the Static IP address to get it working.
I just changed it from static IP address to dhcp and now it is working again. If one of you would tell me exactly what I did and why with all of that code I entered I would really appreciate it. Hopefully then I will be able to troubleshoot myself instead of always having to come back to these forums.

---

### Post by tcrroadie on 2007-06-21
Basically what you performed when following hadaxe's directions, was manually setting your wireless network settings.  To help you understand more of what some of the command line tools used do, I would suggest reading there man pages.  You can read them using a terminal.  The terminal command "man" will open the tools documentation, or manual. 

For example.  To view the manual for the wireless networking configuration tool "iwconfig", you would enter this in a terminal. 
```

man iwconfig
```

Simply use the up/down and Page Up and Page Down keys on your keyboard to move through the manual page.  To exit the manual, press the Q key on your keyboard. 

Now to break down a few of the steps you performed earlier for you to understand.  Recall that "ra1" is your wireless network device.

When you ran the terminal command 

```
sudo ifconfig ra1 down
```

That brought down your wireless network card. 

To set the network id (essid) to use you ran

```
sudo iwconfig ra1 essid "Linksys"
```

And to set your wireless cards broadcast/receive channel

```
sudo iwconfig ra1 channel 6
```

And to tell your wireless card that there is no encryption key used on the network, you ran

```
sudo iwconfig ra1 key open
```

And to set the networks mode 

```
sudo iwconfig ra1 Mode managed
```

Then you ran this code to bring up your wireless device "ra1" using the configuration settings you set previously.

```
sudo ifup ra1
```

If your wireless card did not automatically ask to renew it's dhcp lease to receive a new network address, you would run this command 
```

sudo dhclient ra1
```

All the commands that you enter to set your wireless cards network settings are what would have been run when using GUI tools such as wifi-radar.  

I would suggest installing wifi radar and giving that a try if you would like.  

```
sudo apt-get install wifi-radar
```

After wifi radar is installed, you can find it in your Gnome -> Applications -> Network menu.

Hope this helps answer you question.

---

### Post by FuMangChu on 2007-06-21
after i type in dhclient ra1 it does its thing for a while and then tells me no working leases in persistent database - sleeping...  I have a feeling that is not what i want it to say...

and my wireless is down again.

---

### Post by handaxe on 2007-06-21
Indeed, that message is not what you want to hear.

Please note that you card is not how mine for instance behaves and reports exist that your card or at least the driver is buggy- I write this so that you know your experience whilst not uncommon is not inevitable under linux.

Because of this, you may need to re-run that sequence everytime you want to connect or to connect to another AP in the same boot session. Tccroadie provided you with the means in editing /etc/network/interfaces. Given an probable bug in the card not switching essids until downed, I would modify the file to look as follows:

```
auto ra1
iface ra1 inet dhcp
pre-up ifconfig ra1 up
pre-up ifconfig ra1 down
pre-up ifconfig wireless-essid Linksys
pre-up ifconfig wireless-channel 6
pre-up ifconfig wireless-key open
pre-up ifconfig wireless-mode managed
pre-up ifconfig ra1 up
```
If this does not get the interface up, then try
```

sudo /etc/init.d/networking restart
``` at the CLI

Glad to hear you got somewhere and thanks tccroadie for stepping in - I was away all day fishing...

HA

---

### Post by FuMangChu on 2007-06-21
when i type in sudo /etc/init.d/ networking restart is says  ifup: couldn't read interfaces file "/etc/network/interfaces"

---

### Post by handaxe on 2007-06-21
FYI: sudo /etc/init.d/networking restart calls the ifup and ifdown routines, hence the source of the error message.

Check that the name and path are exactly "/etc/network/interfaces". You can that the message you report if the file name is wrong. If there was an error in the file, the same message appears but it should be coupled with another indicating the nature of the problem.

You need to solve the above problem before considering the below.

You could also try the following edit of my suggested text in /etc/network/interfaces

```
auto ra1
iface ra1 inet dhcp
pre-up ifconfig ra1 up
pre-up ifconfig ra1 down
pre-up ifconfig wireless-essid Linksys
pre-up ifconfig wireless-channel 6
pre-up ifconfig wireless-key open
pre-up ifconfig wireless-mode managed
```(note this omits the final pre-up - which is an instruction to complete the subsequent command before the interface is brought up)

Comments elsewhere in the forums suggests that ifconfig can be replaced by iwpriv with rt61 cards.  So another form of file content to try:

```
 auto ra1
 iface ra1 inet dhcp
 pre-up ifconfig ra1 up
 pre-up ifconfig ra1 down
 pre-up ifconfig wireless-essid Linksys
 pre-up iwpriv ra1 set wireless-channel=6
 pre-up iwpriv ra1 set wireless-key=open
 pre-up iwpriv ra1 set wireless-mode=managed
 
```HA

---

### Post by FuMangChu on 2007-06-22
FREAKIN A!!!

When I run the init.d line it does a whole bunch of stuff but the last line says failed to bring up ra1.

Throughout it also says error while getting interface flags: no such device

---

### Post by handaxe on 2007-06-22
Ok, what of the advice given above have you done?

also:

```
sudo ifconfig
``` at the CLI to confirm that the ra1 device still exists.

Does it still work if you do it the manual way that worked?

HA

---

### Post by FuMangChu on 2007-06-22
Honestly I have done it all at one point, but not sure of where the system stands now. Maybe we should start from square one now that we are sure it is achievable.

Now I cannot get the wireless to work for the life of me.

If you have the time do you have msn or aim so we could do this in real time. I am tired of fiddling with it, and once I get intenet acess on the same computer that I am having the problems on it will be much easier.

ra1 does still exist under ifconfig.

---

### Post by tcrroadie on 2007-06-22
Hi FuMangChu,

I know at times, things can get a little frustrating on Linux, but hang in there.  At this point I would suggest starting a new thread, with a title listing your wireless cards chipset.  Something like 

**Ralink RT61 Wireless configuration help needed.**

This way, you will grab the attention of other users who have the same wireless card, and they may be able to give you more detailed information on the configuration of your Ralink card.  

Also, did you figure out your problem with your /etc/network/interfaces file?  Did you edit this file?  To view the contents of a directory you can use the tool "ls" to list directory contents. 

```
kris@ibook:~$ ls /etc/network
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces
kris@ibook:~$ 
```

---

### Post by FuMangChu on 2007-06-24
Yeah I had accidently typed in "/etc/network/ interfaces"
Instead of........................."/etc/netowrk/interfaces"


...it did not like that.

---

