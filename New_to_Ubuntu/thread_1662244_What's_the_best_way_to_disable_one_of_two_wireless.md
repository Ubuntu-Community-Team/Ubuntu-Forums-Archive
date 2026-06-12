---
title: "What's the best way to disable one of two wireless adapters?"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by diablo75 on 2011-01-07
I have a small computer (Zotac Mag Mini All-in-One Giant) that has a built in wireless adapter that barely works (poor signal), so I'm using an external USB adapter instead.  I would like to disable the adapter inside the PC so that in the future the computer doesn't try to reconnect to the network using the "wrong" interface.

***Edit:***  This edit is for users who are looking for the solution to the same problem I described above.  I decided to summerize what I found out in this thread here so you wouldn't have to scroll through it.

There are two ways that I've discovered to disable a network interface (or place higher priority of one over another).  The best one I learned about ([in this post]("http://ubuntuforums.org/showpost.php?p=10432612&postcount=2")) is the following:

**"First, obtain the MAC code of the device you want to connect. Then right-click on the NM applet icon > Edit connection > Wireless tab > highlight your connnection > edit > Wireless tab > add the MAC address to the 'Device MAC address' field > click apply button. Then, when you start up, network manager will only use the wireless device with that MAC address."**

A quick way to find the MAC address of any interface is to open a terminal and type "ifconfig".  All interfaces will have their MACs listed in there somewhere.

The second (not as good) solution is to determine the kernel module being using by the unwanted interface and blacklist it.  I'm not going to detail this here; just scroll down to see what's involved with that.  The glaring flaw in this technique is the question:  What if both interfaces use the same modules?  Blacklisting wouldn't work in that scenario.

---

### Post by t4thfavor on 2011-01-07
Step 1: go on ebay and pay 4USD for a set of laptop antennas that will fit your internal card.
Step 2: Tape them to the inside of the zotac case.
Step 3: Use the internal card instead of the USB one.

This works with my net top which uses a laptop style mini PCI-E card with the really small antenna plugs.

Option 2:

If the internal card uses a fixed antenna, and cannot use an aftermarket one..

Find out what driver the internal card uses, and then add that module to the /etc/blacklist file.

This will only work if you have a USB card that has a different chipset than the internal because you are essentially stopping that driver from loading.

---

### Post by diablo75 on 2011-01-07
Uh, no, I'd rather just use this USB adapter; it works great and I don't need it for any other computer/laptop.

Isn't there some kind of setting somewhere that I can check off that will disable the unwanted wireless device?  Or a command I can put into a terminal window that will shut it off and keep it off so it doesn't come back upon restarting?

---

### Post by MartyBuntu on 2011-01-07
Poke around in the BIOS. You might be able to disable from there.

---

### Post by diablo75 on 2011-01-07
> **MartyBuntu said:**
> Poke around in the BIOS. You might be able to disable from there.

