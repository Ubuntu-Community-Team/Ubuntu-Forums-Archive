---
title: "Help! Need my Kubuntu 7.04 to talk wireless!"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by JoJerome on 2007-10-18
I'm a bit of a techie but fairly new Linux user here, converting a friend's Dell Inspiron 6000 notebook to Kubuntu 7.04. All is beautiful except that it sees the Intell 2200 series WiFi card but won't connect with it. I see from many hours of Googling that this is common.

Said hours of Googling also produces the same fix; rip the .inf and .sys files from the WinXP drivers using ndiswrapper. 

Problem is getting to said .inf and .sys files. I have no driver CD. Dell's website only allows me to download the drivers in .exe form. As the warranty has expired on this notebook, I am a non-person in the eyes of Dell Tech non-support. Intel's site has a Linux download but it's .tgz files and I'm not seeing what to do with them. 

Can anyone help?

Thanks in advance ...

- Jo

---

### Post by Original Brownster on 2007-10-18
Hi,

to extract the files if they are a tar gzip archive, from a console window type:
tar xvfz foo.tgz 

I had a quick look for you and found [this article]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/") that explains how to extract the files from a windows exe file. Sounds like a lot of the time, the exe is just an archive and can be unzipped, read the article and give it a go.

Good luck, post back if you need anymore help

---

### Post by JoJerome on 2007-10-19
Thanks for the reply!

The article you linked to is actually the one I keep going back to. I also found one in another thread here - [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

My head keeps banging against the same wall however; getting to those .inf and .sys files. I've downloaded the .exe version of the drivers from Dell, but it's truly a .exe file and I'm not having any luck getting it open to get the subfolders I need. 

The folder I downloaded from IBM contains a few .txt instruction files and 2 .tgz files. Your tip for opening these produced the error message: Cannot open: no such file or directory.

Using IBM's instructions, it appears to simply re-open the downloaded folder I'm already in.

Annoying as hell that Dell or IBM can't provide a simple zip file instead of a .exe!

Any suggestions for getting the golden .inf and .sys files?

Thanks again...

---

### Post by Original Brownster on 2007-10-19
Hi,
post me the link to the website with the .tgz file so I can have a look meanwhile I had a look and found the intel site supply the drivers too.

[This link]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&ProductID=1637&DwnldID=13000&strOSs=45&OSFullName=Windows*%20XP%20Home%20Edition&lang=eng") is for windows xp drivers including -Intel® PRO/Wireless 2200BG Network drivers.

Is this the model you have as this is a zip file? anyway have a poke around on there.

There is also native driver support for that chipset a page [here]("http://www.thinkwiki.org/wiki/Ipw2200") describes installing and using the native driver rather than ndiswrapper. Sounds like you have a choice you lucky guy! :)

---

### Post by JoJerome on 2007-10-19
Progress!

That first link you gave me provides .inf and .sys files. Hopefully those are the ones I'm looking for.

Of course, gotta go to work right away, but I'm guessing the user won't have a problem with me holding on to his laptop for another day or two to play with this.

Thanks again so much for your help. I'll post again if I run into any more issues.

- Jo

---

### Post by JoJerome on 2007-10-19
New snag.

I've been diligently following the instructions in
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
which by the way has been way helpful so far in ease of use and anticipating issues. Until...

My wireless device has been named eth1. This, in the instructions, is an anticipated issue. But when I run the recommended command:

gksu gedit /etc/iftab

I get an error message

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Any suggestions on proceeding? 

Continued loads of thanks to all here who are saving my semi-techie backside ("I'll install Linux on your laptop" she said. "It'll be a snap and I'm sure your wireless card will work fine" she said).

- Jo

---

### Post by Original Brownster on 2007-10-20
> **JoJerome said:**
> New snag.

I've been diligently following the instructions in
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
which by the way has been way helpful so far in ease of use and anticipating issues. Until...

My wireless device has been named eth1. This, in the instructions, is an anticipated issue. But when I run the recommended command:

gksu gedit /etc/iftab

I get an error message

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Any suggestions on proceeding? 

Continued loads of thanks to all here who are saving my semi-techie backside ("I'll install Linux on your laptop" she said. "It'll be a snap and I'm sure your wireless card will work fine" she said).

- Jo

Hi,
can you list the file contents? 
less /etc/iftab

I haven't looked at this file before but mine says (Im running gutsy 7.10 so this may be different in 7.04)

