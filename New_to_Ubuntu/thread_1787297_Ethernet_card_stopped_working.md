---
title: "Ethernet card stopped working?"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by Glkanter on 2011-06-20
I gave my friend an older PC so she could use the internet.

The internet connection worked without fail for about 2 months. Then her grandsons came to visit. They used he ethernet cable on their laptops, all weekend, with no problem. She does not have a router. Then they reconnected the cable to her PC, which is running Ubuntu 10.10, and only some archived websites would come up. Refreshing would report that she was working offline. The PC is not connecting to the internet.

I've turned everything on and off.
I spoke with the cable company's tech support. She reset the cable modem. She confirmed that the modem is getting their signal, but that she is not getting a response from the PC. That was the end of her responsibility.

I ran Ubuntu's system test. It first reported that 'network passed' and 'internet failed'. Later, after I messed with things, it reported 'network failed' and 'internet failed'.

The ethernet card is a 3com 3c905c-tx/tx-m [tornado] (rev 78 ). It seems like a yellow light is flashing and an orange light is flashing.

Thanks for any and all advice!

---

### Post by jtarin on 2011-06-21
Run the command ```
lspci
``` and ```
lsmod.
```.....separately and post the results.

---

### Post by jtarin on 2011-06-21
Check you bios to ensure it is set to WOL (wake-up-on-lan)

---

### Post by DawieS on 2011-06-21
It is most probably the ethernet cable that got damaged over the weekend. Ethernet cards normally have a green LED that should stay on if the connection is good.

As a process of elimination, I recommend that you plug in another ethernet cable (known to be good) between this PC and another one, to see if you can get connection.:grin:

---

### Post by Glkanter on 2011-06-21
Thank you for the suggestions.

A new, tested ethernet cable made no difference.

Remote Wake Up is 'off'.

```

eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ lsmod
Module                  Size  Used by
usb_storage            40204  1 
binfmt_misc             6599  1 
snd_emu10k1_synth       5136  0 
snd_emux_synth         29012  1 snd_emu10k1_synth
snd_seq_virmidi         4193  1 snd_emux_synth
snd_seq_midi_emul       5547  1 snd_emux_synth
snd_emu10k1           131818  3 snd_emu10k1_synth
snd_ac97_codec         99227  1 snd_emu10k1
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_emu10k1,snd_ac97_codec
snd_page_alloc          7120  2 snd_emu10k1,snd_pcm
snd_util_mem            3118  2 snd_emux_synth,snd_emu10k1
snd_hwdep               5040  2 snd_emux_synth,snd_emu10k1
snd_seq_midi            4588  0 
radeon                917656  4 
snd_rawmidi            17783  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6047  2 snd_seq_virmidi,snd_seq_midi
snd_seq                47174  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
ttm                    56633  1 radeon
snd_timer              19067  3 snd_emu10k1,snd_pcm,snd_seq
drm_kms_helper         30200  1 radeon
snd_seq_device          5744  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
drm                   168060  5 radeon,ttm,drm_kms_helper
parport_pc             26058  1 
dcdbas                  5402  0 
snd                    49038  14 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
emu10k1_gp              1472  0 
gameport                9327  2 emu10k1_gp
intel_agp              26566  1 
psmouse                59033  0 
soundcore                880  1 snd
serio_raw               4022  0 
i2c_algo_bit            5168  1 radeon
shpchp                 29886  0 
agpgart                32011  3 ttm,drm,intel_agp
intel_rng               2320  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21234  0 
3c59x                  32011  0 
firewire_core          46643  1 firewire_ohci
floppy                 54311  0 
crc_itu_t               1383  1 firewire_core
mii                     4425  1 3c59x
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ 

``````
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R200 BB [Radeon All in Wonder 8500DV]
01:00.1 PCI bridge: ATI Technologies Inc R200 BC [Radeon All in Wonder 8500]
02:00.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 04)
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
03:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
03:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
03:0b.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
03:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ 

```I appreciate the help. I'm at a complete loss on this.

---

### Post by jtarin on 2011-06-21
Thanks for that....now I need you to issue the command in the terminal ```
ifconfig
```then the separate command of ```
route -n
```  and post the results of each.

---

### Post by Glkanter on 2011-06-21
Yes, I'll do that tomorrow. But what is it we're looking for?

How does this amazingly simple and reliable task just stop working?

Thanks.