Did my best but there was no wireless feature listed in the BIOS (probably because it's on a PCI-E slot)...

---

### Post by wep940 on 2011-01-07
If it's in a PCI-E slot, it's not truely "built-in".  Just power down and remove the card.

---

### Post by diablo75 on 2011-01-07
I hate to be a troll about this, but....

IN WINDOWS all I would have to do is open Control Panel>Network (interfaces), then Right-Click on the unwanted interface and select Disable.

Is there no way to disable an interface in Linux?  Why should I have to bust the case of a brand new computer open (voiding the warranty) when I should be able to shut the interface off in software?

---

### Post by Schuby007 on 2011-01-19
I'm trying to figure out the same thing. LOL at your bit on Windows... it's soo true.

I'm finding out that you still have to pay for "good" software...

---

### Post by walt.smith1960 on 2011-01-19
I did just this. No, there's not a Linux equivalent of Control Panel that I know of, unfortunately.  As others have said, find out the name of the module your built-in WiFi adapter uses. In my case the chipset was an intel 3954ABG and the module name was wl3954.  Navigate to etc/modprobe.d and edit the file 'blacklist.conf'.  Add the line "blacklist name_of_the_module_you_want_to_block, save & reboot.

How to determine the name of of the module you want to blacklist?  I used dmesg.  You might want to post the output of the command```
lspci
```. Perhaps someone will recognize the device and know the module name.

---

### Post by cascade9 on 2011-01-19
> **diablo75 said:**
> I hate to be a troll about this, but....

IN WINDOWS all I would have to do is open Control Panel>Network (interfaces), then Right-Click on the unwanted interface and select Disable.

Is there no way to disable an interface in Linux? Why should I have to bust the case of a brand new computer open (voiding the warranty) when I should be able to shut the interface off in software?

A better question is 'why would a hardware manufacturer put a wireless card in that has poor singal strength? 

From what I know, opening the case doesnt void your warranty. At least here (.au) it doesnt, maybe for once we've got better consumer protection laws. :lolflag:

> **Schuby007 said:**
> I'm trying to figure out the same thing. LOL at your bit on Windows... it's soo true.

I'm finding out that you still have to pay for "good" software...

Blacklist the wireless adapter. Its not rocket science. 

Just because you already know how to do something in windows, and dont know how to do it with linux doesnt mean that linux is worse, or windows is better....

---

### Post by eriktheblu on 2011-01-19
Not on Ubuntu right now, but isn't there an option for this in the default panel network applet?

I would personally go with the BIOS. If it's only listed as a port, than just disable the port if you can't remove the card.

---

### Post by Schuby007 on 2011-01-19
> Blacklist the wireless adapter. Its not rocket science. 

Just because you already know how to do something in windows, and dont  know how to do it with linux doesnt mean that linux is worse, or windows  is better....

I'm using "good" in this context to refer to simplicity or ease of use. I don't think it's uncommon for people to install Ubuntu on older laptops that maybe only have a G card and then install an N card for improved speed and signal strength (that's what I did). And I don't want my old card eating up battery searching for SSIDs when I'm solely using the new card. As well, I shouldn't have to dig around on the internet or go through the console for such an obvious feature. Ubuntu prides itself as being "Linux for humans"... It's almost in it's 11th version and I can't simply go into "Network Connections" and there be a hardware tab. It's frustrating.

---

### Post by sbrandon on 2011-01-19
Schuby - what is the USB adapter you are using? Did it work right out of the box?

---

### Post by sbrandon on 2011-01-19
Schuby - what is the USB adapter you are using? Did it work right out of the box?

---

### Post by Schuby007 on 2011-01-19
It's a DWA-652 connected to the cardbus (PCMCIA).
EDIT: Yes, Ubuntu detected it automatically and it works perfectly. According to this forum: [HTML]http://www.backtrack-linux.org/forums/old-wireless/6587-d-link-dwa-652-a.html[/HTML] it's an Atheros AR5416 chipset which supports monitoring mode so I can use it to sniff wireless network traffic :D

I see I'm not the only one having trouble with Ubuntu forums duplicating posts :P

---

### Post by wep940 on 2011-01-19
Just EDIT you extra posts, delete the text, and put in "Duplicate", and then at least no one would have to read it 3 or 4 times.  They are aware of the problem - some of it comes from waiting so long for the server to respond when making a post, assuming something is amiss, and clicking "Submit Reply" again - many of us are guilty of that, myself included.

---

### Post by DOSIX on 2011-01-19
best way to disable the wireless is by blacklisting the module. you don't have to poke around in the bios or any of that stuff. lspci should tell you the name of the card, then you can use lsmod to find the name of the module. then just go to the blacklist file and type the names of the modules you want to keep the kernel from loading. in this way, the kernel will never load the modules, and thus ubuntu will never use the wrong interface.

if anything, post the output of

```
lspci
```

and

```
lsmod
``` 

and i'll be happy to help you out. i just finished going through a driver problem myself, so i ended up learning a bit about modules and just how the kernel works with them.

---

### Post by DOSIX on 2011-01-19
Open Accessories -> Terminal
Type in:
```
lsmod
```
'lsmod' lists all the installed modules that the kernel (the core of the operating system) is using.
Find the module that corresponds to the device you don't want to use. Once you have that, all you need to do is add it to the blacklist file. This will keep the kernel from loading the module, and ultimately disable the device.

