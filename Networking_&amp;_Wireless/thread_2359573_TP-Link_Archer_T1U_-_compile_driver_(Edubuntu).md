---
title: "TP-Link Archer T1U - compile driver (Edubuntu)"
date: 2017-04-25
forum: Networking &amp; Wireless
---

### Post by nickelbabe on 2017-04-25
Hello :)

When I say "I'm new to Ubuntu" please know that I mean I am really, really new and have literally only just installed it.

I've got Edubuntu (for my daughter), latest version and I've no idea how to ask the computer what its called and what the details are.
I do know how to get that command window up (ctrl+alt+t)

I need to get onto the internet, so I bought a TP-Link Archer T1U (as it said it did linux)

I went to the TP-Link website and downloaded their instructions, and read the words on the page, didn't understand a single one of them, but think it wanted me to type some stuff in.
So I did.
the page was:
[ATTACH=CONFIG]274757[/ATTACH]
I can't get a screenprint because that computer is not yet connected to the internet, but my phone camera has captured the mess:
[ATTACH=CONFIG]274758[/ATTACH]

I just have no clue where to even start.

I would be very grateful indeed if someone could please tell me exactly what to type in to the command box (from the very beginning).
And then what to type after I've typed all that in order to actually install the dongle.

(and please no "type xxx which is your computer's name/id/something specific" because I don't understand what that means)


thank you
:)

---

### Post by howefield on 2017-04-25
Welcome to the forums.

I've moved you thread to the "*Networking & Wireless*" forums as it is probably a better fit.

---

### Post by chili555 on 2017-04-25
There is probably a much easier way to get the driver for your device than to follow the instructions that came with it. They are undoubtedly far too old.

Please insert the device and open a terminal and type:```
lsusb
```I think it will report that your device is: 2357:0105  with no further details. In any case, post it here.

If it is the aforementioned device, it will be somewhere between extremely difficult and impossible to get working. If you have the option to return it for a supported device, I'd think seriously about it.

We'd also like to see the result of:```
uname  -r
```The result should be very small; no need for a phone picture.

---

### Post by nickelbabe on 2017-04-25
yes, it does say 2357:0105

but then it came up with a list of 
bus 001 <something something something


the result of 
uname -r 
is
4.4.0-31 generic

I don't suppose you know what devices might be supported please?
That was the only one currys had (and we're in the process of getting a Maplin, but it hasn't got an open date yet)

thank you

---

### Post by chili555 on 2017-04-25
We might just have some luck with your 4.4 kernel; fingers crossed! It won't take much to find out.

Remove the device from the USB slot.

Please download this file on another computer and transfer it on a USB key or similar to the desktop of your daughter's computer: [https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes/archive/master.zip](https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes/archive/master.zip) After you have transferred it, right-click it and select 'Extract Here.' A new folder will appear called mt7610u-linksys-ae6000-wifi-fixes-master. Nice handy name to type into the terminal, eh? Actually, the magic of Linux and Ubuntu will help us a bit here. We will use Tab to autocomplete the command. Open a terminal and type in:```
cd ~/Desktop/mt7
```Press Tab and the remainder of the name should autocomplete so that it now reads:```
cd ~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master
```Woo hoo! Press Enter.

Now please run:```
make
```It will probably build with a few warnings but will end something like this:```
 CC [M]  /home/chili/Downloads/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux/../../common/frq_cal.o
  LD [M]  /home/chili/Downloads/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux/mt7610u_sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chili/Downloads/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux/mt7610u_sta.mod.o
  LD [M]  /home/chili/Downloads/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux/mt7610u_sta.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-19-generic'
cp -f /home/chili/Downloads/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux/mt7610u_sta.ko /tftpboot 2>/dev/null || :

```If so, give another woo hoo and proceed:```
sudo make install
```Insert the device.

Are there any signs of success? 

I will have other steps and comments, so post back your experience so we may continue.

---

### Post by nickelbabe on 2017-04-25
okay, this might take me a few mintues :D
thank you - I'll let you know how I get on.

(I'm assuming "USB key" means normal flash drive?)

right, i got as far as the 
```

