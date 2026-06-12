---
title: "New speakers = no audio ???"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-12
I installed a wireless usb keyboard, mouse, and a pair of usb wired speakers....

the kb and mouse work ok but i have no volume...

when i first plugged in the speakers to a usb port there was a small indicator light that was on indicating power... i booted the pc and as soon as i was in 9.04 the light on the speakers was off...

this is logitech stuff if it matters for drivers ???

i found a similar thread after running a "no volume" search so i ran 3 commands and the results are below... i have no idea what is below but it might help ???

I re-booted and i still have no audio but the speakers do have power as the indicator light is now lit on the speakers.

thanks...



WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel




**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB  AUDIO  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

---

### Post by kostkon on 2009-07-12
You need to install the *PulseAudio Device Chooser* utility. Check [this helpful thread]("http://ubuntuforums.org/showthread.php?t=1130384") for more info.

---

### Post by austinpsycho on 2009-07-12
Or you could simply delete pulse audio.. that works too.  for some reason it makes usb audio not work under alsa.  after that if they still don't work, check your sound preferences *under system* switch one of the outputs to your usb speakers; and hit test; if that works, then open a terminal and type *asoundconf list* 
this will give you a list of audio devices.. then type
*asoundconf set-default-card nameOfCardHere*
then restart ;)

---

### Post by kostkon on 2009-07-12
> **austinpsycho said:**
> Or you could simply delete pulse audio.. that works too.  for some reason it makes usb audio not work under alsa.
Sorry, what?!

Anyway, NOTAGEEK just needs to set these USB speakers as the default output device in the *PulseAudio* volume control.

---

### Post by NOTAGEEK on 2009-07-13
> **kostkon said:**
> You need to install the *PulseAudio Device Chooser* utility. Check [this helpful thread]("http://ubuntuforums.org/showthread.php?t=1130384") for more info.



Interesting thread but way way above my skill level to work from... thanks anyway...

---

### Post by NOTAGEEK on 2009-07-13
> **austinpsycho said:**
> Or you could simply delete pulse audio.. that works too.  for some reason it makes usb audio not work under alsa.  after that if they still don't work, check your sound preferences *under system* switch one of the outputs to your usb speakers; and hit test; if that works, then open a terminal and type *asoundconf list* 
this will give you a list of audio devices.. then type
*asoundconf set-default-card nameOfCardHere*
then restart ;)


played around and have audio using usb audio (oss) but when i exit sound preferences/devices the audio is gone... works on tests though...  thanks...

---

### Post by kostkon on 2009-07-13
> **NOTAGEEK said:**
> Interesting thread but way way above my skill level to work from... thanks anyway...
It's simple, try this:
open *Synaptic*, search for* PulseAudio Device Chooser* (use the full search not the quick-search option) and install it.

Run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

Select the *Output Devices* tab. You should see your USB speakers listed there. Right-click on them and enable the *Default* option to make them the default output device in your system.

Or, you can on-the-fly send the sound of any application to your USB speakers in the *Playback* tab. Right-click on the audio stream you want to move and select *Move Stream...* and in the list that will appear select your speakers.

Hope that helps.

---

### Post by NOTAGEEK on 2009-07-13
> **kostkon said:**
> It's simple, try this:
open *Synaptic*, search for* PulseAudio Device Chooser* (use the full search not the quick-search option) and install it.

Run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

Select the *Output Devices* tab. You should see your USB speakers listed there. Right-click on them and enable the *Default* option to make them the default output device in your system.

Or, you can on-the-fly send the sound of any application to your USB speakers in the *Playback* tab. Right-click on the audio stream you want to move and select *Move Stream...* and in the list that will appear select your speakers.

Hope that helps.


I got through most of it then started listening to a radio station... after about a minute or so the radio quit and the speakers started screaming and would not stop... nothing i did would stop the speaker noise so i had to re boot to fix... audio almost working now but not... thanks...

---