```

sudo gedit /etc/modprobe.d/blacklist

```
sudo requires you to type in your password. Asterisks don't show, just type it in and press enter. 
Just copy and paste the name(s) of the module you need blacklisted all the way at the end of the file.

---

### Post by DOSIX on 2011-01-19
double post.

---

### Post by DOSIX on 2011-01-19
double post

---

### Post by DOSIX on 2011-01-19
Open Accessories -> Terminal
Type in:
```
lsmod
```
'lsmod' lists all the installed modules that the kernel (the core of the operating system) is using.
Find the module that corresponds to the device you don't want to use. Once you have that, all you need to do is add it to the blacklist file. This will keep the kernel from loading the module, and ultimately disable the device.

```

sudo gedit /etc/modprobe.d/blacklist

```
sudo requires you to type in your password. Asterisks don't show, just type it in and press enter. 
Just copy and paste the name(s) of the module you need blacklisted all the way at the end of the file.

---

### Post by oldsoundguy on 2011-01-19
google sez that you can remove the card by removing the mother board .. but that will void your warranty.

LOTS of complaints about the existing Wi-Fi, so see your problem is not unique.

---

### Post by oldsoundguy on 2011-01-19
sorry!

---

### Post by diablo75 on 2011-01-20
> **oldsoundguy said:**
> google sez that you can remove the card by removing the mother board .. but that will void your warranty.

LOTS of complaints about the existing Wi-Fi, so see your problem is not unique.

Huh, glad I didn't follow the suggestions of others and attempt to bust the case open to attempt to remove a card that... allegedly cannot be removed.

The computer I posted this thread about is not my own and I can't access it right now, so I can't do any module black listing right now.

From the amount of froth this thread has generated I can only assume that blacklisting the correct module is the "best" way to tackle this problem at the present time.  Although I can't help but remark that this "solution" is not intuitive and sounds like a hack.

---

### Post by DOSIX on 2011-01-20
every fix you make on ubuntu is a hack! that's the beauty of linux.

---

### Post by BruisedQuasar07 on 2011-01-21
Diablo75,

Do not toss Linux due to this experience. Believe me,you are still better off with it over Windows. 

I have a similar issue. I use Ethernet because its faster and less troublesome for me. I only 
use wifi when I'm at a library or otherwise away from my home.

I've used primarily Linux four years now. I tested and played with the major Linux distros for 15 
years. I am amazed at how far certain practical minded Distro project teams like Ubuntu, LinuxMint, 
Simply Mepis & Puppy Linux have advanced Linux user friendliness over the last three years.

You would not believe the time investment Linux required only four years ago. Just two years ago, 
many Linux newbies gave up trying to get wifi to work in their computer and many fled back to Windows 
when they encountered two issues: Getting their printer to work and getting Wifi to work.

I know the difficulties Microsoft causes for Linux developers. They pressure hardware makers not to 
cooperate with Linux project teams. Those road blocks leave me amazed at how in most cases Ubuntu 
10.10 can automatically install laptop Wifi and printers. Just a year ago it took some knowledge and 
work to get most printers up and running.

When I installed Ubuntu 10.10 in my 2010 model Thinkpad Edge wifi was working. It took seconds
to get my printer running. I only had an input issue. But it was a computer USE killer. I got some 
dumb (dumb because negative) remarks when I tried to get help with the input issue. Genius replies 
like "it doesn't do that in my laptop", the implication being the dishonest one that they too have an 
Edge and Ubuntu works perfectly for them. Fortunately, I've been computing since Apple began. I tried 
several major distros 
and got the same input problem.