cd ~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master
```

then i pressed enter (woohoo)
but when i typed
```
 make 
```

i got 
```
 make *** No targets specified and no makefile found. Stop. 
```

did i miss a step?

it does hve my original name though, too - the entire command prompt thing reads:

```
 marshall@marshall-GA-8ISXT:~/Desktop/mt7610u-linksys-ae6000-wifi-fixes-master$ 
```

the makefile is definitely in the folder

ahaha!

i have the make running - it looks like my flash drive unzipped the zip file when i transferred it onto the key, so i've done it on another one.

I'm now at the stage

"If so, give another woo hoo and proceed:"

okay, device inserted.

i now have on my command box
stuff saying "entering directory" 
and "leaving directory home etc"

(do you want me to put a picture up?)

---

### Post by chili555 on 2017-04-25
Did you let 'make' run all the way to conclusion? Then did you do 'sudo make install'? And then and only then did you insert the device?

PS- I hope as all those lines of code flashed by that you told your daughter, "Look! nicklebabe is a kernel hacker and a driver dawg!"

---

### Post by nickelbabe on 2017-04-25
yes, i waited until it said the last thing on your code box, and then i did sudo make install, and waited for it to do its thing and then inserted the device.

and now waiting for next instruction

I did say "woohoo! Look at that!"
:D

[ATTACH=CONFIG]274763[/ATTACH]

---

### Post by chili555 on 2017-04-25
Did the driver module load as expected?```
lsmod
```Do you see mt7610u_sta listed? If not, let's load it:```
sudo modprobe mt7610u_sta
```Is a wireless interface created? wlx-something??```
iwconfig
```If so, does it scan?```
sudo iwlist scan
```You needn't do pictures, just tell us yes, no or...otherwise.

If there is no wireless interface wlx-something, look for clues here:```
modinfo mt7610u_sta | grep 0105
dmesg | grep mt76
```The funny pipe symbol | is on the right side of my US keyboard on the same key with \.

I think we need a picture for the last two. Sorry.

On the other hand, if there is an interface and it scans, it ought to connect!!!

---

### Post by nickelbabe on 2017-04-25
> **chili555 said:**
> Did the driver module load as expected?```
lsmod
```

Do you see mt7610u_sta listed? If not, let's load it:```
sudo modprobe mt7610u_sta
```
[B]
yes to both of these if i'm still 
:~desktop/mt7610u etc
[/B]
Is a wireless interface created? wlx-something??```
iwconfig
```If so, does it scan?```
sudo iwlist scan
```You needn't do pictures, just tell us yes, no or...otherwise.

[B]no, this comes up with 
lo Interface doesn't support scanning
and
eth0 Inerface doesn't support scanning[/B]

If there is no wireless interface wlx-something, look for clues here:```
modinfo mt7610u_sta | grep 0105
dmesg | grep mt76
```The funny pipe symbol | is on the right side of my US keyboard on the same key with \.

**pics for both of the last two lines**
[ATTACH=CONFIG]274764[/ATTACH][ATTACH=CONFIG]274765[/ATTACH]


I think we need a picture for the last two. Sorry.

On the other hand, if there is an interface and it scans, it ought to connect!!!

i don't know if this makes any difference, but i left the pc on while waiting for your response and it had gone to sleep when i got back - i don't know if this would have cancelled everything we'd done up to there.

ooh!
 i do have the mt7601u_sta in the directory when i'm only marshall@marshallGA-8ISXT:~$ 

but iwconfig
still comes up with nothing there

```
 lo        no wireless extensions.

eth0      no wireless extensions.
```

and then i gt for 
```
modinfo mt7610u_sta | grep 0105
```
this
```
 modinfo: ERROR: Module mt7601u_sta not found.
```

and for 
```