---

### Post by jtarin on 2011-06-21
> **Glkanter said:**
> Yes, I'll do that tomorrow. But what is it we're looking for?

How does this amazingly simple and reliable task just stop working?

Thanks.I'm looking to see if the correct driver is loaded for your card and if the system recognizes it. When you look at the back of your computer (I'm assuming this is a desktop)at the location the cable enters the box......do you see a small solid not flashing green light in that area when the computer is on and your cable plugged in? No...tell me exactly what lights you see and their behavior.

---

### Post by Glkanter on 2011-06-21
I looked at this, and reported it yesterday. There is an orange flashing light and a yellow flashing light.

This is what I don't get: What changed? Everything was fine, perfect, almost. Then the cable is removed, plugged into a couple of Windows laptops successfully, then doesn't work on the Ubuntu desktop.

I mean, I know that's what happened (although I was not there), but *why*?

Thanks!

---

### Post by jtarin on 2011-06-21
Does the cable company identify the valid computer online by the MAC address of the ethernet card or the MAC address of their modem? Your not using a router are you?

---

### Post by Glkanter on 2011-06-21
There is no router.

When I spoke with the cable company's tech support, I took the power plug out of the cable modem. Once it was back on, the tech person sent the 'reset' command. She could see that the modem was responding. She could also see that the PC's network card was not responding. At that point, she said there was nothing else she could do for me, as her equipment was doing it's job properly.

---

### Post by jtarin on 2011-06-21
Try to reseat the card it might have loosened with moving around or unplugging cables. The again it might be kaput. Run those commands I gave you and lets look a little further.

---

### Post by Glkanter on 2011-06-21
Yes, I will run the commands and re-seat the card tomorrow.

I thought about re-seating, but I figured there were too many clues indicating that it was ok.

Thanks.

---

### Post by jtarin on 2011-06-22
> **Glkanter said:**
> Yes, I will run the commands and re-seat the card tomorrow.

I thought about re-seating, but I figured there were too many clues indicating that it was ok.

Thanks.Run the commands first and then we'll see. The lights should be one a steady green if the card is transferring 10-100mbs and blue if it is above 100mbs. The amber one would be flickering if there was anything being transmitted.

---

### Post by jtarin on 2011-06-22
A thought....has there been any kernel updates in the time the computer left your hands and the time it was returned in non-working order? Also something to try to eliminate any software configuration if you still have the Ubuntu CD....boot with it and see if you can connect.

---

### Post by Glkanter on 2011-06-22
The visiting grandsons did something regarding a gmail account's password, so I am certain the system was working before the cable was removed.

I set the Ubuntu update frequency to the max, which I think is 2 weeks just a week or two ago. With her being a novice user, I can't imagine any updates have been done without my involvement.

But I will take a live 10.10 cd with me to test if it works. Great idea!

Thanks!

---

### Post by jtarin on 2011-06-22
Keep me posted.:p

---

### Post by Glkanter on 2011-06-22
The card doesn't need to be re-seated. It's integrated into the motherboard.

```
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:b0:d0:17:20:9d  
          inet6 addr: fe80::2b0:d0ff:fe17:209d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7841 errors:0 dropped:0 overruns:1 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:482274 (482.2 KB)  TX bytes:4663 (4.6 KB)
          Interrupt:11 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2720 (2.7 KB)  TX bytes:2720 (2.7 KB)

eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ 

``````

eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ 

```I tried the live 10.10 cd twice. I saw a 'fail' message scroll by the 2nd time, but couldn't 'grab' it. I've attached a photo of the screen.

---

### Post by jtarin on 2011-06-22
Do you use Network Manager to connect?

---

### Post by Glkanter on 2011-06-22
I don't even know what Network Manager is.

That's the thing. Ubuntu has always just configured itself for the ethernet card and the internet. Even when I would use the live cd, the thing just always has a working network connection. I just click on Firefox, and I'm on my way.

So, what do those commands tell you?

---

### Post by jtarin on 2011-06-22
Your ifconfig tells me one of two things.....your "eth0" has been renamed to "eth1", which is only normal if you have 2 ethernet cards and one is disabled.Possibly your connection is looking for the former.Let's look at some configs. Issue the command 
```
cat /etc/iftab
```and post the results. We'll see what matches and what doesn't.

---

