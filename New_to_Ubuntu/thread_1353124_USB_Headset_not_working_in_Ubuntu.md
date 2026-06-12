---
title: "USB Headset not working in Ubuntu"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-12-12
Hi All,

I'm having Logitech USB Headset. As soon as If I connect the headset Ubuntu login sound I can here on the headset. After that when I try to play songs I'm not able to here any sound from my USB Headset. Instead of using my headset If I connect to normal speakers sound is coming without any problem. Do I need to do anything in Ubuntu to make USB headset work. Please anyone help me on this.

I'm using Ubuntu LTS (8.04)
Kernal Version 2.6.24-26-generic

---

### Post by ufarmer on 2009-12-12
Hi,

I too am trying to get a Logitech Premium Notebook Headset to work with Ubuntu 9.04.  According to some posts in other forums it's supposed to be possible but nobody has posted a comprehensive how to.  If I look in System-->Preferences-->Sound I see that the device is being detected (it is plugged in to a USB port).  When I test sound play back I can hear the test sound; however sound capture only picks up very faint sounds from the microphone.  When I am on skype I get absolutely nothing from either the speakers or the microphone.

A headset like this doesn't seem it should be so difficult to operate.  Any advice is appreciated.

---

### Post by ufarmer on 2009-12-12
So it turns out that it's just when the headset is plugged in as a USB that it doesn't function.  When it's plugged into the regular jacks (analog?) it works fine.  I have no idea why this would be the case.

---

### Post by 3rdalbum on 2009-12-12
Ubuntus 8.04 and 9.04 need an extra utility called 'padevchooser' to properly select sound input and output devices. This utility should be in Synaptic Package Manager.

Install it and add the 'padevchooser' command to your startup programs. It adds a new icon to your notification area that lets you set up inputs and outputs for your programs.

Ubuntu 9.10s volume control already contains this functionality.

---

### Post by keenansnews on 2009-12-12
You may want to open Pulse Audio Volume Control and move the stream to your usb device.  If you need more specific instructions, just say so.

---

### Post by vipin.balakrishnan on 2009-12-12
Hi All,
 
Please anyone gave me answer for my problem

---

### Post by frenchn00b on 2009-12-13
> **3rdalbum said:**
> Ubuntus 8.04 and 9.04 need an extra utility called 'padevchooser' to properly select sound input and output devices. This utility should be in Synaptic Package Manager.

Install it and add the 'padevchooser' command to your startup programs. It adds a new icon to your notification area that lets you set up inputs and outputs for your programs.

Ubuntu 9.10s volume control already contains this functionality.
  
You do not need padevchooser !! that's an error.

For 3rdalbum, please do ```
man alsa
```
  
You do not solve this with another software when it is available in alsa by default.

