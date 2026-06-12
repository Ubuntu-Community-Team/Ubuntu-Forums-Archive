---
title: "Can't hear my guitar through Rakarrack"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by zangler on 2010-12-23
I installed Ubuntu Studio 10.10 yesterday as I want to use Rakarrack with my usb guitar and then record some guitar and other audio tracks using Ardour.  I can't get any output from Rakarrack and have struggled to get any sound at all out of the system.  I am very new to Ubuntu and don't know where to start troubleshooting.  I have a soundblaster live soundcard installed.  I have had a read through some posts on these forums to try to resolve it, but I can't seem to follow many of the instructions... they are still a bit over my head.  I'd really appreciate it if some kind soul could offer me a little help.  Many thanks.

---

### Post by stelloscuro on 2010-12-23
Try reading up on Jack, it is like a virtual patchbay, among other things

---

### Post by zangler on 2010-12-23
I've been reading up on JACK and I stumble at the first fence.  Looking at the community documents, there is an item "HowToJACKConfiguration" at [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration) In the first few sentences it refers to "Now, open up QjackCtl..."

What is this and where can I find it?

---

### Post by cchhrriiss121212 on 2010-12-23
Hi
What you need to do is go to Applications>Sound and Video>JACK Control AKA qjackctl. It is the user interface for the jack sound server. Jack allows you to connect your audio together manually at a low latency. 

First, enter the setup window and select your soundblaster card as the interface. Now press OK and try pressing start on the main window. The setup window has many options, but you can use the default settings for now.

If it runs OK, open up patchage and make a note of what ports you can see, these will be the inputs and outputs of your soundcard. If you open a sound program like Rakarrack you will see new ports appear which you can connect your soundcard to.

Note: Patchage displays audio ports as blue boxes and MIDI ports as green boxes

---

### Post by zangler on 2010-12-23
Thanks cchhrriiss121212.

I've done what you have suggested - JACK is running and I can now hear my microphone input through my headphones via the soundblaster live card.  I then start rakarrack, and I've noticed that in Patchage the settings for System capture_1 and capture_2 are mapped to Rakarrack in_1 and in_2 respectively.  Similarly, Rakarrack out_1 and out_2 are mapped to System playback_1 and playback_2 respectively.

So thanks to you, I've now got headphones and mic working - do you have any suggestions about how to listen to the guitar through the USB port?

---

### Post by cchhrriiss121212 on 2010-12-23
Rakarrack will autoconnect, you can turn that off if you like in the preferences.

> So thanks to you, I've now got headphones and mic working - do you have any suggestions about how to listen to the guitar through the USB port?
Try opening the setup window in jack control, then check the input device list. If you see it there then try selecting it. 

If you don't see it, put this into a terminal and post the output:
lsusb && arecord -l

---

