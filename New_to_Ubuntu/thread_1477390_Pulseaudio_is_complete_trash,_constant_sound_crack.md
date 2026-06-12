---
title: "Pulseaudio is complete trash, constant sound crackling on USB audio"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by El Lance-O on 2010-05-08
I have attempted to remove Pulseaudio SEVERAL times following several instructions posted on the forums, none of them work with Lucid. Developers have shoved Pulseaudio down our throats and are forcing us to use it without giving us the option to change to anything else.

Now that removed all Pulseaudio packages from my system, I cannot access the Sound management program under System > Preferences > Sound. I have read this is because of the hidden .pulse folder in the home folder needs to be deleted. I have attempted to delete this folder numerous times, and it keeps getting recreated, and the Sound program, still, will not open.

I have tried use gnome-alsamixer and alsamixergui to configure my system to work with these USB speakers, but there is no option for me to change output, I simply can only change the levels.

I am using a Logitech N700 lapdesk with built-in speakers. And yes, I know I have made a separate thread about this [here]("http://ubuntuforums.org/showthread.php?t=1472830"), but it is just being ignored and this is more directly a Pulseaudio issue.

Has anyone on Lucid had perfect success with removing Pulseaudio and getting ALSA to work properly? Please reply with any information you may have, I pretty much lost $60 over this lapdesk because of how horrible the crackling is. Renders movies completely unwatchable and some music is terrible, seems to me like an encoding issue.

Thanks so much ahead of time to those that actually take the time to help me, rather than ignore the issue and let Pulseaudio be forced upon us.

---

### Post by sandyd on 2010-05-08
can you do
```

cat /etc/asound.conf
```

---

### Post by nerdy_kid on 2010-05-08
to *disable* pulseaudio run (with pulseaudio installed of course)

```

sudo chmod -x /usr/bin/pulseaudio

```

i don't know how lucid will react to this (at least the GNOME lucid, kubuntu works fine).

also with pulseaudio, have you tried tweaking the values in /etc/pulse/daemon.conf? That very well might solve your issue, but i dont know very much about it other then to try tweaking these lines:

```

default-fragments = 8
default-fragment-size-msec = 10

```

---

### Post by El Lance-O on 2010-05-08
Thank you so much for the replies, I really appreciate it.

> **carlee said:**
> can you do
```

cat /etc/asound.conf
```


```
###@###:~$ cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory

```

I thought this was a bit weird, never deleted it that I know of, clean install.

> **nerdy_kid said:**
> 
[/CODE]
have you tried tweaking the values in /etc/pulse/daemon.conf? That very well might solve your issue, but i dont know very much about it other then to try tweaking these lines:

```

default-fragments = 8
default-fragment-size-msec = 10

```

I will try tweaking with those settings, but what increments should I toy with?

---

### Post by BT1 on 2010-05-08
Hey hey, Pulse isn't all bad. I have 10.04 in various flavors installed on 6 computers in my house from 10 year old Pentium 4 1.4's, to Netbooks, to Quad Cores, and I have yet to run into an issue with Pulse. People like who you say "THE WHOLE THING IS TRASH" instead of "It's not working for me" are ones who spread doubt and fear about stuff other people have yet to try. Next time please take a different approach. ;)

---

### Post by El Lance-O on 2010-05-08
Doing a quick forum search, or even a Google search, you'll see that "Pulseaudio doesn't work for me" is a gross understatement.