### Post by Glkanter on 2011-06-22
Let me answer your earlier question a different way: The first day I addressed the problem, I messed around with some things. System->Administration->Network Tools was definitely one of them. System->Preferences->Network Connections and System->Preferences->Network Proxy were others. That's probably it. (I'm giving you the 11.04 names for those programs, but the subject system is 10.10.)

I certainly could have caused eth-1 to have happened. I didn't mess around with a whole lot of settings, but I *was* there.

---

### Post by Glkanter on 2011-06-22
I try out your commands at home, and this one didn't do so good:

glkanter@glkanter-System-Product-Name:~$ cat /etc/iftab
cat: /etc/iftab: No such file or directory
glkanter@glkanter-System-Product-Name:~$ 

I used copy & paste for the command, so I didn't make a typo...

---

### Post by jtarin on 2011-06-22
> **Glkanter said:**
> Let me answer your earlier question a different way: The first day I addressed the problem, I messed around with some things. System->Administration->Network Tools was definitely one of them. System->Preferences->Network Connections and System->Preferences->Network Proxy were others. That's probably it. (I'm giving you the 11.04 names for those programs, but the subject system is 10.10.)

I certainly could have caused eth-1 to have happened. I didn't mess around with a whole lot of settings, but I *was* there.We'll look at th
at if we need to.....first the file posting.```
cat /etc/iftab
```

---

### Post by jtarin on 2011-06-22
Try```
cat /etc/network/interfaces
```

---

### Post by Glkanter on 2011-06-22
That gave a response.

By the way, I appreciate all your patient help on this. You're very generous with your time and knowledge.

Thanks.

---

### Post by jtarin on 2011-06-22
Post the results here

---

### Post by jtarin on 2011-06-22
> **Glkanter said:**
> That gave a response.

By the way, I appreciate all your patient help on this. You're very generous with your time and knowledge.

Thanks.
I teach English and I do this between students during the day and my wife's tirades to get off the forum at night.:P

---

### Post by jtarin on 2011-06-22
Can you search for that file /etc/iftab file? I'm not on my machine at home so I cant verify it is in the latest Ubuntu.

---

### Post by Glkanter on 2011-06-22
Well, we just discovered one area where my skills end. I'm not even sure what you're asking me to do.:confused:

---

### Post by jtarin on 2011-06-23
> **Glkanter said:**
> Well, we just discovered one area where my skills end. I'm not even sure what you're asking me to do.:confused:post the results from ```
cat /etc/network/interfaces
```

---

### Post by jtarin on 2011-06-23
You can copy and paste to and from the terminal.

---

### Post by Glkanter on 2011-06-23
I'm confused. Is that command for the PC with the ethernet problem, or for my PC that didn't recognize the previous command when I tested it?

---

### Post by jtarin on 2011-06-23
> **Glkanter said:**
> I'm confused. Is that command for the PC with the ethernet problem, or for my PC that didn't recognize the previous command when I tested it?All these commands are to be issued on the machine with the internet problem any other machine would be useless.

---

### Post by Glkanter on 2011-06-23
This is what I have no idea how to respond to:

"Can you search for that file /etc/iftab file? I'm not on my machine at home so I cant verify it is in the latest Ubuntu."

I'll talk to you tomorrow. Thanks for everything!

---

### Post by Glkanter on 2011-06-23
Thursday's results:

```
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ cat /etc/iftab
cat: /etc/iftab: No such file or directory
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$
``````
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ 


```

---

### Post by jtarin on 2011-06-23
Ok try the command ```
sudo /sbin/ifconfig eth0 up
```and without closing the terminal bring up a browser and see if you connect.

---

### Post by Glkanter on 2011-06-23
I will do so in about 18 hours.

Thanks!

---

### Post by Glkanter on 2011-06-24
Two thoughts while I can't sleep:

There might be a 2nd ethernet card in that PC. I didn't really look.

I could have brought the PC back to my place, since without the internet, it's just sitting there. Then this troubleshooting would have all been done in one evening.

Too soon old, and too late smart. <sigh>

---

### Post by grahammechanical on 2011-06-24
Can I butt in and make a comment? Thank you.

From the listing in ifconfig I see this:

> eth1    Link encap: Ethernet    HWaddr 00:b0:17:20:9d
          inet6 addr:   fe80::2b0:d0ff:fe17:209d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1This tells me a few things. I may be wrong about all of this but 