I knew the problem was a Linux driver problem with some new hardware in my Edge. Finally I realized 
with the help of a mature young Edge owner at Linuxquestions forum that his Thinkpad X series had the same 
hardware as my Edge and he found the issue was not the keyboard, AMD P529 Turion or the Graphics chipset as 
I presumed. (I was kicking myself for forgetting my Linux rule to never get the latest hardware & to make
sure before I buy new that the laptop & all its hardware works in the newest distro releases. I just
continued to use my Thinkpad T-60 until I found an answer. It came a month later. I know from experience
it would just take some time. I could have been a "real man" and invested hours and hours into
pinning down the problem and the solution but I would also have lost thousands of dollars and some
fun using my time that way. This dummy earns a good living from home by studying and investing in
stocks. I'd rather USE my laptop researching to make sure I am correct that Wallstreet is wrong about 
Apple and Steve Jobs and make several thousand in one day)

It was the new lenovo touchpad. Its too sensitive for existing Linux drivers. disabling the scroll pad 
solved the issue.

Having said this I must point out how dramatically improved the Linux community is compared to just five to 
eight years ago. I had nearly given up on linux ever being a real alternative to goofy Windows
because the community (12 or more years ago seemed dominated by socially challenged power users who spent more 
time in Linux and much less using their computers than with living a real life. They intentionally
spoke in Code and shorthand so non-Linux obsessed people could not comprehend them and then insulted them when they 
asked for a normal English language explanation and told them to get back to Windows when they objected to the rank
incivility.

It was not that long ago that the founders of Ubuntu, Puppy Linux, Mepis, & LinuxMint changed the basic attitude of 
Linux communities.

So, hang in there. Your issue is not a huge one, nor is mine. Its just a nuisance (certainly mine is), having to 
disable wireless each time I boot up. 

You are absolutely correct in thinking disabling your internal wifi should be a simple menu option, I think there is 
a simple solution.I find it hard to believe that the user friendly Ubuntu project team is so thick they did not know 
to make it easy to disable an internal wifi card.

Meanwhile, there have always been Linux power users who want to convince Newbies they are thick or need to learn scripting 
and code in order to use Linux, the conclusion being "whats a matter you? Not man enough to invest 10 hours of reading 
and study for every 30 minutes of computer USE?" To that I say "What, you mean a real man mechanic invests hours into
studying his screw drivers for every hour of work?"

I could be just as ridiculous and say: "What? You want Russian "War and Peace" and ancient Chinese "Art of War" 
translated into English so you can enjoy them? A real man would learn Russian and Chinese first or like many 
narcissistic math professors "Its easy" and write the exact obtuse math procedure that is in the textbook on the 
blackboard, implying: 'only a lazy idiot doesn't get it.' Sort of reminds me of the Americans I used to see in Asia 
(1960s) who would speak English very loud and slow to a speaker of Chinese, calling him stupid when he still didn't 
understand.

Pose your question @ linuxquestions.org and maybe one other appropriate section here. I will look 
around too and post what I find.

--Bruised

---

### Post by DOSIX on 2011-01-21
what he says is true. ubuntu is way better than windows. for starters, how long would you have to be on the phone with an indian tech support phone operator reading a script to you to have gotten even half the information you've gotten out of this thread? the community is awesome.

---

### Post by diablo75 on 2011-01-23
You guys don't need to do any preaching to convince me to stick with Linux; I've been a fan of it for several years.  Though I have to express minor annoyances about it from time to time when it comes to things that I've been spoiled with since Windows 95, like disabling a network interface via the GUI with four mouse clicks.  A lot else about Ubuntu is right on the ball and holds great potential for attracting mainstream OS users to an open-source platform... it's just really surprising to run into this one problem that I naively expected would have been just a strait forward and apparent as it has been in other OSs for... well, a very long time.

Anyway I'll mark this solved for now.

---

### Post by diablo75 on 2011-01-31
Well I gave it my best shot but I apparently don't know what I'm doing.

So here is all the information I can muster about this system.  Hope someone else can tell me what I'm forgetting to black list.  I've added:

ath
ath9k
ath9k_hw
ath9k_common

To /etc/modprobe.d

But the internal wireless adapter still works just fine.  Perhaps I've got too many things in this list or something.  What I want is for the external, USB adapter to work and for the internal one to be disabled.

Here is the output of lsmod:

```
Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_nvhdmi    13615  1 
snd_hda_codec_realtek   218492  1 
binfmt_misc             6599  1 
snd_hda_intel          22203  0 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
arc4                    1165  4 
rt73usb                22442  0 
crc_itu_t               1383  1 rt73usb
nvidia               9329739  38 
snd_rawmidi            17783  1 snd_seq_midi
ath9k                  88756  0 
snd_seq_midi_event      6047  1 snd_seq_midi
rt2x00usb               9779  1 rt73usb
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
rt2x00lib              27275  2 rt73usb,rt2x00usb
ath9k_common            5982  1 ath9k
ath9k_hw              292297  2 ath9k,ath9k_common
ath                     8153  2 ath9k,ath9k_hw
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231959  4 ath9k,rt2x00usb,ath9k_common,rt2x00lib
snd                    49038  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7342  0 
shpchp                 29886  0 
parport                31492  3 parport_pc,ppdev,lp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
led_class               2633  2 ath9k,rt2x00lib
i2c_nforce2             5179  0 
agpgart                32011  1 nvidia
psmouse                59033  0 
cfg80211              144694  5 ath9k,ath9k_common,rt2x00lib,ath,mac80211
serio_raw               4022  0 
joydev                  8767  0 
hid_logitech            8971  0 
ff_memless              4393  1 hid_logitech
usbhid                 36882  1 hid_logitech
hid                    67742  2 hid_logitech,usbhid
ahci                   19198  2 
forcedeth              49433  0 
libahci                21728  1 ahci
```

Output of lspci:

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

Output of lsusb:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any ideas what I'm doing wrong?

---

### Post by diablo75 on 2011-02-01
Bump.

---

### Post by DOSIX on 2011-02-01
you added it to the wrong file. can you show the output of: 
```

ls /etc/modprobe.d

```

---

### Post by YesWeCan on 2011-02-01
No one has mentioned 'ifdown'.
[http://linux.die.net/Linux-CLI/c8319.htm](http://linux.die.net/Linux-CLI/c8319.htm)

If you are running Network Manager it will try to be helpful by automatically bringing up the primary wireless interface whenever wired is not available. I guess there is a way to configure it not to or to disable it and specify your own preferences in /etc/network/interfaces
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by DOSIX on 2011-02-01
I think this might be your answer. I didn't even know that existed. Thanks a million YesWeCan.

---

### Post by diablo75 on 2011-02-01
> **DOSIX said:**
> you added it to the wrong file. can you show the output of: 
```

ls /etc/modprobe.d

```

```
alsa-base.conf              blacklist-modem.conf
blacklist                   blacklist-oss.conf
blacklist-ath_pci.conf      blacklist-watchdog.conf
blacklist.conf              intel-5300-iwlagn-disable11n.conf
blacklist-firewire.conf     ndiswrapper.conf
blacklist-framebuffer.conf  nvidia-graphics-drivers.conf

```

Edit:  I've come to realize that the "blacklist" file was created by me, but I only entered exactly the command you asked me to in a previous post on page 2:

> 'lsmod' lists all the installed modules that the kernel (the core of the operating system) is using.
Find the module that corresponds to the device you don't want to use. Once you have that, all you need to do is add it to the blacklist file. This will keep the kernel from loading the module, and ultimately disable the device.


```
sudo gedit /etc/modprobe.d/blacklist
```



So just to cut to the chase, exactly what file am I supposed to edit and exactly what modules do I need to declare blacklisted?  There seem to be 4 different modules that have the letters "ath" at the beginning of the name so I can only assume them all to be involved.  But do I need to black list them all?

---

### Post by DOSIX on 2011-02-02
yeah you gotta black list them all. but i think that i made a mistake in what file i told you to place the blacklisted drivers in. it seems to me like they should be put in the blacklist-ath_pci.conf file.

---

### Post by diablo75 on 2011-02-06
> **DOSIX said:**
> yeah you gotta black list them all. but i think that i made a mistake in what file i told you to place the blacklisted drivers in. it seems to me like they should be put in the blacklist-ath_pci.conf file.

This did the trick.  Thanks.

---

### Post by DOSIX on 2011-02-06
alright no problem.

---