here is how to change cards, of swap them to get sounds:
[http://forums.debian.net/viewtopic.php?f=17&t=47477](http://forums.debian.net/viewtopic.php?f=17&t=47477)

Please post:

```
cat  /etc/modprobe.d/alsa-base
```

```
lsmod
```

then your  /etc/modprobe.d/sound.conf will have to be modified based on hte running modules:

I have this:
```
 ## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-pcsp
alias snd-card-1 snd-usb-audio

## module options should go here
#options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1
options snd-pcsp index=0 
```

---

### Post by Primefalcon on 2009-12-13
Just right click on the speaker icon in your taskbar above and select sound preferences, select output

you'll have 2 options probably

first will be internal and the second will be sound adapter or such.....

one will be your speakers one will be your headphones, select what you will and adjust the volume and enjoy

---

### Post by 3rdalbum on 2009-12-13
> **frenchn00b said:**
> You do not need padevchooser !! that's an error.

For 3rdalbum, please do ```
man alsa
```
  
You do not solve this with another software when it is available in alsa by default.

here is how to change cards, of swap them to get sounds:
[http://forums.debian.net/viewtopic.php?f=17&t=47477](http://forums.debian.net/viewtopic.php?f=17&t=47477)

Please post:

```
cat  /etc/modprobe.d/alsa-base
```

```
lsmod
```

then your  /etc/modprobe.d/sound.conf will have to be modified based on hte running modules:

I have this:
```
 ## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-pcsp
alias snd-card-1 snd-usb-audio

## module options should go here
#options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1
options snd-pcsp index=0 
```

There is no manual page for Alsa. And this seems a lot harder and a lot less flexible than Pulseaudio Device Chooser. This is Absolute Beginner Talk.

---

### Post by vipin.balakrishnan on 2009-12-14
Hi frenchn00b[]("http://ubuntuforums.org/member.php?u=450766"),

  Thank you for replying.  Can you Please explain me little more clear. Because I'm very new to Linux.

---

### Post by LowSky on 2009-12-14
You should be able to click on the sound icon on the top right of your screen. go to preferences or settings or whatever (sorry Im on Windows right now, and  use 9.10 at home so its a bit hazy... anyway there should be an option to change the input/output

> **vipin.balakrishnan said:**
> Hi frenchn00b[]("http://ubuntuforums.org/member.php?u=450766"),

  Thank you for replying.  Can you Please explain me little more clear. Because I'm very new to Linux.


Open the program called Terminal, it under accessories under the application tab. Most the Code boxes the frenchn00b used require you to enter the text in terminal
 Just try to folow his directions carefully, they are pretty staight forward.

> **frenchn00b said:**
> You do not need padevchooser !! that's an error.

For 3rdalbum, please do ```
man alsa
```
  
You do not solve this with another software when it is available in alsa by default.

here is how to change cards, of swap them to get sounds:
[http://forums.debian.net/viewtopic.php?f=17&t=47477](http://forums.debian.net/viewtopic.php?f=17&t=47477)

Please post:

```
cat  /etc/modprobe.d/alsa-base
```

```
lsmod
```

then your  /etc/modprobe.d/sound.conf will have to be modified based on hte running modules:

I have this:
```
 ## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-pcsp
alias snd-card-1 snd-usb-audio

## module options should go here
#options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1
options snd-pcsp index=0 
```

---

### Post by vipin.balakrishnan on 2009-12-14
Hi

  I dont have file called '/etc/modprobe.d/sound.conf' .But if I search under the directory I can find a file called alsa-base. I have pasted the content of that file here

> 

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388



I dont find anything simlar in these things

Can you please tell me what to do next.

---

### Post by frenchn00b on 2009-12-14
> **frenchn00b said:**
> You do not need padevchooser !! that's an error.

For 3rdalbum, please do ```
man alsa
```
  
You do not solve this with another software when it is available in alsa by default.

here is how to change cards, of swap them to get sounds:
[http://forums.debian.net/viewtopic.php?f=17&t=47477](http://forums.debian.net/viewtopic.php?f=17&t=47477)

Please post:

```
cat  /etc/modprobe.d/alsa-base
```

```
lsmod
```

then your  /etc/modprobe.d/sound.conf will have to be modified based on hte running modules:

I have this:
```
 ## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-pcsp
alias snd-card-1 snd-usb-audio

## module options should go here
#options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1
options snd-pcsp index=0 
```

so your PC has those ways to play the sound:
```
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options  mpu_port=0x330 fm_port=0x388
```

eg. snd-cmipci
shall be instead of snd-pcsp in my file below:

or you can try all possibilites, and force restart. I am not expert, but it is tehre almos thte solution to your issue.

```
 ## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-pcsp
alias snd-card-1 snd-usb-audio

## module options should go here
#options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1
options snd-pcsp index=0 
```
 
I am not expert, but it is the solution tehre. : 
 /etc/modprobe.d/sound.conf
or ask simply per emails the coders of ALSA, they are very friendly and will be very glad to help you. 
alsa sourceforge

let us know please about your progresses. We are intending all our best to make you succeed in your sound issue.

---

### Post by keenansnews on 2009-12-14
I've never did this for USB headsets, but I have done it for USB speakers, but it should world in principle the same way.  

You need to go to go to your menu and find **Pulse Audio Volume Control**(Do not choose the selected item in this pic, choose the one below it, *Pulse Audio Volume Control*).  [Link]("http://equima.pfpfree.net/wp-content/uploads/2009/11/Select-Pulseaudio-Dev-Chooser.png")

If you have chosen **Pulse Audio Volume Control**, a window will appear that looks like this : [link]("http://tombuntu.com/wp-content/uploads/2008/04/pavucontrol.jpg")

Notice that there is an **Input** tab as well as an **Output** tab and a **Playback** tab.  You **Output** is where the audio stream of your mic to go.  Your **Input** is what audio stream you want to come into your headset.  On the input/ouput tabs there are three buttons for each device.  There is a speaker button, a lock button, and disclosure "v" symbol.  You are going to want to pay attention to the "v" button.  This is the one that will allow you to "move streams".

Plug in your USB headset.  Click through the tabs.  Pay attention to all the buttons.  Use your common sense to determine where to move streams.

For exmaple, if you have music playing, you will want to first find that music stream, then pick the "v" button, and it will give you the option of moving that stream to the usb headset.  If you are using a internet phone or audio chat, that audio stream could also be move to the headset through the **Pulse Audio Volume Control**.

I'm guessing you should be able to use common sense to get your headset working from these basic ideas of moving input and output streams to where you want them.

---

### Post by 3rdalbum on 2009-12-14
Editing the basic configuratiom of your sound system is NOT NECESSARY.

You need to install the 'padevchooser' program from Synaptic Package manager. Hit Alt-F2 and type 'padevchooser' and this will put a new icon into your notification area. Left click it and choose Volume Control and go to the Input tab. It shows you the current programs that are using sound input. 

Click the little arrow to the right of the program you want to use your headset with. This opens a popup menu where you can 'move stream' to your headset.

Go to the Output tab and do the same thing.

Note that with Skype, you may need to do the Test Call before it appears in the Input list.

---

### Post by frenchn00b on 2009-12-14
> **keenansnews said:**
> I've never did this for USB headsets, but I have done it for USB speakers, but it should world in principle the same way.  

You need to go to go to your menu and find **Pulse Audio Volume Control**(Do not choose the selected item in this pic, choose the one below it, *Pulse Audio Volume Control*).  [Link]("http://equima.pfpfree.net/wp-content/uploads/2009/11/Select-Pulseaudio-Dev-Chooser.png")

If you have chosen **Pulse Audio Volume Control**, a window will appear that looks like this : [link]("http://tombuntu.com/wp-content/uploads/2008/04/pavucontrol.jpg")

Notice that there is an **Input** tab as well as an **Output** tab and a **Playback** tab.  You **Output** is where the audio stream of your mic to go.  Your **Input** is what audio stream you want to come into your headset.  On the input/ouput tabs there are three buttons for each device.  There is a speaker button, a lock button, and disclosure "v" symbol.  You are going to want to pay attention to the "v" button.  This is the one that will allow you to "move streams".

Plug in your USB headset.  Click through the tabs.  Pay attention to all the buttons.  Use your common sense to determine where to move streams.

For exmaple, if you have music playing, you will want to first find that music stream, then pick the "v" button, and it will give you the option of moving that stream to the usb headset.  If you are using a internet phone or audio chat, that audio stream could also be move to the headset through the **Pulse Audio Volume Control**.

I'm guessing you should be able to use common sense to get your headset working from these basic ideas of moving input and output streams to where you want them.
 
thank you for this howto with screenshots. Even me, I was not capable to do it with this new tool, stick to alsa as prehistoric, as default. Although I am wondering if we are going good playing around with pulse audio. Pulse is for pulsing audio, well, some years ago.

---