```
# This file is no longer used and has been automatically replaced.
# See /etc/udev/rules.d/70-persistent-net.rules for more information.
#

# This file assigns persistent names to network interfaces.  See iftab(5).
```

I can edit mine using gksu gedit ... so perhaps it's corrupt?

looking at the contents it's simple to replace but if you have a udev rule as above I expect you will find the entries in there, mine are for eth0 / eth1 (not wireless on this pc yet but will be v.soon I have the adapter sitting next to me but I can't be asked..)

---

### Post by JoJerome on 2007-10-20
Taking a new route now. I just installed the brand spanking new 7.10 version of Kubuntu. Though apparently one still needs to go through the driver installation process manually.

Here's hoping it's a little more stable now, say, something I can do on my lunch break today!

- Jo

---

### Post by omarg on 2007-10-20
im with ya bro. when u fix the problem i will need ya help.  i have the same issue. i just wan to know if someone resolved this issue already, i have killed many days trying to get the wireless up.

---

### Post by wieman01 on 2007-10-20
Hang on, guys... I own a laptop with IPW2200 BG and it has been working out of the box since Dapper (at least). I don't think you need to use "ndiswrapper" at all!

Please do me a favor and post the results of (command line, terminal):
> sudo iwlist scan
> sudo ifdown -v eth1
> sudo ifup -v eth1
Honestly I have not had any troubles with IPW2200 so far. Is the radio turned on?

---

### Post by JoJerome on 2007-10-21
```

~$ less /etc/iftab
/etc/iftab: No such file or directory

```

This after multiple attempts to run...

```

gksu gedit /etc/iftab

```

The above command produces a pop-up window asking for the password, I enter it and nothing at all appears to happen. I enter the recommended gedit syntax, but based on the "nothing at all happening" bit, I suspect my syntax is disappearing into the ether.

It's somewhat comforting however to learn I'm not the only one having this issue. :)

---

### Post by wieman01 on 2007-10-21
> **JoJerome said:**
> ```

~$ less /etc/iftab
/etc/iftab: No such file or directory

```

This after multiple attempts to run...

```

gksu gedit /etc/iftab

```

The above command produces a pop-up window asking for the password, I enter it and nothing at all appears to happen. I enter the recommended gedit syntax, but based on the "nothing at all happening" bit, I suspect my syntax is disappearing into the ether.

It's somewhat comforting however to learn I'm not the only one having this issue. :)
Either try...
> sudo gedit /etc/iftab
Or...
> sudo nano /etc/iftab

---

### Post by JoJerome on 2007-10-21
```

~$ sudo gedit /etc/iftab
sudo: gedit: command not found

```

```

~$ sudo nano /etc/iftab
 [ New File ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

Also, upon running that last code I'm not given any command prompt. I have to close Konsole and start over.

---

### Post by wieman01 on 2007-10-21
Ah... my fault. You are running Kubuntu. So it will be:
> kdesu kate /etc/iftab

---

### Post by JoJerome on 2007-10-21
Is it possible that the wifi will work fine with a name of eth1 versus wlan0? 

I've been assuming not because this is the same point in the directions I got stuck in 7,04 and it didn't work when I took it to the hotspot. But now that I'm on 7.10 maybe something's different. We'll know in a few hours when I run to Java Joint on my lunch break, eh?

If not, I'll definitely try your Kate edit suggestion next. 

Again, thanks for the continuing help to all! Now if I can just get this laptop to take less than 3 minutes to boot up. Fishing for help on that in thread... [http://ubuntuforums.org/showthread.php?p=3586800&posted=1#post3586800](http://ubuntuforums.org/showthread.php?p=3586800&posted=1#post3586800))

:KS

- Jo

---

### Post by JoJerome on 2007-10-21
Thank you - was able to edit /etc/iftab in kate. But my problem remains...

```

~$ less /etc/iftab
# This file assigns persistent names to network interfaces.
#See iftab(5) for syntax.

#eth1 mac 00:12:f0:97:ce:e8 arp 1
wlan0 mac 00:12:f0:97:ce:e8 arp 1

