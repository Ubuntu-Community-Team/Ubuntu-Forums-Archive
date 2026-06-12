---
title: "How do I connect xubuntu to an xfinity hotspot if the OS doesn't detect wifi signals?"
date: 2019-02-20
forum: Networking &amp; Wireless
---

### Post by jjc55 on 2019-02-20
Super newbie. The real problem is that xubuntu isn't detecting any WiFi at all, whether its public xfinity hotspot, my mobile hotspot or any other WiFi in the area. I do have a user name and password for the xfinity hotspot, as well as my mobile(obviously) but they're just not being detected. The laptop is dual boot and I can connect with windows just fine.  When clicking on the network icon on the top right of the screen it will allow me to check "enable networking", "enable WiFi", "VPN connections" and "edit connections", but the rest of the menu is greyed out. I don't have access to the router, as its a public xfinity wifi hotspot(not free),  so I don't know the SSID and stuff. I do know the SSID to my daughters router(this is who gave me the user name and password for her xfinity account), but she lives 50 miles from me so I don't think any of that is relevant.   Anyway, as previously stated, the new xubuntu installation just isn't detecting any signal at all. I've tried everything and getting really frustrated. Any help would be very much appreciated. Thanks a bunch.

---

### Post by howefield on 2019-02-20
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by chili555 on 2019-02-20
Let's gather a few details. Please open a terminal and run and then post:```
iwconfig
rfkill list all
lspci -nnk | grep 0280 -A3
```Thanks.

---

### Post by jjc55 on 2019-02-21
```
iwconfig:
wlol      IEEE 802.11 ESSID:off/any
              Mode:Managed Access Point : Not- 
              Associated  Tx-Power =off
              Retry short long limit:2 RTS thr:off 
              Fragment thr:off
              Power Management :off
enpls0  no wireless extensions. 
lo           no wireless extensions. 
rfkill list all :
0: phy0: Wireless LAN
               Soft blocked:no
               Hard blocked :yes
lspci -nnk | grep 0280 A3
07:00.0 Network controller [0280] : Ralink corp. RT5390 Wireless 802.11n 1T/1R PC Ie [1814:5390]
               Subsystem: Hewlett-Packard Company 
               U98Z077.00 Half-size Mini [103c : 1636] 
          Kernel driver in use: rt2800pci 
          Kernel modules : rt2800pci