dmesg | grep mt76 
```

the same as in the picture above

---

### Post by chili555 on 2017-04-25
> it had gone to sleep when i got back - i don't know if this would have cancelled everything we'd done up to there.It doesn't erase it.> and then i gt for 
Code:
modinfo mt7610u_sta | grep 0105
this
Code:
 modinfo: ERROR: Module mt76[COLOR="#FF0000"]01[/COLOR]u_sta not found.It appears that there is a typo here. The module it built is mt7610u_sta;> LD [M]  /home/chili/Downloads/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux/[COLOR="#FF0000"]mt7610u_sta[/COLOR].ko
...and not mt7601u_sta.

I decided to check the file myself to see if it covers your device:```
$ modinfo os/linux/mt7610u_sta.ko
filename:       /home/chili/Downloads/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux/mt7610u_sta.ko
version:        3.0.0.2
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
license:        GPL
srcversion:     52AD08FADC7D7981998F7E4
alias:          usb:v0E8Dp7650d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v0E8Dp7630d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v20F4p806Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB31d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v293Cp5702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8502d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0951d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3425d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3D02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0075d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17DBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp761Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pC711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pB711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp7610d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           mac:wireless mac addr (charp)
parm:           debug:log verbosity level (0: off, 1: error only [default], 2: warnings, 3: trace, 4: info, 5: loud) (long)

```Notice that your 2357:0105 is not listed. 

Boooooo!!!

I'd like to work out how to amend the driver code to include it, however, Mrs. Chili is serving supper. I will post back full instructions later.

---

### Post by chili555 on 2017-04-25
Let's try an experiment. From the terminal:```
sudo -i
modprobe mt7610u_sta
echo "2357 0105"  >  /sys/bus/usb/drivers/rt2870/new_id
exit
```Any signs of life?```
iwconfig
sudo iwlist scan
```If this works, we'll amend one file and make it permanent.

---

### Post by nickelbabe on 2017-04-26
>  and then i gt for 
Code:
modinfo mt7610u_sta | grep 0105
this
Code:
 modinfo: ERROR: Module mt76[COLOR=#FF0000]01[/COLOR]u_sta not found.                            It appears that there is a typo here. The module it built is mt7610u_sta;                                                         LD [M]  /home/chili/Downloads/mt7610u-linksys-ae6000-wifi-fixes-master/os/linux/[COLOR=#FF0000]mt7610u_sta[/COLOR].ko                      
     
 
...and not mt7601u_sta.

that's cos i can't type.
sorry
okay, when i type 
```
 modinfo mt7610u_sta | grep 0105
```
it returns just the command prompt


just reading the rest of your replies

> Let's try an experiment. From the terminal: 	Code:

 	```
sudo -i
modprobe mt7610u_sta
echo "2357 0105"  >  /sys/bus/usb/drivers/rt2870/new_id
exit
``` 
Any signs of life? 

this gets me
[ATTACH=CONFIG]274772[/ATTACH] 	
> Code:

 	```
iwconfig
sudo iwlist scan 
```

gets me 
[ATTACH=CONFIG]274773[/ATTACH][ATTACH=CONFIG]274774[/ATTACH]

which fills me with some hope becuase it mentions bt-hub5-fznts (and two others- all of which appear on my wifi list on my pc)
(unfortunately, that's next door's - our is sky4984F...)
but at least it's found something right?
:D

and look! :o
[ATTACH=CONFIG]274775[/ATTACH]

---

### Post by chili555 on 2017-04-26
I wonder if your router is on a frequency that the device doesn't (yet) see. There are channels used in some countries that are not used in others due to regulation. Let's try setting the regulatory domain and see if it helps.

Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Unload and reload the driver:```
sudo -i
modprobe -r mt7610u_sta
modprobe mt7610u_sta
echo "2357 0105"  >  /sys/bus/usb/drivers/rt2870/new_id
exit
```Now does it see your network?```
sudo iwlist scan
```No picture needed; just does it (woo hoo) or does it not (boo hoo).

Let's see what channels the device does:```
sudo iwlist chan
```No pics again; does it do 1-11 or 1-13?

Is your router set to use 5 gHz? If so, and if the channel list you got above doesn't list channels in the 5 gHz range and your router is set to 5 gHz, then they will never see each other and connect. 

Here is a sample from my machine:```
wlp3s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : [COLOR="#FF0000"]5.18 GHz[/COLOR]
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:5.745 GHz (Channel 149)