```

However, even upon reboot, lshw -C network shows me the same info as before. The wireless device is still named eth1. I made absolutely sure I got the mac address right. 

Ran to a wifi hotspot and still no connection.

:(

- Jo

---

### Post by JoJerome on 2007-10-22
Ok, since I'm dead in the water here I've found an alternate set of directions on getting my wifi working...
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide)

Reason I didn't go that route in the first place is that the first thing it asks me to do is look up the PCI ID in device manager.

1) Been looking for weeks and can't find anything called "device manager" or as someone told me it might be called, "hardware manager."

2) Is there a way to find the PCI ID in a shell command?

Again, this is now Kubuntu 7.10. Thanks!

- Jo

---

### Post by Original Brownster on 2007-10-22
> **JoJerome said:**
> 
2) Is there a way to find the PCI ID in a shell command?

Again, this is now Kubuntu 7.10. Thanks!

- Jo

Hi,

yes in a shell type

$ lspci -nvv

scroll through and you should find your card in there somewhere and the 2 x four digit hex code you're after.

ps. I've just joined the party and am currently trying to get my wireless pci card configured, of course it's not working yet, but I'm hopeful, lol. :)

---

### Post by JoJerome on 2007-10-23
Ok, 
~$ lspci -nn
gave me the PCI ID I was looking for. I did what I could with the new directions but it doesn't seem like anything has changed. I'll try the hotspot again tomorrow. In the meantime...

1) It's been suggested that some hotspots 'ban' Linux or are somehow configured such that Linux won't work. Is this true and could it be my whole problem?

2) Is there any command(s) or check(s) to see if my wifi is indeed up and looking for a hotspot, thus confirming the problem is now the hotspot and not this lappy? It sure looks to this n00b's eyes like everything is installed, other than it's called eth1 instead of wlan0 and I've yet to get a wifi signal at a hotspot.

3) Should I be configuring something in Network Settings? While hooked to the wired eth0 port I'm using now, eth1 shows as an enabled wireless device and gives me an ip address.

4) I now believe that "device manager" and/or "hardware manager" are linux myths. There is no such place and their mention in various directions is purely to mess with my mind.

5) Count me in for the Halloween/make-my-wifi-work party.

:KS

- Jo

---

### Post by wieman01 on 2007-10-23
> 1) It's been suggested that some hotspots 'ban' Linux or are somehow configured such that Linux won't work. Is this true and could it be my whole problem?
No, certainly not. I could not think of any way they could achieve that... wireless is based on open standards, how could they ban Linux users?

They could ban certain browsers for sure, but I don't think anybody would do that.

---

### Post by JoJerome on 2007-10-23
Well, maybe not actively 'ban,' but it was suggested that thier wifi wouldn't connect to linux, perhaps inadvertantly. But yeah, I'm not sure how one would achieve that kind of firewall.

Another potential issue I just found...
```

~$ ndiswrapper -l
w29n51 : driver installed
        device (8086:4220) present (alternate driver: ipw2200)

```

That first device, 8086:4220, is the correct PCI ID. According to the ndiswrapper website, when there's an alternate driver shown, linux might be trying to use it instead of the first, correct one. Question then is how to get rid of that alternate driver without unistalling and reinstalling ndiswrapper altogether?

Hope I'm not a pain here - I'm really and truly playing around with it as much as I can think of before replying again and again!

- Jo

---

### Post by JoJerome on 2007-10-23
Oops, I meant the first *driver* w29n51 is correct.

---

### Post by wieman01 on 2007-10-23
> **JoJerome said:**
> Oops, I meant the first *driver* w29n51 is correct.
Try to use a IPW2200? Oh man... You could blacklist the module (ipw2200) perhaps.

---

### Post by Original Brownster on 2007-10-23
Yeh blacklist it in /etc/modprobe.d/blacklist

you can remove it without re-boot with

$ sudo rmmod foo

incidently I have ndiswrapper installed with a driver rt2500, and I have blacklisted rt2500pci, ndiswrapper -l still shows the alternate.

to see what modules are loaded and in use 

$lsmod

will show if the offending module is indeed loaded and in use :)

ps. I have finally got my wireless up and running with wpa encryption, <sigh of relief> for me there was noway the installed rt2500pci driver would work, so I got ndiswrapper and tried that, this sort of worked but the driver did not have the same 'interface' so when you looked with iwpriv, I could not use the 'set' command. Got the CVS version of the rt2500 driver from serialmonkey in the end, please because this is the open source one. Had to compile as a module, which didn't work initially (for some strange reason the stable v1.0 release would not compile but the cvs would, go figure) and at last I'm wireless :)

---

### Post by JoJerome on 2007-10-23
Stop the presses - I might have something here!

The laptop's wifi idiot light, which has shown no signs of life since obliterating Window$, is suddenly shining at me like a little green beacon of hope! Please God/dess/s, tell me this means it's looking for an access point, eager to talk to the 'net!

Sadly, I'll have to wait until tomorrow morning to get to a hotspot and answer that burning question. 

Once again I ask, is there any way to tell by looking at Network Settings, shell commands, or anywhere else under Kubuntu's skirt if I'm truly wireless ready now? The user has given me until tomorrow to prove my love of Linux right or re-install Window$ for him.

What I've done - and please feel free to tell me if I'm crazy - since all attempts at renaming the device from eth1 to wlan0 (as all instructions seem to feel it needs to be named) failed, I thought I'd come from the other direction and change what name ndiswrapper is looking for:

```

