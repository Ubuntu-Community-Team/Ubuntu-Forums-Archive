---
title: "Sound Problem with Ubuntu 9.04"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Faud on 2009-08-15
Hello everyone,

New install of 9.04. I am dual booting with windows 7.
I am using headphones that are plugged into the usb slot. I do not have any speakers.
If I go into Preferences>Sound and I switch it from auto detect to USB I can hear all of the test sounds but I cannot hear sound on the web or from a player.

```
ryan@ryan-desktop:~$ lspci | grep Audio
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

```

If anyone has any ideas to get it working please let me know.  I did go into alsamixer in terminal, it would not let me up the bar that said headphones but other than that everything looked ok as far as I know.

Thanks

---

### Post by Faud on 2009-08-16
Anyone have any ideas?

---

### Post by colau on 2009-08-16
Set to ALSA.

---

### Post by Faud on 2009-08-16
Hi,

I have put it on ALSA and also HDA NVidia ALC883 Digital ALSA and neither of them work or even give me a test sound

The only one that gives a test sound is USB Device

If I use USD Device ALSA I get

```
audiotestsrc wave=sine freq=512 ! audioconver ! audio resample ! gcodfaudiosink: Could not open audio device for playback.
```

---

### Post by Faud on 2009-08-16
I have tried turning everything up in ```
alsamixer
``` but still nothing.  I am fresh out of ideas so if anyone can help that would be fantastic. I have no sound anywhere except on the test sound thing

---

### Post by camaron1 on 2009-08-16
Try setting every thing to pulse audio except for Default Mixer Tracks where you choose your card or the Alsa equivalent. I'm not sure what you mean when you say you set to to USB Device, what ever that is I don't think it refers to headphones.

Good luck

---

### Post by Faud on 2009-08-16
I did not have any luck with that but here is a picture of the Preferences>Sound so you know what Im talking about with the USB thing.

---

### Post by camaron1 on 2009-08-16
As I said, I don't think you should choose the USB device, but I suppose it doesn't matter as the actual playback is set to Pulse Audio.

Now, You've got Default Mixer Track set to Capture, set it to either playback (and again choose your card name) or your card name (alsa mixer). This options are further down.

See if this works

See attachment bellow.

---

### Post by camaron1 on 2009-08-16
Also, go to Applications>Sound & Video and  open Sound control. Make sure you've got the right device chosen. Then turn the relevant controls up. The controls you see will depend on your specific device. The attachment shows mine.

---

### Post by colau on 2009-08-16
@Fuad
I also suggest this:
[http://ubuntuforums.org/attachment.php?attachmentid=125072&d=1250414251](http://ubuntuforums.org/attachment.php?attachmentid=125072&d=1250414251)

---

### Post by colau on 2009-08-16
@Fuad
[http://ubuntuforums.org/attachment.php?attachmentid=125071&d=1250413738](http://ubuntuforums.org/attachment.php?attachmentid=125071&d=1250413738)

---

### Post by Faud on 2009-08-16
I have tried both of your suggestions, neither worked.  Im at my wits end here, been messing with it for a few hours.  I did want to say thank you though to the guys/gals that helped.

Thanks

---

### Post by Faud on 2009-08-16
If this can help anyone =)

```

ryan@ryan-desktop:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: MCP55 High Definition Audio
       vendor: nVidia Corporation
       physical id: f.1
       bus info: pci@0000:00:0f.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
ryan@ryan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0xd8c0x0c [USB Device 0xd8c:0x0c], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ryan@ryan-desktop:~$ 

```

---

### Post by Faud on 2009-08-16
Any new ideas or sound experts for this?

---

### Post by Windows Nerd on 2009-08-16
Getting speakers and then plugging your headphones into there might work. I have never really heard of someone plugging in headphones using a USB.

This may not be expert advice, but there *is* some common sense involved :)

---

### Post by Faud on 2009-08-16
> Getting speakers and then plugging your headphones into there might work. I have never really heard of someone plugging in headphones using a USB.

This may not be expert advice, but there is some common sense involved

I have no idea what this means.  Have you never seen headphones that plug into a USB?  That is what I am using.  I have no idea what you mean by common sense?
But, I really should not have to buy additional parts for my machine to get the same performance on Ubuntu as I do on Windows...you agree?

---