```In the USA, channels 12, 13 and the very rare 14 are not used. 

Perhaps you can tell from other computers, tablets, phones, etc. what frequency the router is on.

---

### Post by nickelbabe on 2017-04-26
it says country 00

so i typed
```
 
sudo iw reg set GB
```

and got the command prompt

then i typed ```
 
gksudo gedit /etc/default/crda 
```
and got 

```
 the programe gksudo is currently not installed. you can install it by typing:
sudo apt-get install gksu
```

i tried to do get install gksudo but it said 
```
unable to locate package gksudo
```

---

### Post by praseodym on 2017-04-26
Alternatively, run this one-liner:

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=GB/g" /etc/default/crda 
```
Reboot

---

### Post by nickelbabe on 2017-04-26
when i've run that, do you mean reboot the computer?

and then where do i go in chilli's script after that please?

(thank you)

i've rebooted and now i've got no wifi listed at all.

and boohoo
for the iwlist scan
 and boohoo for
iwlist chan

i do know that the router is 2.4 gHz

---

### Post by chili555 on 2017-04-26
> i've rebooted and now i've got no wifi listed at all.Until we decide that this driver suite definitely will or will not work and implement a permanent fix, after reboot it will be necessary to repeat:```
sudo -i
modprobe mt7610u_sta
echo "2357 0105"  >  /sys/bus/usb/drivers/rt2870/new_id
exit
```Now does your router appear?```
sudo iwlist scan
```

---

### Post by nickelbabe on 2017-04-27
okay, I've repeated that code in the command box, and it still only lists the BT wifi hubs.

I get 
BT-hub5-FZNTS
BT-wifi-with-FON
and
BT-Wifi-X

but no Sky4984F

(on the plus side, I can now remember the mt7610u_sta off by heart ;)

One thought I had, was, is it maybe out of range?

---

### Post by chili555 on 2017-04-27
> One thought I had, was, is it maybe out of range?Unlikely, as it is your router, yes? I assume it is in your own home. If this is a laptop, walk it over and try again:```
sudo iwlist scan
```So what channel is your router on? What channels does the USB wireless see?```
sudo iwlist chan
```

---

### Post by nickelbabe on 2017-04-27
it's not a laptop, unfortunately, but it is an old computer (but of course a new dongle.)

it's on channel 11, according to the computer in the other room.
and ```
sudo iwlist chan
```
shows channels 1-13 (inclusive), then 36 etc

but,at the bottom of the channel list it says
```
Current Frequency=2.413 GHz (Channel 1)
```

(channel 11 is listed as 2.462GHz)

---

### Post by chili555 on 2017-04-29
I have been giving considerable thought and more than considerable research into your problem. It is tempting to gather more syslog outputs. It is tempting to try to tweak a few things, especially the DAT file that gets installed. However, I have had no luck whatever with the mt7610 chipset at all. The driver that you ably compiled which is relatively recent, doesn't even include the usb.id for your exact device. We had to force it in with the /sys/bus/usb/drivers/rt2870/new_id mechanism. It is not exactly unexpected that it didn't work perfectly. It worked just well enough to tease us by scanning and seeing some networks but not all. Of course, it never connected nor passed web pages nor emails nor the all important Facebook posts from grandpa!

I feel that it is time to abandon the project and recommend a working out of the box device.

Several of us, including me, use this: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/) Be certain to get that exact device, the newer model has a different NOT working out of the box chipset.