~$ kdesu kate /etc/modprobe.d/ndiswrapper

alias **eth1** ndiswrapper

```

I also uninstalled and reinstalled ndiswrapper, using the specific name of the driver I'm needing to use rather than generically having it search all 5 .inf files I was given.

Between those 2 things, I seem to have made some kind of progress.

So again I ask, any other way to check that besides "Go to Starbucks and cross your fingers?"

Thanks a million more...

- Jo

---

### Post by Original Brownster on 2007-10-24
> **JoJerome said:**
> Stop the presses - I might have something here!

The laptop's wifi idiot light, which has shown no signs of life since obliterating Window$, is suddenly shining at me like a little green beacon of hope! Please God/dess/s, tell me this means it's looking for an access point, eager to talk to the 'net!


Hi and it does look promising :)
> 
Once again I ask, is there any way to tell by looking at Network Settings, shell commands, or anywhere else under Kubuntu's skirt if I'm truly wireless ready now? The user has given me until tomorrow to prove my love of Linux right or re-install Window$ for him.

What I've done - and please feel free to tell me if I'm crazy - since all attempts at renaming the device from eth1 to wlan0 (as all instructions seem to feel it needs to be named) failed, I thought I'd come from the other direction and change what name ndiswrapper is looking for:

```

~$ kdesu kate /etc/modprobe.d/ndiswrapper

alias **eth1** ndiswrapper

```

You can't re-install windblows, that would be a disaster, no I hope you can get this going and convince your friend.
I am not sure about the aliasing you have done, but if it works fair enough. otherwise I would go with leaving as wlan0
To clarify the issue about the naming of the wireless device I think it depends on your computer,
my device is wlan0 on a pc with an ethernet network card so I see both devices listed.
others have ra0 etc.
However on my old laptop running gentoo that does not have an ethernet card just a wireless pcmcia card, I see eth0 and wifi0 both with wireless extensions that seem to be one and the same!

To the point, the most important thing is does your computer see a wireless device, if you type
$iwconfig
do you see a wireless entry, wlan0 or other (ra0 for example) or with your aliasing you may see wireless extensions on eth0 now?

if you do (see a wireless entry) this is good because it means a driver is loaded by the kernel for you device (hopefully one that works...)
I'll assume from what you have said that you do so all things being equal it's just a matter of configuring it (famous last words)

I am using wpapsk here and have configured my setting manually in the /etc/network/interfaces file, however, the easiest route possibly for you since you are going to use a hotspot, is one of the tools like 'wireless assistant'. I say try this because it should show you the wireless networks in the area and you should be able to just click and connect.
If this doesn't work post back with what info you have about the hotspot, I have never used one, do they use encryption for example or do they just tell you the essid of the network and that's it?

Can you see the access point in the hotspot, well I think if you are in range,
try:
$sudo iwlist scan
this will return the id of all the cells in range including the one you want along with the address, now type
$iwconfig
if you have a card configured you should see something like:

```
wlan0     RT2500 Wireless  ESSID:"hotspot"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:01:d3:02:17:00   
          Bit Rate=11 Mb/s   Tx-Power:-6 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=83/100  Signal level:-12 dBm  Noise level:-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

if you are connected you'd see the access point address listed as in the snippet matching the one found using 'iwlist scan' 

hope this helps

---

### Post by JoJerome on 2007-10-24
Hi again Wayne!

I agree; no matter how much trouble this is, it's less headache than M$. Still working on convincing the user, but if I get this working and he starts playing in Linux, I think he'll like it. His main concern is security (done) and viruses (one in a million shot). 

Before heading to the hotspot...