### Post by JC Cheloven on 2009-08-16
Hi, 
I have to admit that I'd seldom succeded in fixing sound problems under linux, altough I tried hard. On one hand, this explains my dependence on windoze for sound apps. On the other hand, this warns you about how much you can expect from my advice ;-) Anyway: 

I'd say that your usb headphones are in fact a sound card, and are so detected. Having multiple soundcards is a linux bitch, in my humble experience. I'd suggest to disable your nvidia card from the bios. Turn off the computer. Plug your usb headphones, and then reboot.

Hope this helps

EDIT: Beware, turn off only the nvidia soundcard (if possible), not every other nvidia services that are possibly over there.

---

### Post by Faud on 2009-08-16
Thanks, good idea.

Is there a way that I can do this internally on Ubuntu, only for Ubuntu that way I do not have to re-enable every time I boot up to windows?

---

### Post by Windows Nerd on 2009-08-17
> **Faud said:**
> I have no idea what this means.  Have you never seen headphones that plug into a USB?  That is what I am using.  I have no idea what you mean by common sense?
But, I really should not have to buy additional parts for my machine to get the same performance on Ubuntu as I do on Windows...you agree?


Actually, I have never seen someone plugin headphones using a USB. I use a laptop for preety much everything, as does my family and most of my friends...and a laptop usually has a headphone jack built in at the front or side.

And I get what you mean by not having to buy additional parts: I hate spending money exept when absalutely nescesary. I was just proposing an alternative solution.


Scott

---

### Post by JC Cheloven on 2009-08-17
> **Faud said:**
> Thanks, good idea.

Is there a way that I can do this internally on Ubuntu, only for Ubuntu that way I do not have to re-enable every time I boot up to windows?

I vaguely remember it was. Also I vaguely remember some problem related with that; I think it was the setting don't surviving to a reboot, making it of little interest. I'll look around to see if I can be more precise, and come back over.

Also, a bit out of topic: does your pc have a headphones outlet? Every pc I'm aware does. And it surely works with your nvidia card. In that case, you can take some headphones you may have around (I have several of them, from old mp3 players and similar stuff) and simply plug them. Or perhaps your present usb headphones are of much better quality? Sorry, I'm just curious.

---

### Post by Faud on 2009-08-17
I did find some old headphone in a box, and they are working fine with the sound.
One of the great things about Ubuntu though is that when you come across a problem, you learn so much about your computer, and Ubuntu as you try different things to fix it. 
You also get to meet some great people on these forums :)
Once you learn how to fix it, you get to pass that knowledge on to the next person.
So I hope to get this figured out with the USB headsets, but for now I will use some regular headphones and have sound :guitar:

---

### Post by camaron1 on 2009-08-17
In spite of everything I'm sure you'll get it working. It was hard job for me but eventually got there. What I discovered a couple of times is that sometimes different apps that control the same parameters have different set ups (they don't communicate well with each other). Open all apps you have installed one by one and recheck all settings. It could be also a case that you don't have some package needed for your sound. 

Go through this posts, it is a bit of work but all to do with sound and ubuntu is there. 
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
[ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")
[ubuntuforums.org/showthread.php?t=997506]("http://ubuntuforums.org/showthread.php?t=997506")
[ubuntuforums.org/showthread.php?p=6628921]("http://ubuntuforums.org/showthread.php?p=6628921")
[ubuntuforums.org/showthread.php?p=5931543]("http://ubuntuforums.org/showthread.php?p=5931543")

Let us know if you are not lucky

---

### Post by JC Cheloven on 2009-08-22
> **Faud said:**
> I did find some old headphone in a box, and they are working fine with the sound.
One of the great things about Ubuntu though is that when you come across a problem, you learn so much about your computer, and Ubuntu as you try different things to fix it. 
You also get to meet some great people on these forums :)
Once you learn how to fix it, you get to pass that knowledge on to the next person.
So I hope to get this figured out with the USB headsets, but for now I will use some regular headphones and have sound :guitar:

Glad to hear you overcame the problem. Sorry I didn't provide a smarter solution. But perhaps the mini-soundcard built into your headphones simply is not standard enough, and isn't supported in linux. I tried once a very small usb sc (of the size of a pendrive; a friend bought it in a chinesse internet store), and I wasn't able to put it to work in linux either. But camaron gave you a nice set of pointings to ckeck out... good luck.

btw: I also like people in these forums ;-)

---