```

---

### Post by jjc55 on 2019-02-21
Sorry about the faces, I have no idea how those got there. Thanks for any help you might give me. Super frustrated.

---

### Post by jeremy31 on 2019-02-21
Use code tags to eliminate the smilies.  Is there a switch on the computer to enable/disable wifi?

---

### Post by jjc55 on 2019-02-21
Thanks for the smiley tip. Yes there is a WiFi button, I tried that with no success. Everything works fine over in windows but I'm trying to migrate away from that platform. Anyway,  with that said, I don't know where the problem exists. The only thing I can think of is driver incompatibility. Is there any way to download the correct drivers in windows and transfer them over to xubuntu?

---

### Post by chili555 on 2019-02-21
Installing different drivers will do precisely nothing to change the rfkill issue. 

What brand of laptop is it? An Asus or an HP?

May we see:```
lsmod | grep wmi
```

---

### Post by jjc55 on 2019-02-22
Its an HP... Sorry if there are any errors in the code, I have to type it all in by hand on my phone at the moment. Painstaking business, but I'm dedicated to getting the problem solved. It should be error free. Thanks. 

lsmod | grep wmi:

hp_wmi       16384 0
sparse_keymap   16384  1 hp_wmi
wmi_bmof   16384  0
snd_rawmidi   32768  1 snd_seq_midi
snd_seq_device   16384  3  snd_seq, snd_rawmidi, 
                                snd_seq_midi
snd         81920 19 snd_had_Intel, snd_hwdep, 
               snd_seq_hda_codec, s
nd_hda_codec_idt, snd_timer, 
                snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic, 
snd_seq_device, snd_pcm
wmi        24576   2  wmi_bmof, hp_wmi

---

### Post by chili555 on 2019-02-22
> **jjc55 said:**
> 
[COLOR="#FF0000"]hp_wmi       16384 0
sparse_keymap   16384  1 hp_wmi[/COLOR]
wmi_bmof   16384  0
snd_rawmidi   32768  1 snd_seq_midi
snd_seq_device   16384  3  snd_seq, snd_rawmidi, 
                                snd_seq_midi
snd         81920 19 snd_had_Intel, snd_hwdep, 
               snd_seq_hda_codec, s
nd_hda_codec_idt, snd_timer, 
                snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic, 
snd_seq_device, snd_pcm
wmi        24576   2  wmi_bmof, hp_wmiThe issue of HP wireless being inoperable because of a hard block and therefore the usual wireless key not toggling wireless on and off is long-standing. There are only a few things you can try.

First, try removing the helper module hp_wmi and then try to switch the wireless on with the key combination. 

You could also try:

```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list all
```

Second, check the user guide for your HP laptop and be certain that the wireless key combination you are using is correct. Be certain that you are not using Fn+F12, for example, if the user guide says it is simply F12. On the other hand, if you are certain you are using the correct sequence, try the wrong sequence as an experiment; i.e., use Fn+F12 (or whatever your sequence is) if the user guide says it’s F12 and vice versa.

Next, you can remove the card, tape off pin 20 and re-insert it: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

You can, if all these steps fail, file a bug report against the module hp_wmi: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Finally, in many, but not every case, a USB wireless will also be hard blocked for the same reasons. If you want to try one, be certain to try it within a return period.

I regret that there isn’t a better answer for HP laptops.


Possibly related: [https://askubuntu.com/questions/965595/why-does-airplane-mode-keep-toggling-on-my-hp-laptop-in-ubuntu-18-04/965596#965596](https://askubuntu.com/questions/965595/why-does-airplane-mode-keep-toggling-on-my-hp-laptop-in-ubuntu-18-04/965596#965596) By the way, if you have a newer Ubuntu version, you will need the systemd approach.

---

### Post by jjc55 on 2019-02-26
None of the above is working. I certainly appreciate the help though. I think I'm going to uninstall xubuntu and install Ubuntu in its place, if that's possible. ie: install Ubuntu over the top of xubuntu. Maybe that will cure my woes. Any suggestions would be welcome. Thanks again!

---

### Post by chili555 on 2019-02-26
> Maybe that will cure my woes.It almost certainly will not. You can test by running a live session; that is, Try Ubuntu, and press the wifi button to see if your wireless works. My guess is that it will not. Check before and after the button presses with:```
rfkill list all
```We will be interested in your report.

---

### Post by jjc55 on 2019-02-27
You're right, I tried Ubuntu instead of xubuntu and it most certainly did not cure my woes. 
rfkill list all:
0: phy0: Wireless LAN
               Soft blocked: no
               Hard blocked: yes
Ahhhh! Now what? Shall I accept defeat and come to terms with the fact that wifi in Ubuntu is just not going to happen with this machine; or are there other alternatives to try with this OS? Thanks for hanging in there chilli555.

---

### Post by chili555 on 2019-02-27
Did you check out this link I gave above? [https://askubuntu.com/questions/965595/why-does-airplane-mode-keep-toggling-on-my-hp-laptop-in-ubuntu-18-04/965596#965596](https://askubuntu.com/questions/965595/why-does-airplane-mode-keep-toggling-on-my-hp-laptop-in-ubuntu-18-04/965596#965596)

Let's see what the log says as you try the wifi key:```
tail -f /var/log/syslog
```Now press the key. Does syslog report key presses that it doesn't recognize? 

Get out of 'tail' with Ctrl+c.

May I assume that you didn't consider taping off the pin on the card?

---

### Post by jjc55 on 2019-02-27
You would be correct to assume that I haven't yet tried taping off the pin on the wireless card. I'm saving that for a last ditch effort. From what I saw in one of the links you posted it looks like a really tedious task. If I don't get this figured out by tonight I might give it a try. I have given every other suggestion a shot with no success. This includes the last command: 'tail'.  I also tried the last link you just sent me. With that though, I feel like I did something wrong in the process. After being instructed to save, it never really tells you how to move forward with the last set of commands. I messed around a bit until I was able to enter the commands and instruct the machine to restart, but in the process I feel like I may have voided all the previous command entries. I'd like to give that another shot because I have a feeling like it wants to work. If you would be willing to guide me through this one little step that would be great. Thanks... So after "control x", followed by y,  to confirm and save the text; exactly what is my next step to enter the final commands and reboot? I know this is probably such a simple thing that I should already know, and that I'm a bit naive. I surely apologize for that and thank you for your patience. Also, if you have any other tricks up your sleeve before I try to tape off the pin, I'm all ears. Thanks again.
Update:
I tried taping the pin with no success. I tried 4 or 5 different methods, all attempts were made with meticulous finesse and care. This thing is a STUBBORN little son of a gun.

---

### Post by chili555 on 2019-02-28
> I tried taping the pin with no success. Are you quite certain that you taped off the correct pin? Is your wireless card an M.2? [https://thecomputerperson.wordpress.com/2016/11/04/how-to-mask-off-the-wifi-power-off-pins-on-m-2-ngff-wireless-cards-the-old-mini-pci-pin-20-trick/](https://thecomputerperson.wordpress.com/2016/11/04/how-to-mask-off-the-wifi-power-off-pins-on-m-2-ngff-wireless-cards-the-old-mini-pci-pin-20-trick/)

Or is it a PCIe Mini or Micro? [http://www.allthingstechie.net/2014/10/bypass-laptop-wireless-hardware-radio.html](http://www.allthingstechie.net/2014/10/bypass-laptop-wireless-hardware-radio.html)

Are you quite sure you counted to pin 20 from the back? In many (most?) cases, pins 1-51 are on the front and pins 2-52 are on the back. Pin 20, an even numbered pin, would be counted from the back.

---

### Post by jjc55 on 2019-03-02
I have good news and bad news to report... I tethered my laptop to my phone and started doing some digging. While digging around, I stumbled upon this link: [https://github.com/agerwick/RT28XX-RT539X-Linux-driver](https://github.com/agerwick/RT28XX-RT539X-Linux-driver)   After following the instructions I was finally able to toggle off airplane mode. Unfortunately, my wifi card still isnt being detected after all that work. Another concern:The  rfkill list all command isnt listing anything at all now, it simply drops down to the next line so as to prepare for the next command. After several attempts and several other reboots, I still cant seem to get a wifi network card detection. With this new found knowledge; is there something else that you think may help? Maybe I'm missing something that can be solved easily now that you know airplane mode is no longer a permanent display. It seems as if I'm getting somewhere so I don't want to give up just yet. Thanks

---

### Post by chili555 on 2019-03-03
> After following the instructions I was finally able to toggle off airplane mode.Yes, yes indeed. If you installed a faulty driver and blacklist the current useful driver, the system won't recofnize any wireless device at all and therefore can't check the position of the rfkill switch, aka Airplane Mode.

In effect, you have solved the Low Oil problem in your car by removing the engine and hauling it to the junkyard. The dashboard no longer gives a Low Oil warning! Yippee!

Did you read and understand my post #8?> 
Installing different drivers will do precisely nothing to change the rfkill issue. Please revert these changes:> 
sudo nano /etc/modprobe.d/blacklist.conf

Add the following lines:

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta
To save and exit, press Ctrl-X, Y, Enter


Reboot and your wireless will reappear albeit with Airplane Mode stuck on.

---

### Post by jjc55 on 2019-03-05
I know, I know,  didn't listen. Haha,  My mother always said I had that problem when I was a kid. I apologize for that. So I did what you said. First though, I went back in and taped off what I'm fairly certain to be pin 20 this time,  this is a different pin than the last time I tried.  I then switched the machine on, opened the terminal and followed your instructions. Before I go any further, I must tell you that nobody ever really told me where to "add lines" after the "sudo nano /etc/modprobe.d/blacklist.conf"  command. As I stated before im a super naive newbie... Here's what happened: after typing in "sudo nano... " command, I added lines at the very top where the curser block first appeared blinking. It looks as though thats right where I typed in the last lines when I installed the new driver. I have no idea if I even did that right back then. So after that, I saved, enter, and rebooted. Nothing. I then deleted what I thought were the lines I added last time, leaving only the ones you told me to add. Save, reboot... Nothing. I then scrolled down to the bottom of the terminal and added them there where it said something about "amd", blah blah,  still nothing. I deleted them, and added them again under a line that said something about "network" something or other, all these are taking shots in the dark. Well, still nothing. Each time I checked "rfkill list all", It shows nothing. Still no airplane mode either. So under this sudo nano... Command I'm not sure if I'm supposed to be seeing all this text, but there's like 64 lines of it I think it said, which makes it difficult for me to know where I'm supposed to "add lines" when instructed. It would be a huge relief if someone could clue me in on that. Can I put screenshots on here?  Would that be helpful?  So anyway, not sure what my next move is before I tie a brick to this thing and kick it into a polluted river. Joking, now I'm actually more intrigued and determined to get to the bottom of this than ever. Even though I havent had any success I feel like I'm really learning from you here. As always, thanks, and especially a big thanks for your patience.
By the way, I Installed Ubuntu over xubuntu, mainly because I wasn't crazy about the xfce interface, among other reasons. I don't know if this makes any difference to you in your tutorials but I thought I should add that in here.

---

### Post by chili555 on 2019-03-05
Please run:```
cat /etc/modprobe.d/blacklist.conf
```And show us the result. I will give you a step-by-step to fix it.

While we wait, is there any effect if tou simply do:```
sudo modprobe rt2800pci
rfkill list all
```> 
I'm actually more intrigued and determined to get to the bottom of this than ever.
Me, too! Let's get this thing working!!!

---

### Post by jjc55 on 2019-03-06
cat /etc/modprobe.d/blacklist.conf
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta



# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# Causes trackpads to stop working on Lenovo 11e 2nd gen (Ubuntu: #1802135)
# and Lenovo x240 to hang on boot (Ubuntu: #1802689)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

```