```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s
          RTS thr=1600 B   Fragment thr=2304 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

eth0 is the wired connection, which has always worked beautifully.
eth1 is the wireless connection which resists all attempts to rename it. Hence, my possibly crazy idea to instead tell ndiswrapper, "Fine. Stop looking for wlan0. Look for eth1." After all, what's in a name?:)

```

~$ sudo iwlist scan
[sudo] password for dave:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


```

Again, I'm not at the hotspot yet - wanted to do all I possibly could before leaving my working connection here. But to this newbie's eyes, it sure looks like eth1/wifi is doing its part to search for a signal.

We who are about to die salute you...

- Jo

---

### Post by Original Brownster on 2007-10-24
Hi,
Looks good so far, have you thought about how you will configure the connection when you get there? 
The software I suggested 'wireless assistant' might work for you or maybe get something else installed and running?

Good luck & fingers crossed ;)

---

### Post by JoJerome on 2007-10-24
This laptop is so, so, NOT respecting my authoritah.

I get to the wifi hotspot and as soon as the wifi light comes on the boot process freezes completely.

I get away from the hotspot, the wifi light comes on and stays on as all boots normally.

So apparently the card is up and running, but for whatever reason as soon as it connects with an access point it freezes. I didn't have time to try booting away from the hotspot, then physically bring it into range to see what happens. 

Can't imagine what could be the conflict here. Since coming back to work, I have taken the syntax out of etc/iftab that was to (but failed to) change the name from eth1 to wlan0. 

If the user lets me keep it a while longer, I'm determined to make this wifi work if it kills me!

- Jo

---

### Post by Original Brownster on 2007-10-25
What a monkey, how long did you wait whilst it froze? All I can think is could it be your card is using dhclient to acquire an address at boot causing the freeze - if the card is not fully configured yet this might appear as a freeze (clutching at straws) hopefully this and something more difficult. 

You could try disabling the card at boot time (in etc/network/interfaces comment out the auto line) then once the laptop is up start the network with
$ sudo /etc/init.d/network start

if still a problem look at the output of /var/log/syslog (in another term try $ tail -f /var/log/syslog  this will follow the live output)

Have you done any config. of the network side yet? what do you have in /etc/network/interfaces ?

---

### Post by JoJerome on 2007-10-29
Began a vacation, so I'm just now able to restart work on this laptop...

I've waited upwards of 20 minutes while the progress bar on the Kubuntu splash screen sits about 1/4 of the way through booting. 

When I took it home that night and tried working on it away from the hotspot it began freezing and finally not booting even away from wifi access. Many attempts since, with or without wifi nearby, and I'm unable to boot at all.  

Since this was all a fresh, new install, I'm now re-installing 7.10 and going back through the motions of setting up the wireless card now that I have a better idea how to do that. And now that I have most of the next 2 days to work on this right next to a wireless AP. 

Again, it's a Dell Inspiron 6000 with an Intel 2200bg wireless card. 

Once again, we who are about to die salute you!

- Jo

---

### Post by JoJerome on 2007-10-29
[QUOTE=wieman01;3586805]Hang on, guys... I own a laptop with IPW2200 BG and it has been working out of the box since Dapper (at least). I don't think you need to use "ndiswrapper" at all!

Please do me a favor and post the results of (command line, terminal):
```

~$ sudo iwlist scan
lo               Interface doesn't support scanning.

eth0          Interface doesn't support scanning.

eth1          Scan completed :
                 Cell 01 - Address: 00:0F:66:DA:D6:43
                                ESSID: "linksys"
                                Protocol:IEEE 802.11b
                                Mode:Master
                                Channel:6
                                Frequency:2.437 GHz (Channel 6)
                                Encryption key:Off
                                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                                Quality=64/100   Signal level=-23 dBm
                                Extra: Last beacon: 172ms ago
                 Cell 02 - Address: 00:18:3F:C4:35:39
                                ESSID: "2WIRE977"
                                Protocol:IEEE 802.11b
                                Mode:Master
                                Channel:6
                                Frequency:2.437 GHz (Channel 6)
                                Encryption key:on
                                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
		    		9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
				48 Mb/s; 54 Mb/s
                                Quality=33/100   Signal level=-80 dBm
                                Extra: Last beacon: 160ms ago
	        Cell 03 -  Address: 00:0F:66:D7:7F:78
                                ESSID: "Predator&#8221;
                                Protocol:IEEE 802.11b
                                Mode:Master
                                Channel:7
                                Frequency:2.442 GHz (Channel 7)
                                Encryption key:on
                                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 6 Mb/s
		    		11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
				48 Mb/s; 54 Mb/s
                                Quality=33/100   Signal level=-80 dBm
                                Extra: Last beacon: 160ms ago
 	        Cell 04 -  Address: 00:14:6C:A2:68:64
                                ESSID: "woong&#8221;
                                Protocol:IEEE 802.11b
                                Mode:Master
                                Channel:11
                                Frequency:2.462 GHz (Channel 11)
                                Encryption key:on
                                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 6 Mb/s
		    		11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
				48 Mb/s; 54 Mb/s
                                Quality=64/100   Signal level=-62 dBm
                                Extra: Last beacon: 56ms ago
                               