[http://www.webcitation.org/5kcZfOb4l](http://www.webcitation.org/5kcZfOb4l)

There is plenty of information out there with people having severe issues with Pulseaudio, and having it so hard-coded into the system so that the common user cannot easily fix simple audio problems with Pulseaudio by switching to ALSA or OSS, there arises a huge ethical problem with it being forced on us so harshly.

I have came across Pulseaudio problems on all 3 computers I have used with Ubuntu, including Ubuntu Studio issues with jackd that was completely related to Pulseaudio's bad development and complete lack of interest of fixing common bugs.

The fact that I have to post on the forums several times, try multiple guides to remove Pulseaudio that do not work, and tweak with several configurations to just get RID of it, is an issue. This is not what Ubuntu 10.04 should have been. There is nothing "LTS" worthy of such ignorance.

I know I could have gone about it better, but it still should be called to attention the direct flaws between the sound systems and whole infrastructure.

---

### Post by -humanaut- on 2010-05-08
PulseAudio has worked great on my system and an entire range of Computers that I've installed Lucid on Maybe your doing something wrong?

---

### Post by El Lance-O on 2010-05-08
If by using Pulseaudio completely with default settings you mean wrong, then yes, I am doing it all wrong.

I don't think having your sound crackle so bad that movies are completely unwatchable should be punishment for "doing it wrong".

---

### Post by nerdy_kid on 2010-05-09
> **El Lance-O said:**
> Thank you so much for the replies, I really appreciate it.




```
###@###:~$ cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory

```

I thought this was a bit weird, never deleted it that I know of, clean install.



I will try tweaking with those settings, but what increments should I toy with?

thats the part i really don't know :'(  Don't know very much about pulse, mainly how to disable/reenable it when i need to :D

---

### Post by El Lance-O on 2010-05-09
I've tried several different values in those fields, no luck. It seems to be either a system-wide encoding problem over USB audio, or a latency problem. I have no problems at all on my normal speakers, just the USB.

I'm going to do more experimenting and see what I can find. Thanks again for all the help, I really appreciate it.

Any other suggestions?

---

### Post by Sealbhach on 2010-05-09
I have to say Pulse Audio is working great in Lucid, for me. I had some problems with it in 9.10 but they all seem to have been ironed out - especially with sound in video games.

.

---

### Post by El Lance-O on 2010-05-09
I appreciate the response, but saying "What do you mean, it works fine for me!" isn't really helpful to my situation.

---

### Post by twisted_steel on 2010-05-09
Did you have this problem in an older version of Ubuntu, or did you just get the lapdesk?

---

### Post by El Lance-O on 2010-05-09
I just recently purchased the lapdesk. It works fine on Windows, OSX, and other distros.

---

### Post by twisted_steel on 2010-05-09
> **El Lance-O said:**
> I just recently purchased the lapdesk. It works fine on Windows, OSX, and other distros.

Well if it works fine with other distros, it definitely sounds like something is messed up with the support in Ubuntu.  Unfortunately, I don't really know much about troubleshooting audio.  Until someone comes around with a fix, I would file a bug.  I looked through the sound troubleshooting page and didn't see anything that applies.  I did notice in your other thread that you were still hearing crackling with alsa selected in gstreamer-properties.  That doesn't sound good.

Anyway, these are the two pages I started looking at, but did not find much other than how to get information for a bug report:
1. [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
2. [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by alphacrucis2 on 2010-05-09
May be nothing to do with pulseaudio. Perhaps the driver Lucid has installed for your USB headset is the problem. I have actually seen very few issues with pulseaudio reported for Lucid. Different story if you go back to Jaunty or the early days of Karmic. 

I suspect it is going to get more difficult to take pulseaudio out without breakage as it seems more and more things assume it will be there. IIRC you can't run the later versions of Skype without it.

---

### Post by El Lance-O on 2010-05-09
Really? See that I think is the issue here, Pulseaudio is being forced onto us, instead of being able to keep the options open.

How would I go about seeing what drivers the lapdesk uses, or to change them? I'm not too savvy on that.

The speakers work GREAT sometimes, depending on if it's flash video, or for example .mp4 video works just fine. But the majority of the time, the crackling is still there.

I agree it may not be Pulseaudio direcly, but more of a conflict because Pulseaudio is so hard-coded into everything now, which I think is a huge mistake on the developers part.

Thanks again for the support, I really can't wait to get this resolved so that I may watch movies on these great speakers, and not have wasted a good $60.

---

### Post by El Lance-O on 2010-05-09
I have no idea if this worked or not, but I think I fixed it.

I unplugged the USB speakers, and tried using it in different USB ports, no difference. In the process I unplugged my external.

When I plugged the external in, as soon as it was remounted, the crackling stopped. I'm going to do some further testing to confirm this.

Edit: When works fine for a bit, but as soon as I play a video it works fine for a minute, then starts crackling again. USB latency conflict?

Edit #2: Again, it's going back to crackling SEVERELY as soon as I play a video, now I'm back to thinking it's an encoding issue over USB.

---

### Post by twisted_steel on 2010-05-09
> **El Lance-O said:**
> How would I go about seeing what drivers the lapdesk uses, or to change them? I'm not too savvy on that.

From the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") page:

Run "lspci -v | less" in a terminal and look for Audio device.  At the bottom of that section, you should find a "Kernel modules" line.  It should have the driver (or drivers) listed.

For example, this is what my onboard sound card looks like:
```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at ea100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

---

### Post by alphacrucis2 on 2010-05-09
> **El Lance-O said:**
> Really? See that I think is the issue here, Pulseaudio is being forced onto us, instead of being able to keep the options open.

How would I go about seeing what drivers the lapdesk uses, or to change them? I'm not too savvy on that.

The speakers work GREAT sometimes, depending on if it's flash video, or for example .mp4 video works just fine. But the majority of the time, the crackling is still there.

I agree it may not be Pulseaudio direcly, but more of a conflict because Pulseaudio is so hard-coded into everything now, which I think is a huge mistake on the developers part.

Thanks again for the support, I really can't wait to get this resolved so that I may watch movies on these great speakers, and not have wasted a good $60.

One thing you can do is open up the Log File Viewer under System - Administration. Select the syslog. Then plug in the USB device. You should see a number of kernel messages pop up as it detects the new USB device and loads a driver for it.

---

### Post by El Lance-O on 2010-05-09
Couldn't seem to find it with the lscpi command.

```
May  9 18:44:07 ##### kernel: [ 6310.652086] usb 3-1: new full speed USB device using uhci_hcd and address 11
May  9 18:44:08 ##### kernel: [ 6310.860398] usb 3-1: configuration #1 chosen from 1 choice
May  9 18:44:08 ##### kernel: [ 6310.927870] input: Logitech Logitech Speaker Lapdesk N700 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/input/input22
May  9 18:44:08 ##### kernel: [ 6310.928690] generic-usb 0003:046D:0A1A.000D: input,hidraw0: USB HID v1.00 Device [Logitech Logitech Speaker Lapdesk N700] on usb-0000:00:1d.1-1/input2
```

---

### Post by twisted_steel on 2010-05-09
> **El Lance-O said:**
> Couldn't seem to find it with the lscpi command.

```
May  9 18:44:07 ##### kernel: [ 6310.652086] usb 3-1: new full speed USB device using uhci_hcd and address 11
May  9 18:44:08 ##### kernel: [ 6310.860398] usb 3-1: configuration #1 chosen from 1 choice
May  9 18:44:08 ##### kernel: [ 6310.927870] input: Logitech Logitech Speaker Lapdesk N700 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/input/input22
May  9 18:44:08 ##### kernel: [ 6310.928690] generic-usb 0003:046D:0A1A.000D: input,hidraw0: USB HID v1.00 Device [Logitech Logitech Speaker Lapdesk N700] on usb-0000:00:1d.1-1/input2
```

Sorry about that; it would make sense that that would fail, as the command looks for PCI devices, not USB devices :(

Here's another random command since lsusb has way too much information.  Try "hal-device | less" and look for "driver".  You can search with "/" and typing "driver" and hitting enter.  For example, here is my USB card in place:

```

7: udi = '/org/freedesktop/Hal/devices/usb_device_8bb_2902_noserial_if1'
  usb.device_class = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor_id = 2235  (0x8bb)  (int)
  usb.product_id = 10498  (0x2902)  (int)
  usb.vendor = 'Texas Instruments Japan'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.product = 'USB Audio Interface'  (string)
  usb.num_ports = 0  (0x0)  (int)
  linux.subsystem = 'usb'  (string)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.is_self_powered = false  (bool)
  usb.speed = 12  (double)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.can_wake_up = false  (bool)
  info.subsystem = 'usb'  (string)
  usb.version = 1.1  (double)
  usb.bus_number = 6  (0x6)  (int)
  usb.interface.number = 1  (0x1)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8bb_2902_noserial'  (string)
  usb.interface.class = 1  (0x1)  (int)
  usb.interface.subclass = 2  (0x2)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  **info.linux.driver = 'snd-usb-audio'  (string)**
  info.product = 'USB Audio Interface'  (string)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1'  (string)
  usb.num_configurations = 1  (0x1)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8bb_2902_noserial_if1'  (string)

```

---

### Post by El Lance-O on 2010-05-09
```
7: udi = '/org/freedesktop/Hal/devices/usb_device_46d_a1a_noserial_if1'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  info.linux.driver = 'snd-usb-audio'  (string)
  info.subsystem = 'usb'  (string)
  info.product = 'USB Audio Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_a1a_noserial_if1'  (string)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 3  (0x3)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.product_id = 2586  (0xa1a)  (int)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.product = 'USB Audio Interface'  (string)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.linux.device_number = 17  (0x11)  (int)
  usb.speed = 12  (double)
  usb.version = 2  (double)
  usb.max_power = 500  (0x1f4)  (int)
  usb.can_wake_up = false  (bool)
  usb.bus_number = 3  (0x3)  (int)
  usb.is_self_powered = false  (bool)
  usb.interface.number = 1  (0x1)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_a1a_noserial'  (string)
  usb.interface.subclass = 2  (0x2)  (int)
  usb.interface.class = 1  (0x1)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
```

---

### Post by El Lance-O on 2010-05-09
Again, I will confirm that unplugging and replugging in my external corrects the issue, until I play a video that is not .mp4.

This is seriously, mind-boggling.

---

### Post by El Lance-O on 2010-05-10
bump

I was getting some great help, I know there is someone out there that has an answer...:confused:

---

### Post by alphacrucis2 on 2010-05-10
> **El Lance-O said:**
> bump

I was getting some great help, I know there is someone out there that has an answer...:confused:

Be patient. At this point I think we need an expert to come along as your situation seems rather bizare. I tried to reproduce but I don't have the same hardware setup as you. My USB headset (not speakers like you have) remain working fine after playing flash movies

---

### Post by gradinaruvasile on 2010-05-10
> **alphacrucis2 said:**
> May be nothing to do with pulseaudio. Perhaps the driver Lucid has installed for your USB headset is the problem. I have actually seen very few issues with pulseaudio reported for Lucid. Different story if you go back to Jaunty or the early days of Karmic. 

I suspect it is going to get more difficult to take pulseaudio out without breakage as it seems more and more things assume it will be there. IIRC you can't run the later versions of Skype without it.

Skype works perfectly fine without PulseAudio. In fact it uses less CPU and it is more stable with just ALSA.

To the OP:

What movie player do you use for playback? In vlc, smplayer, xine etc you have the opton to explicitly use PulseAudio as the sound out device. Letting the devices on "default" sometimes might mess up things.

For gstreamer sounds (totem,rhytmbox etc) press alt+f2 and type "gstreamer-properties" press enter. Set default input+output to PulseAudio server. This may help.

Also, i use bluetooth handsfree sometimes via PulseAudio on my laptop - al programs have higher (+~20%) CPU usage when playing the sounds through it - the pulseaudio process itself doesnt eat much CPU.
Start the movie, open a terminal and type "top" then enter - see if you have high CPU usage - try it once with the USB sound ant then with the internal to see if there is a difference.

---

### Post by El Lance-O on 2010-05-10
It's not even just flash movies, but videos of any kind really. Even rotating the cube with Compiz triggers it, it seems to be a system-wide bug of some kind.

---

### Post by El Lance-O on 2010-05-20
> **gradinaruvasile said:**
> Skype works perfectly fine without PulseAudio. In fact it uses less CPU and it is more stable with just ALSA.

To the OP:

What movie player do you use for playback? In vlc, smplayer, xine etc you have the opton to explicitly use PulseAudio as the sound out device. Letting the devices on "default" sometimes might mess up things.

For gstreamer sounds (totem,rhytmbox etc) press alt+f2 and type "gstreamer-properties" press enter. Set default input+output to PulseAudio server. This may help.

Also, i use bluetooth handsfree sometimes via PulseAudio on my laptop - al programs have higher (+~20%) CPU usage when playing the sounds through it - the pulseaudio process itself doesnt eat much CPU.
Start the movie, open a terminal and type "top" then enter - see if you have high CPU usage - try it once with the USB sound ant then with the internal to see if there is a difference.

Sorry for the delayed reply.

I have tried VLC, Totem, AND Mplayer will all the same results. I did what you suggested, and still, problems arise. No CPU use increase whatsoever.

It has gotten to the point where when I start Ubuntu, I have to manually start pulseaudio before I can even access my sound options, and the volume jumps erratically when I change it. Sometimes it will not work properly, and only Dummy Audio shows up under output, rendering sound VERY quiet.

I'm really at a loss here, and it's driving me NUTS. It's been over a week that I still haven't been able to solve this, and it really sucks not being able to use my brand new speakers. They sound AMAZING without the popping and crackling.

Please someone help? :confused:

---

### Post by lidex on 2010-05-20
Can you post the output of this command please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by El Lance-O on 2010-05-21
Absolutely. :)

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```

---

### Post by lidex on 2010-05-21
OK. Now this:
```
lsusb | grep snd
```

And this;
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by El Lance-O on 2010-05-21
'lsusb | grep snd' provides no information.

```
2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: N700 [Logitech Speaker Lapdesk N700], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).
```

```
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9200

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa

```

---

### Post by lidex on 2010-05-21
> **El Lance-O said:**
> 'lsusb | grep snd' provides no information.



Yeah...I wonder why :oops:
Should be:
```
lsmod | grep snd
```

---

### Post by El Lance-O on 2010-05-21
Haha, no wonder! Silly you.

```
snd_hda_codec_idt      53061  1 
snd_hda_intel          20288  3 
snd_usb_audio          75954  0 
snd_usb_lib            16130  1 snd_usb_audio
snd_hda_codec          79300  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5668  2 snd_usb_audio,snd_hda_codec
snd_seq_dummy           1498  0 
snd_pcm_oss            34571  0 
snd_mixer_oss          13929  1 snd_pcm_oss
snd_seq_oss            27626  0 
snd_seq_midi            4621  0 
snd_pcm                71265  4 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss
snd_rawmidi            19141  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48106  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18720  2 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55939  22 snd_hda_codec_idt,snd_hda_intel,snd_usb_audio,snd_usb_lib,snd_hda_codec,snd_hwdep,snd_seq_dummy,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_seq_midi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm

```

---

### Post by lidex on 2010-05-21
Are you using onboard sound at all? It kinda sounds like the problematic files are trying to access your other device, hence the hotplugging of usb device restores sound. Wait a sec:
> I unplugged the USB speakers, and tried using it in different USB ports, no difference. In the process I unplugged my external.
When I plugged the external in, as soon as it was remounted, the crackling stopped.
What is the "External"? USB HDD? So the sound is corrected then but not with re-plugging lapdesk? What happens with the external disconnected and a reboot? Are these devices plugged into the PC or a hub?

You stated you removed pulse. Did you re-install it or are you trying to use alsa?

---

### Post by Psyphre on 2010-05-21
I had a similar issue when i reinstalled ubuntu (used to disable it in Jaunty), but I decided to keep it when I installed Lucid.

I would get crackles from time to time (usually when some load was put on the CPU/GPU - like rotating the cube as you mentioned). It's completely gone now, and I can't remember what solved it, but I do remember changing the volume in pulse audio (it's 100% on default). If you look at the pulse audio sound properties, you will see 2 notches; '100%' and 'unamplified'. I've set it on unamplified and I'm quite sure that's what stopped the crackling and hissing.

I do agree it's ridiculous how hard they've made it for people to use anything else besides pulseaudio.

---

### Post by El Lance-O on 2010-05-21
> **lidex said:**
> Are you using onboard sound at all? It kinda sounds like the problematic files are trying to access your other device, hence the hotplugging of usb device restores sound. Wait a sec:

What is the "External"? USB HDD? So the sound is corrected then but not with re-plugging lapdesk? What happens with the external disconnected and a reboot? Are these devices plugged into the PC or a hub?

You stated you removed pulse. Did you re-install it or are you trying to use alsa?

No, unplugging does not seem to make a different. It SEEMED that way at first, but it started again and still does not stop.

I TRIED getting rid of Pulseaudio, but then I was unable to set the Lapdesk as my audio device because I cannot access Sound settings after removing Pulse, it sits there saying "Waiting for Audio Devices" or something to that extent until I manually run Pulseaudio. I have to do this every time I start up now.

---

### Post by lidex on 2010-05-21
Make sure all these packages are installed (excepting bluetooth - unless needed).
See screen, this is from synaptic.

---

### Post by El Lance-O on 2010-05-22
Yup, all installed, problems are still here.

I'm pretty close to just giving up on 10.04 and downgrading to see if that fixes the problem. I kinda feel like this release was really rushed, and many details overlooked.

---

### Post by lidex on 2010-05-22
I am leaning toward sampling rate as the culprit.
[http://ubuntuforums.org/showthread.php?t=662043]("http://ubuntuforums.org/showthread.php?t=662043")

---

### Post by El Lance-O on 2010-05-23
That's what I thought it was! I've had sampling rate issues with Ubuntu Studio in the past, and this was VERY similar.

But, how do I change those settings? That thread did not help because it is very outdated, there is no asoundconf in the repositories, and I do not have a /etc/asound.conf file to edit the sampling rates.

SO CLLOOOSSEEE!!!! :P

---

### Post by twisted_steel on 2010-05-23
> **El Lance-O said:**
> That's what I thought it was! I've had sampling rate issues with Ubuntu Studio in the past, and this was VERY similar.

But, how do I change those settings? That thread did not help because it is very outdated, there is no asoundconf in the repositories, and I do not have a /etc/asound.conf file to edit the sampling rates.

SO CLLOOOSSEEE!!!! :P

Check out the third post: [http://ubuntuforums.org/showthread.php?t=989456](http://ubuntuforums.org/showthread.php?t=989456).  I see the line set to defaults (commented out) in my daemon.conf, so the file should be there for you as well.

[EDIT]
Actually, a few posts later it says that you can set a file in your home directory with the settings rather than risk updates changing your daemon.conf back to defaults.

---

### Post by lidex on 2010-05-23
pssst...[http://ubuntuforums.org/showthread.php?t=1348604]("http://ubuntuforums.org/showthread.php?t=1348604")

---

### Post by El Lance-O on 2010-05-25
Ok just wait a second before I start adding MORE dirty hacks to my system.

I now have no start-up sounds at all. The volume control buttons on my laptop now only work to turn it down, not up. When I manually start Pulseaudio (I have to every time I boot now), and go the Sound properties, there is a section between 'unamplified' and '100%'. At unamplified, it is hardly audible, at 100%, it is painfully loud. There is no way to set it anywhere between, I have to set the volume within each program specifically to get a decent level. This is only for the lapdesk, the sound level is fine on my normal speakers, but the other issues still exist.

Not only that, but once I changed the sampling rate to 48000, now only the right speaker works on my lapdesk. So far, I have mangled my sound to the point that it cannot do something as simple as volume control, system sounds, and play through both speakers. And the crackling is still there. I have to manually start Pulseaudio for most things to work, and this is just getting ridiculous.

Seriously, what will asoundconf do that everything else has not? Because if it will fix these problems, I am all for it. But if it is just going to further damage my system as everything has so far, I think I will just call my losses, and give up honestly. This is getting to the point where it is infringing on everything else from working properly.

Please someone help with my existing issues, this is getting absolutely ridiculous. And thanks again lidex, you've been a HUGE help so far, I really appreciate it.

---

### Post by El Lance-O on 2010-08-14
Well I solved the problem. Guess what it was?

[SIZE="4"]COMPIZ![/SIZE] :lolflag:

No joke, disabling compiz makes my speakers stop crackling for some reason.  Oh well, I guess I just can't use compiz anymore.

---

### Post by lidex on 2010-08-14
> **El Lance-O said:**
> Well I solved the problem. Guess what it was?

[SIZE="4"]COMPIZ![/SIZE] :lolflag:

No joke, disabling compiz makes my speakers stop crackling for some reason.  Oh well, I guess I just can't use compiz anymore.
That's interesting...I'd like to know the connection.

---

### Post by HermanAB on 2010-08-14
Howdy,

Pulse Audio is layered on top of ALSA.  If the ALSA levels are wrong, then no amount of fiddling with Pulse will fix things.

The crackling problem is usually caused by the PCM input being set to maximum (I don't think anything ever use the PCM input).  Run Gnome ALSA Mixer and set PCM to zero, all other levels to maximum, unmute all outputs and set Rec (to unmute the Mic).  Your Pulse-Audio should now work properly.

To make sure that the ALSA levels stick, save them with:
$ sudo alsactl store.

---

### Post by El Lance-O on 2010-08-16
Um...you obviously didn't read my last post.

It's compiz that is producing the crackling. Why, I have no idea. Trust me I have already tried fiddling with ALSA settings, no effect.

---

### Post by simosx on 2010-08-16
> **El Lance-O said:**
> Um...you obviously didn't read my last post.

It's compiz that is producing the crackling. Why, I have no idea. Trust me I have already tried fiddling with ALSA settings, no effect.

Thanks for getting down to the end of this. Many people simply blame PulseAudio and try to uninstall it.

Why would your sound misbehave when you have Compiz enabled?

It could be an issue with your graphics hardware where the CPU takes a bit too much processing power so that PulseAudio gets often buffer underruns.
You can try to run some program that takes up a bit of CPU and see if your sound continues to work.

Or, your graphics setup is such that compiz needs to take up exclusive time from the system. Systems such as PulseAudio need constantly small amounts of CPU to playback/record, so if for ½ second there is no CPU given to PulseAudio (because the graphics card hogs the CPU) you get a cruckling sound.

You may give your graphics card details plus driver in case a member gets a similar problem. You can do this with

[FONT="Courier New"]sudo lshw -class display -numeric[/FONT]

---

### Post by gradinaruvasile on 2010-08-16
> **HermanAB said:**
>  Run Gnome ALSA Mixer and set PCM to zero, all other levels to maximum, unmute all outputs and set Rec (to unmute the Mic). 

Ummm... PCM controls the volume on all Ubuntu/Debian systems i have seen (ALC655, C-Max Media, MCP78S, ICH7-8 etc cards). Setting it to 0 will kill the playback volume completely.

You maybe have a PCM on the capture tab or gnome alsa mixer has different controls compared to alsamixer?

---

### Post by HermanAB on 2010-08-16
Well, since you run Ubuntu, which defaults to Gnome, why don't you  run Gnome ALSA Mixer and have a look?

This gives a zillion hits to the problem:
[https://encrypted.google.com/search?q=ALSA+PCM+crackle](https://encrypted.google.com/search?q=ALSA+PCM+crackle)

Anyhoo, the prblem has nothing to do with Pulse Audio.  It is the Ubuntu ALSA default settings that are wrong.

---

### Post by pagoogle on 2010-12-30
How do you get the sound to go through the Logitech lapdesk speakers? When I run the test on the sound preferences, after choosing "usb audio" from each list, i hear the test beep fine. But that's the only time I get sound through the lapdesk speakers.

I have a Dell Insirion 910 with Ubuntu 8.04    ):P

Nevermind, found a soln in this older thread: [http://ubuntuforums.org/showthread.php?t=937398](http://ubuntuforums.org/showthread.php?t=937398)

---