You can see here at the bottom, as well as the top where I put the blacklist codes. Almost surely in the completely wrong place.

---

### Post by jjc55 on 2019-03-06
As for the next set of commands you requested: sudo modprobe rt2800pci and rfkill list all 

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

So I actually do get something doing it that way. Is there a better time that I should report back so as to possibly try to make this walk through closer to real-time? Maybe it would be easier if we could coordinate it that way. Just a thought. 
Quick edit: I'm happy to report that I am now back in airplane mode. Seems unusual to say that, but...

---

### Post by chili555 on 2019-03-06
> Hard blocked: yesPlease recheck your work. Pin 20 is not taped off.

Please do:```
sudo nano /etc/modprobe.d/blacklist.conf
```This entire file will open:```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
[COLOR="#FF0000"]blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta[/COLOR]



# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# Causes trackpads to stop working on Lenovo 11e 2nd gen (Ubuntu: #1802135)
# and Lenovo x240 to hang on boot (Ubuntu: #1802689)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
[COLOR="#FF0000"]blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta[/COLOR]

```Remove entirely the lines I've highlighted. Proofread carefully twice.

The file should now read:```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# Causes trackpads to stop working on Lenovo 11e 2nd gen (Ubuntu: #1802135)
# and Lenovo x240 to hang on boot (Ubuntu: #1802689)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```Write out the file with Ctrl+o followed by Enter. Exit nano with Ctrl+x.