```

```

~$ sudo ifdown &#8211;v eth1
ifdown: interface eth1 not configured


```

```

~$ sudo ifup &#8211;v eth1
Ignoring unknown interface eth1=eth1


```

Again, this is a fresh install of 7.10, no extra drivers, ndiswrapper, etc installed.

- I'm working on this at a friend's house with a wireless router. As far as they know, anyone with wifi on a laptop has been able to come over and connect upon bootup.

- Do these outputs mean the wifi card is running but just not configured?

- I'm not getting the 'wifi' idiot light on the laptop.

Thanks for any advice on this.

- Jo

---

### Post by Original Brownster on 2007-10-29
Hi there,
From the output of iwlist, it shows that eth1 is indeed working with wireless extensions so a driver is loaded correctly and running, good news.
Also your laptop can 'see' 4 networks or cells. notice the first with essid 'linksys' has encryption off,  very risky.

You need to establish:
which of these cells is your one in your friends house
what type of encryption has been set up (normally wpa-psk or wep)
what the passphrase or key is. 
Is the router you are trying to connect to a dhcp server so you get an ip automagically or will you need to be assigned and configure a static ip.

armed with the above information you should be able to move this baby forward :)
If you want to try a gui tool to do the configuration install something like Wireless assistant. otherwise its manually editing /etc/network/interfaces
depending on your wireless card / driver you may be able to use just this file to configure your card. here's mine as an example but remember your card will most likely require different commands:

```

auto wlan0
iface wlan0 inet dhcp 
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "crazybadger"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="somelongwindedkeyienteredhere"
pre-up ifconfig wlan0 up

```

hopefully wieman01 is reading this and can chime in with his config. and or what gui tool he uses.

---

### Post by JoJerome on 2007-10-29
[I]You need to establish:
which of these cells is your one in your friends house[/I]

The one entitled "linksys" is the router where I am. As it's a nice neighborhood, I gather most everyone around here has a wireless router which is why I'm seeing so many? 

*what type of encryption has been set up (normally wpa-psk or wep)*

According to the scan, none. Wouldn't that be the case at a wifi hotspot? Isn't that how one can just go to the local Java Joint and connect without manipulating any controls?

*Is the router you are trying to connect to a dhcp server so you get an ip automagically or will you need to be assigned and configure a static ip.*

This I'm not sure of and my friends won't be home for a few more hours for me to ask. Not sure how/where to find that in Windoze XP. I expected to find an installed program for the router, but no such animal that I can see.

But again, others bring their Windoze laptops over and are immediately connected without having to enter anything. Shouldn't Kubuntu be able to set up to do the same?

As for Wireless Assistant, sounds great but it's not installed, not in the add/remove programs or in the current repositories. Will have to connect to the net first so I can go out into the ether and get such wonderful applications!

Is there any other way to find out if the router I'm connecting to is dhcp before I start manipulating files?

- Jo

---

### Post by JoJerome on 2007-10-29
**VICTORY!!!** ... I think!

Original Brownster, I'd bear-hug you if we were in the same hemisphere!

Not having much of any of the stats and settings you asked about, I thought I'd at least mimic your /etc/network/interfaces settings to some extent. 

```

~$ kdesu kate /etc/network/interfaces

auto eth1
iface eth1 inet dhcp 
pre-up ifconfig eth1 up


```

Rebooted and miracle of miracles, the laptop is connecting wirelessly! Remaining questions now are:

- In doing this, have I disabled the ability to connect via ethernet cable in the future?

- As it appears to now be looking for a dhcp connection, does this mean I *should* be able to connect automatically at any hotspot?

Again Brownster - you're my hero! :KS

- Jo

---

### Post by Original Brownster on 2007-10-30
> **JoJerome said:**
> **VICTORY!!!** ... I think!

Original Brownster, I'd bear-hug you if we were in the same hemisphere!

Not having much of any of the stats and settings you asked about, I thought I'd at least mimic your /etc/network/interfaces settings to some extent. 

```