1) if you have two ethernet ports on the machine then one of these physical ports will be eth0 and the other eth1. The change from eth0 to eth1 is simply because the cable was put in the eth1 port and not the eth0 port. 

2) The words UP and the RUNNING tell me that the ethernet adapter is recognized by the OS and is working.

3) There should be a line above inet6 addr: that looks something like this

>  inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0This is from the ifconfig report on my machine. It tells me that my network adapter is connected to my router/modem. The absence of this line in your ifconfig report tells me that the machine has not connected to the router. The service provider also said that the computer was not responding to her test signals.

Network manager is a utility that does what its name implies. There will be an icon in the top panel. It should look like curved arcs radiating upwards. It should have a red exclamation mark set against it. There should also be messages saying not connected. Click the icon (left and right) and see if the line Enable Networking has a tick mark on it. If not the click the line to put the tick mark there and reboot.

Please also consider this possibility. Did the service provider put a special network card into the computer to make the cable connection to their router/hub? If so, then the cable from that router maybe plugged into the wrong network port. It maybe plugged into one of the standard ethernet ports and not the special ethernet port that connects to the service provider's router. This is just a crazy thought that I have had in my ignorance. You could also try putting the cable into the other ethernet port. Then it will become eth0 again.

Regards.

---

### Post by Glkanter on 2011-06-24
Hi, thanks for dropping in.

The PC in question was given to me. I, in turn gave it to the lady that has it now. I'm certain the internet provider did not add an ethernet card, but I'm not 100% certain that one had not been added previously.

There is no router.

Your's is the 2nd mention of Network Manager. I am familiar with the curved lines, etc, but it is not on any panel. Can you tell me the path for adding it? The PC in question is Ubuntu 10.10. (My PC is 11.04. While the Ubuntu Software Center reports I have installed Network Manager, I cannot find it on the menu system, nor does it show up on the list of programs I can add to the panel. My 11.04 system uses the old user interface.)

Thanks.

---

### Post by Glkanter on 2011-06-25
As instructed:
```
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ sudo /sbin/ifconfig eth0 up
[sudo] password for eileen: 
eth0: ERROR while getting interface flags: No such device
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ 
```Thinking it couldn't hurt, and might help:
```
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ sudo /sbin/ifconfig eth1 up
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ 
```Leaving Terminal open, when I clicked on Firefox, it immediately went to the 'offline' error page. Which is different than it did previously, when it would go to a cached version of the home page.

---

### Post by jtarin on 2011-06-25
After running the command ```
sudo /sbin/ifconfig eth1 up
``` at the prompt type ifconfig and lets see what it shows.

---

### Post by jtarin on 2011-06-25
```
sudo gedit /etc/network/interfaces
```
and edit your file to look like this:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
```
Save

then
```
sudo /sbin/ifconfig eth1 down
```
then
```
sudo /sbin/ifconfig eth1 up
```
Now
```
ifconfig
```
Post that result

---

### Post by jtarin on 2011-06-25
[Here's]("http://wiki.debian.org/NetworkConfiguration") some additional info for you to use.

---

### Post by no2498 on 2011-06-25
just thinking is the browser set to work off line

if it is will not most of the test fail

---

### Post by jtarin on 2011-06-25
> **no2498 said:**
> just thinking is the browser set to work off line

if it is will not most of the test failThat's why we're not just using the browser but also the command line.

---

### Post by Glkanter on 2011-06-29
Hi guys!

```
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ sudo /sbin/ifconfig eth1 up
[sudo] password for eileen: 
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:b0:d0:17:20:9d  
          inet6 addr: fe80::2b0:d0ff:fe17:209d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11515267 errors:0 dropped:0 overruns:1 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:714084294 (714.0 MB)  TX bytes:4380 (4.3 KB)
          Interrupt:11 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:421136 (421.1 KB)  TX bytes:421136 (421.1 KB)

eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ sudo gedit /etc/network/interfaces
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ sudo /sbin/ifconfig eth1 down
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ sudo /sbin/ifconfig eth1 up
eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:b0:d0:17:20:9d  
          inet6 addr: fe80::2b0:d0ff:fe17:209d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11523886 errors:0 dropped:0 overruns:1 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:714613862 (714.6 MB)  TX bytes:7913 (7.9 KB)
          Interrupt:11 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:421136 (421.1 KB)  TX bytes:421136 (421.1 KB)

eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ 