You may also get some ideas here: [https://ubuntuforums.org/showthread.php?t=2309068](https://ubuntuforums.org/showthread.php?t=2309068) and here: [https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

I regret that we were unable to coax the Archer to life.

---

### Post by nickelbabe on 2017-05-06
Thank you for all your help Chili, I think you're right.

Really, the only thing she needs the internet for right now, is to update and upload programmes (like the VLC player) that have to be downloaded from the software centre.
She's happy right now with the ones that are already on there.

My own computer uses an older version of the TP-Link, I wonder if that would work in hers?
I think it's called TL-WN725N (that's what I get from the wifi info, but I don't have a clue where the little installation disc is)
I'll have a search to see if I can get any more information on that.
(and then switch mine to the new one)

Thank you again for all your help.
nickel

---

### Post by chili555 on 2017-05-06
> I think it's called TL-WN725N (that's what I get from the wifi infoInsert it in daughter's computer and run:```
lsusb
```Tell us what it is. It might just show eight numbers and letters, something like 12ab:34cd, with no other description. If it is what I think it is, we can probably get that one working fairly easily!

Can you easily trade devices with her?

--------------

Note to Chili: 8188eu?  [https://askubuntu.com/questions/912498/tl-wn722n-is-not-recognized/912507#912507](https://askubuntu.com/questions/912498/tl-wn722n-is-not-recognized/912507#912507) Maybe??

[https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1](https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1)

---

### Post by nickelbabe on 2017-05-07
This is what I get.

---

### Post by chili555 on 2017-05-07
I'm working a crazy theory here! Please run:```
modinfo r8188eu | grep 8179
```No pic, just tell us what it says. It will either come back blank, show an alias or report that the module r8188eu is not found. Which does it tell us?

I actually think the device will be covered by the module r8188eu that is already present in the 4.4.0-xx kernel in your daughter's computer!

---

### Post by nickelbabe on 2017-05-08
When I put a gap before grep I get error no module found.
I got excited because I got 2 aliases 
usb: v07B8p etc
and
v0BDAp
But then I realised i'd put no space before grep :(

---

### Post by chili555 on 2017-05-08
> I got excited because I got 2 aliases 
usb: v07B8p etc
and
v0BDApLet's be clear. Is this what you see?```
chili@T440p:~$ modinfo r8188eu | grep 8179
alias:          usb:v07B8p[COLOR="#FF0000"]8179[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp[COLOR="#FF0000"]8179[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*

```If so, then the driver r8188eu is present on your daughter's machine and it covers your device! In the picture you posted above, it clearly says 0bda:8179.

If that is the case, is a wireless interface created? Possibly wlx-something:```
iwconfig
```Does it scan and see networks?```
sudo iwlist scan
```If it scans, can you click the Network Manager icon, see networks and connect?

In all cases, no pics required; just tell me what you see.

---

### Post by nickelbabe on 2017-05-09
Yes, that's exactly what it said.

kay, I'm trying the iwconfig now

Yes, it scans and sees our network.
Essid: sky4984f.

Yes, it sees the network and has "connect" when I click the wifi picture on.thd very top bar of the screen (next to the time and power options)

---

### Post by chili555 on 2017-05-09
> **nickelbabe said:**
> Yes, it scans and sees our network.
Essid: sky4984f.

Yes, it sees the network and has "connect" when I click the wifi picture on.thd very top bar of the screen (next to the time and power options)So, did you connect? Did you trade devices with your daughter? Are you all set?

---

### Post by nickelbabe on 2017-05-09
I think I have.
I can see the software centre and it's letting me attempt to install stuff.
I'll have to see what works. 
Unfortunately,  thr blasted other dongle doesn't work on mine either!
it's listed as every windows from xp except vista.
<sigh>
So I'll share this dongle with my daughter for now - she's only 5 so she's limited to internet access.
And I can worry about it later.

Thank you for all your help Chili :)

---

### Post by chili555 on 2017-05-09
> So I'll share this dongle with my daughter for now - she's only 5 so she's limited to internet access.I'm glad that it's sorted.

She's a lucky girl.

---