### Post by zangler on 2010-12-23
Here is the output from the terminal window...

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**** List of CAPTURE Hardware Devices ****
card 0: Live [SB Live! 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! 5.1 [SB0060]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I had a look at the various options in the JACK input devices - there were none that linked to guitar or anything similar - the two USB entries (USB Audio and USB Audio Codec) gave error messages and I struggled to stop the application from just churning out error messages.

---

### Post by transmogrifox on 2010-12-23
> **zangler said:**
> Here is the output from the terminal window...

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**** List of CAPTURE Hardware Devices ****
card 0: Live [SB Live! 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! 5.1 [SB0060]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I had a look at the various options in the JACK input devices - there were none that linked to guitar or anything similar - the two USB entries (USB Audio and USB Audio Codec) gave error messages and I struggled to stop the application from just churning out error messages.

You will struggle against physics if you try to use a USB device as an input and your SB Live as an output.  Your USB guitar probably has a run-of-the-mill USB audio chip in it, so it looks like it has an input and an output (thus you see two entries in jack).  Now the problem is the audio coming in from this device is not synchronized to the same clock as the audio to/from the SBLive, so it generates interrupts to say "hey I have audio to put into the stream" at different times than the SBLive generates and interrupt to say "hey I'm ready for some audio".  This really messes up the real-time scheduling of jack, and usually jack can't even start in this case.

One setting you can mess with that may give you some limited success is the periods/buffer setting.  This creates memory for more audio slices, so the computer has the ability to use the added latency to pad the lack of synchronization.  Increasing Frames/Buffer may help too, and also unchecking the Realtime box may help Jack deal with the scheduling issues.  Please remember all these ideas are only work-arounds to a fundamental time synchronization problem.

Your best bet is if your USB guitar happens to have an audio output (which is unlikely).  Then that USB interface is your sound card in (from guitar) and out (to some speakers).  

It is best to use a conventional electric guitar and plug into the mic or line input on your sound card so all audio is going to and coming from the SBLive.

Now, you might be able to work something out through PulseAudio's jack interface.  The idea is you route the usb interface through pulseaudio into jack, then back out to pulseaudio to the SBLive.  You will never get very low latency like this, but maybe it will be acceptable.  Unfortunately I don't know much about PulseAudio so I can't help there, but maybe somebody else can chime in on that.

---

### Post by cchhrriiss121212 on 2010-12-23
> It is best to use a conventional electric guitar and plug into the mic or line input on your sound card so all audio is going to and coming from the SBLive.
I agree with this, except you should also use a pre-amp before going into the soundcard. A guitar OD pedal will do, then you just need a 1/4" to 1/8" cable which only cost a small amount.
You could go straight into the soundblaster but it won't sound very good.

Edit: you might be able to use the USB with jack if you use alsa_in/alsa_out which enables you to use 2 devices at once. See here:
[http://ubuntuforums.org/showthread.php?t=1377954]("http://ubuntuforums.org/showthread.php?t=1377954")

---

### Post by transmogrifox on 2010-12-23
> **cchhrriiss121212 said:**
> I agree with this, except you should also use a pre-amp before going into the soundcard. A guitar OD pedal will do, then you just need a 1/4" to 1/8" cable which only cost a small amount.

Yes, this is good advice.  Line Input and Mic input impedances are not well suited to a typical passive electric guitar output.  If you have an onboard active system on your guitar, then you can plug direct without another preamp.

---

### Post by zangler on 2010-12-23
My USB guitar is a Behringer iAxe 393 which has 3 sockets - 1 for traditional elec guitar output (1/4" Jack), 1 for USB connection (I believe this feeds in both directions) and the third is a 1/4" Jack for headphones.  The original setup on a windows PC had a Native Instruments Guitar Combo modelling amp, with USB in/out and headphones/speakers connected directly to the guitar - the traditional elec guitar output wasn't used unless I wanted to plug straight into an amp (without the USB connected).  This worked a treat.  Can I arrange for similar in Ubuntu Studio?  Do I need to remove the Soundblaster Live soundcard to make sure that it doesn't interfere?

I'm sorry, I don't understand the alsa in/out discussion in the other thread.  I appreciate you are trying to help, but this just confused me even more! :confused:

---

### Post by cchhrriiss121212 on 2010-12-23
> Can I arrange for similar in Ubuntu Studio?
I think so: try selecting USB as the interface then leave the input device as default. That means you won't get sound from your creative card, and you don't need to remove it.

The thing about jack is that it is only designed to use one sound device, alsa_in/out was made to get around that, but it is still not very user friendly like many other linux tools. If you are happy using one device at a time, then you can forget about it.

---

### Post by transmogrifox on 2010-12-23
Yes, use the USB Audio CODEC device for the output, and the other USB item listed for input.  I have found with the chip Behringer uses in these it doesn't matter which you select for input and output.  48kHz sample rate is the most stable in my experience with the UCA202, which I would bet large money has the same CODEC chip in it.

If you have the headphones output then you're set.  Select HW:1 instead of HW:0.

The only problem jack has is if you were trying to use the guitar as input and the SB audigy for output.  If you use the USB guitar for input and the USB headphone output then it's just a matter of selecting this for inputs & outputs in qjackctl and start jack.  It will probably work like a charm :)

If you have computer speakers, or a pair of monitors/amps, stereo system, then you can use the proper adapter cable to plug the headphone out jack into whatever.  

If you go directly into an amp from the headphone jack, and you find you're not happy with the sound quality, then here's my input on that:
For the headphone out on my UCA202, I have a feeling it is a little PWM (switch-mode) amplifier because it sounds a bit noisey going into a standard amplifier input.  For this I load it down with a 47 ohm resistor and put a little capacitor in parallel to make the headphone amp happy.  You can also try adding an RF choke in series with the line or run it a few loops through a ferrite donut.

---

### Post by zangler on 2010-12-24
Thank you both for your patience and assistance.  I've plugged headphones into the guitar port (as I would have done under windows) and the guitar is connected to Ubuntu Studio via USB.  When I boot, I can hear the sound file played on entry to studio, via the headphones connected to the guitar.  I open Rakarrack and there is no response to the guitar.  The level indicators do not move for either input or output.  I open up JACK and it is running.  In the Setup section, I change the defaults to USB Audio CODEC HW:1,0 for the output and USB Audio HW:1 for the input.  I stop JACK and close it, then open up Rakarrack again - still no sound or movement on the input/output levels.  JACK seems to be working fine (there are no dubious error messages - I had loads of these yesterday when I selected the 2 USB lines for input and output).

I don't know what to do next.

---

### Post by cchhrriiss121212 on 2010-12-24
>  change the defaults to USB Audio CODEC HW:1,0 for the output and USB Audio HW:1 for the input
Try setting these back to default. Then select hw:1 as the interface. Press start and check patchage again as you will now have different ports available for connection, Rakarrack could still be trying to use your soundblaster (hw:0) ports.

---

### Post by zangler on 2010-12-24
Thanks for the prompt response.  I've changed them back to default input/output devices and changed the interface to hw:1 (USB Audio CODEC) - restarted JACK/Rakarrack and no indication of throughput.  Changed the interface to hw:1,0 (USB Audio) - restarted JACK and Rakarrack, still no indication of throughput.

Patchage shows System capture_1 and capture_2 connected to in_1 and in_2 of Rakarrack respectively and out_1/out_2 of Rakarrack to System playback_1/playback_2 respectively.

---

### Post by cchhrriiss121212 on 2010-12-24
Could be that your capture levels are muted. Open a terminal and type alsamixer, then use the arrow keys to adjust.

---

### Post by zangler on 2010-12-24
alsamixer gives two soundcards (as expected), 0 is the SB Live card and 1 is the USB Audio CODEC.  The default is the SB Live card.  If I select the USB Audio CODEC, there is only one control under [playback] - PCM and it is at max (100).  Pressing F4 for Capture options results in the following message "This sound device does not have any capture controls".  I guess these settings are ok?  Is there anywhere to enable/disable the capture facility, could that be the problem (or am I clutching at straws)?

---

### Post by cchhrriiss121212 on 2010-12-24
Some devices don't have any capture control, that is normal. Here is something that might give you a few tips:
[http://braintubes.com/blog/?p=821](http://braintubes.com/blog/?p=821)

It is old but it shows the device works under Ubuntu, try to copy the same jack settings and see what you get. You don't need to use Creox, it is not being developed anymore.

---

### Post by zangler on 2010-12-24
Thanks for the link - there's hope that this setup can work in ubuntu!  I came unstuck at the first picture.  It shows a window that was obtained by the path System > Preferences > Sounds.  Following that path in Studio 10.10 doesn't give me the two tabs shown in the screenshot - I get Sound Effects, Hardware, Input, Output and Applications.  None of these tabs have the settings to route everything through ALSA.  Has this functionality been moved somewhere else in Studio 10.10?

---

### Post by cchhrriiss121212 on 2010-12-24
Just ignore steps 1 and 2, the guide should still work without the old Sound menu. Jack uses ALSA anyway so I'm not sure why it was included in the guide.

---

### Post by zangler on 2010-12-24
I assume I don't need to do Step 3 as jackd and qjackctl are installed (is this right?  I wouldn't be able to open up the Jack Audio Connection Kit if these two packages weren't installed?)

Steps 4 & 5 - opened up JACK Control, made and saved all the changes shown in the settings tab - my settings now identical to those in the given screenshot.

Step 6 - started Rakarrack.

Unfortunately, still no sound - no input/output level movement in Rakarrack.

---

### Post by cchhrriiss121212 on 2010-12-24
Try just connecting the system capture ports to the system playback ports, if that gives nothing then I am out of ideas.
I can't think of any other reasons why this device wouldn't work, given that it is class compliant and there are reports of it working for other people on Ubuntu.

---

### Post by zangler on 2010-12-24
Do you mean to remove the links to Rakarrack in Patchage and just link the two System in_1/in_2 to the System out_1/out_2?

No that didn't work!  Frustrating to know that others have got it working but I can't!  Is it worth trying a clean reinstall of everything (typical Windows answer!)

---

### Post by cchhrriiss121212 on 2010-12-24
> Frustrating to know that others have got it working but I can't!
I had the same thing happen to me last year with a DVD drive that was fully supported. Sometimes the a certain kernel can cause trouble or there is just a bad match between hardware controllers. With every new Ubuntu release there are many devices that gain support and a handful that lose support, the reasons are to do with the way Linux has been designed. 

>   Is it worth trying a clean reinstall of everything		
I doubt that would help.

You could try an older version like 10.04 (go for the regular Ubuntu), but that depends on whether you want to download another image. You wouldn't have to install it, just try it out with a live environment using something simple like Audacity.

---

### Post by transmogrifox on 2010-12-24
One good idea is to try routing the output of an audio player (like totem) or software synth like ZynAddSubFX through Rakarrack just to make sure all is well with jack and that you're not experiencing trouble elsewhere.  If you can get sound from the computer internals to the output, then it narrows our troubleshooting to only the capture ports.

Here's the link the author of the blog cchhrriiss121212 linked for another angle on it:
[http://www.detector-pro.com/2008/11/how-to-connect-usb-guitar-pedal-or-any.html](http://www.detector-pro.com/2008/11/how-to-connect-usb-guitar-pedal-or-any.html)

Then Ubuntu's documentation:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
And,
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)
It's old but still relevant.  I prefer to make connections from qjackctl instead of patchage.  For troubleshooting purposes, it may be better to eliminate patchage for the moment until you get things figured out.

For me figuring out how to get audio in and out of jack & Rakarrack the first time was a little mind boggling, but once I got it working, the light bulb came on & it all made sense.

Edit:
Another good thing you can try is GNUguitarINUX.  It's a live CD (you can also flash it directly to USB stick too) that is set up specifically for guitar players who are newbies to linux:
[http://gnuguitarinux.sourceforge.net/](http://gnuguitarinux.sourceforge.net/)

Use the qjackctl Connections dialog to make connections.  Once you get things properly configured and working, you can go into Rakarrack preferences and select input and output ports used in jack.  On my computer, all I need to do is start Rakarrack.  Rakarrack automagically starts jack if it is not running, then connects to my capture and playback ports -- nothing more needed to start jamming.

---