```I copy/pasted the desired result into the 'interfaces' file. The first two lines were unchanged, but I replaced them anyways. The attachment is a screen print of that file.

I brought the PC home with me, so if anyone is still interested, we can do any number of iterations in 'real time'.

Thanks a million!

---

### Post by jtarin on 2011-06-29
> **Glkanter said:**
> I copy/pasted the desired result into the 'interfaces' file. The first two lines were unchanged, but I replaced them anyways. The attachment is a screen print of that file.

Did you do this as root?

---

### Post by Glkanter on 2011-06-29
1. I don't know what that question means.
2. What you see is exactly what I entered, except the password isn't shown. That is the complete, unabridged record of the terminal session.

Thanks!

---

### Post by jtarin on 2011-06-29
> **Glkanter said:**
> 1. I don't know what that question means.
2. What you see is exactly what I entered, except the password isn't shown. That is the complete, unabridged record of the terminal session.

Thanks!What I mean is when you copied and pasted the file and saved it did you do it as "root" (sudo). If you did the file will still be there as you copied and pasted. Is it still there in that same way?

---

### Post by Glkanter on 2011-06-29
Sure. I copied your exact command:
"eileen@eileen-ER921AA-ABA-SR1830NX-NA660:~$ sudo gedit /etc/network/interfaces"

---

### Post by jtarin on 2011-06-29
Is your Ubuntu computer connected by cable to your modem and ready for internet connection?

---

### Post by Glkanter on 2011-06-29
Negatory on that.

1. A router will be involved here at my place.
2. I gotta do some policing of the area, and run a couple of errands first.

It is currently 7:15 pm in Ohio, USA. Can we schedule something that is good for your schedule, say in an hour or so?

Thanks!

---

### Post by jtarin on 2011-06-29
Ok

---

### Post by Glkanter on 2011-06-29
Well, how about that?

The internet is working perfectly. Upon booting. Period.

---

### Post by jtarin on 2011-06-29
Thank God! :lolflag:
Mark this thread as solved if you would.

---

### Post by Glkanter on 2011-06-29
I would, but it's not. But maybe it's not a Ubuntu issue any longer (if it ever was).

It didn't work this morning at my friend's house when I followed your instructions.

Any idea why it works at my place, but not her's?

Thanks!

---

### Post by jtarin on 2011-06-29
If you both have the same connection setup I have no clue. It would only point to loss of connection at her modem possibly bad wiring or non-payment of services.

---

### Post by Glkanter on 2011-06-29
Yeah, the whole thing hasn't made a lick of sense the whole time.

Thank you for your guidance and patience.

---

### Post by jtarin on 2011-06-29
Mark as solved if you will.

---

### Post by Glkanter on 2011-07-04
And finally, on Sunday, I returned the computer to it's owner. Plugged it in. Powered it on. Began surfing the internet as usual.

One for the books.

---

### Post by jtarin on 2011-07-04
Excellent!! Good Luck with Ubuntu.

---

### Post by Glkanter on 2011-07-04
It's not excellent, really.

This isn't my first rodeo by any stretch, and this is the single most inexplicable computer related problem I've ever had.

Thank goodness it decided to start working again, because it wasn't anything you or I did.

---

### Post by jtarin on 2011-07-04
You might say that but I beg to differ......we went through normal procedures for this type of situation and one of them set it right. I can't explain it fully as I am not on your end and rely solely on input I get from you to direct you. BTW, I'm semi-retired from that rodeo.

---

### Post by Glkanter on 2011-07-04
I'll never argue over a success, but the chronology of events that I experienced and described is *not* consistent with you and I solving the problem.

But thank you, thank you, thank you, for all your patience and experience.

---

### Post by UndefinedDecoder on 2011-07-09
i was just experiencing the same issues and after trying *everything* i could think of, i remembered i had set IPv6 to 'auto' to see what it would do. i had forgotten about it because the changes didn't take place until i rebooted almost 5 hours later :? so after some research (via my wireless connection less than a foot from my router) i found this

if your internet service provider does not give you a IPv6 IP address you need to set IPv6 to 'ignore' in your connection settings.   [http://test-ipv6.com/](http://test-ipv6.com/) will test your IPv6  [http://test-ipv6.com/ipv6day.html](http://test-ipv6.com/ipv6day.html) FAQ of the subject

this solved the problem for me btw

---