~$ kdesu kate /etc/network/interfaces

auto eth1
iface eth1 inet dhcp 
pre-up ifconfig eth1 up


```

Rebooted and miracle of miracles, the laptop is connecting wirelessly! Remaining questions now are:

- In doing this, have I disabled the ability to connect via ethernet cable in the future?

- As it appears to now be looking for a dhcp connection, does this mean I *should* be able to connect automatically at any hotspot?

Again Brownster - you're my hero! :KS

- Jo

lol I'm pleased for you :)

Well there are a few things we can deduce from what has happened:

yes you are using dhcp

Since you did not enter any encryption key, you are obviously not using any encryption so most likely you are connected to the linksys router. you can check by running 
$sudo iwconfig eth1
will show you the hw address of the access point you are connected to, compare this address to the list you get by entering
$sudo iwlist scan

You wouldn't want to do anything which reveals personal info using this link as anybody, including someone sitting outside your house could connect to this network and snoop the traffic, capture email passwords (often sent as plain text) for example. fine for surfing I guess. 
I haven't used a hotspot before but you will most likely find that they use the same settings ie, dhcp and no encryption, they will probably just tell you the name of the network essid.
A tool like wireless assistant (in the universe repositories as 'wlassistant' and its a kde app) will be cool as you just open it up and see a list of networks and signal strengths, you can just click on the one you want and a wizard takes you through allowing you to enter settings if required.

You also have eth0 for a wired connection on your laptop from memory which you will still be able to use but you have to switch between the two. the reason being only one can be the default route / gateway to the big bad world. I'm not sure on the best way of switching between them, probably see how you get on with the network connection (assistant?) tool that's installed by default (I've removed it as it edits the /etc/network/interfaces file and I end up fighting with it :) ) 

Hope this helps ;-)

---

### Post by JoJerome on 2007-10-30
Thanks a million more Original Brownster!

On your recommendation I've installed Wireless Assistant.

On security, I'm wondering what if any steps this user should take since he will primarily use this laptop at wifi hotspots. His number one concern here is security - I ultimately talked him into Linux on the point that viruses become a ridiculously minimal threat. 

But as I understand it, that's the nature of hotspots. You have to have your network's back flapping open in the wind as it were so anyone and their brother can jump on without a key.

Thanks once again to all for a wireless issue well-solved!

- Jo

---

### Post by Original Brownster on 2007-10-30
> **JoJerome said:**
> Thanks a million more Original Brownster!

On your recommendation I've installed Wireless Assistant.

On security, I'm wondering what if any steps this user should take since he will primarily use this laptop at wifi hotspots. His number one concern here is security - I ultimately talked him into Linux on the point that viruses become a ridiculously minimal threat. 

But as I understand it, that's the nature of hotspots. You have to have your network's back flapping open in the wind as it were so anyone and their brother can jump on without a key.

Thanks once again to all for a wireless issue well-solved!

- Jo

Hey your welcome, glad to help :D

My advice is:
Avoid carrying out any transactions that involve money or private data whilst using an open network you just don't know who is listening in and what tools they may be using.

Depending on where he get's his email he might want to look at ensuring he uses a secure login,  yahoo has the option and gmail for example, even if your friend is using a provider that has to use plain text login (many pop3 servers are like this but not all) he can always pick up the mail via yahoo, I'm not absolutely sure but I think this would protect his password since the request (and plain text password) would be sent from the yahoo server and not his laptop hence keeping it a secret.
He'll be a lot more secure now anyway since he is not using ie / outlook / m$ just by virtue of the fact that nearly all the threats are written for these, let alone the more secure nature of linux.

You are one ahead of me on converting someone to Linux now, I'll have to try and get someone to switch :)

---

### Post by wieman01 on 2007-10-30
> **Original Brownster said:**
> My advice is:
Avoid carrying out any transactions that involve money or private data whilst using an open network you just don't know who is listening in and what tools they may be using.
Actually to be precise... that's generally no problem at all, as most banking sites, etc. use HTTPS which is secure. So there is not much to worry about. :-)

Just thought I'd point that out. Great job, guys!

---