---

### Post by jjc55 on 2019-03-06
EUREKA! We have found it! Success! (well, you have found it, I did nothing but mess it up the whole time) Airplane mode is off, toggle switch now lights up as blue instead of amber, and it is now showing available networks. Now I will attempt to connect to my wifi. Is there any further instructions, or are we finally finished? If the latter, then a huge thanks for hanging in there chilli555. You're a beast! Hats off my friend, hats off.
Update: I am happy to report that I am submitting this post with my newly working and connected wifi. Thanks again to chilli555!

---

### Post by jjc55 on 2019-03-07
Alas, I have celebrated too soon! Airplane mode stuck back on and no wifi detection. Ahh! Back to the old drawing board I suppose. At least it seems as though there's some glimmer of hope to be had here now that we know there was some sort of detection. I guess my only question now is: What is my next move?

---

### Post by chili555 on 2019-03-07
Does the button on the laptop respond to key presses now? Does the Airplane Mode button in Network Manager respond or does it flip right back to On? Any changes here?```
rfkill list all
```

---

### Post by jjc55 on 2019-03-08
Yeah, I tried all the tricks with the fn and WiFi buttons. Also, yes the Airplane Mode button in Network Manager flips right back to on when I click on it. I don't get it, it was working just fine when I followed your last set of instructions. I brought my laptop to work later that night, turned it on and it went right back to what it was doing when I first installed Ubuntu. So the glory only lasted about thirty minutes or so. Here is the reading for rfkill list all:

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

Update: A full day or two later upon posting the above code, wifi card randomly started working and is showing available wifi networks. Since starting this thread I have seen many complaints of the same nature. i.e. wifi adapter detection is unstable and airplane mode keeps switching on and off. At least we're heading in the right direction. Is there some sort of solution to this seemingly popular problem? Should I open the case back up and check to see that my tape job on pin 20 is secure, or is there a better solution?

---

### Post by jjc55 on 2019-03-11
After a four or five days my WiFi is apparently being detected randomly between restarts. Upon restart, when WiFi is detected, it will stay on throughout the entire session, regardless of how long or short the session is. Then, the very next reboot will automatically throw the machine back into airplane mode, every time, without fail. There's no telling when WiFi will start working again. Chili555, I haven't seen any recent posts from you on this thread in a while. Are we done here? Just curious. Thanks.

---

