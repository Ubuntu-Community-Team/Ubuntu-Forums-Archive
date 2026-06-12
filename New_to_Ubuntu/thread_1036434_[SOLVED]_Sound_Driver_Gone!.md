---
title: "[SOLVED] Sound Driver Gone!"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by RogueS on 2009-01-10
RESOLVED! Thanks everyone for the help!



No volume control GStreamer plugins and/or devices found.

My volume control has a little X on it. 

I just noticed I wasn't getting sound on a few games but watched movies earlier just fine. I restarted because some updates were suggested and now I have no sound at all.

I'm a total  noob so step by step help please and thanks!

---

### Post by skern03 on 2009-01-10
> **RogueS said:**
> No volume control GStreamer plugins and/or devices found.

My volume control has a little X on it. 

I just noticed I wasn't getting sound on a few games but watched movies earlier just fine. I restarted because some updates were suggested and now I have no sound at all.

I'm a total  noob so step by step help please and thanks!

It's usually a good idea to post which version if Ubuntu you're using. However, I can direct you to a a sticky post that covers 8.10, 8.04 and even earlier versions.

At the Ubuntu Forums home, look for the Multimedia & Video forum, and open it (this is not the same thing as the Multimedia Production Forum, BTW). Click the link to the forum. At the top you'll see two sticky posts. Follow the instructions in the Comprehensive Sound Problem Guide (it's the second post, as I recall).

It's also a good idea to follow the instructions in the first post, which is a how-to on video and multimedia.

If you still have sound issues after following those instructions, post back, and let us know what problems you're having.

---

### Post by RogueS on 2009-01-10
Ok so the first thing it tells me to do is go to a shell and type...

HEY! Im a noob wtf is a shell?

Thanks but thats why I asked here because I cant understand the other help forums at all because I am very new at using Ubuntu thanks.

---

### Post by RogueS on 2009-01-10
Ok 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Giga-byte Technology Unknown device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at fb000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f458:5002
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) 

I figured out that shell is terminal. Quit making new names for things! LoL!

So Im STUCK here at this point in the instructions on that post:

(3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

    * Success - You will have found the driver for your soundcard's chipset.

    *
      Failure - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you, but stay tuned!)


I can't find the damned drop down box there isn't one I get this huge parent directory site and cant find anything useful.

---

### Post by skern03 on 2009-01-10
> **RogueS said:**
> Ok 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Giga-byte Technology Unknown device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at fb000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f458:5002
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) 

I figured out that shell is terminal. Quit making new names for things! LoL!

So Im STUCK here at this point in the instructions on that post:

(3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

    * Success - You will have found the driver for your soundcard's chipset.

    *
      Failure - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you, but stay tuned!)


I can't find the damned drop down box there isn't one I get this huge parent directory site and cant find anything useful.

Ooohhh... A lot of people have reported difficulty with HDA drivers. Guess I'm lucky to have an older chipset. I don't know of a solution - there may be one, I just don't know of one, and have no way to test since I don't have HDA. If you're not running 8.10, you might try upgrading. Not sure if will help, tho.

---

### Post by RogueS on 2009-01-10
It worked great til today, how do I upgrade? I dont even know which one im using :(

---

### Post by cariboo on 2009-01-10
IF you are a noobie, I wouldn't suggest upgrading, as you will more then likely fix one problem, and run to another one. To find if the sound drivers are loaded in a terminal (shell) type:

```
lsmod | grep snd
```

If the sound module is loaded, you should see something like this:

```
lsmod | grep snd
snd_hda_intel         542772  3 
snd_usb_audio         108576  1 
snd_pcm                98952  3 saa7134_alsa,snd_hda_intel,snd_usb_audio
snd_usb_lib            27392  1 snd_usb_audio
snd_seq_midi           15744  0 
snd_seq_midi_event     16512  1 snd_seq_midi
snd_rawmidi            33920  2 snd_usb_lib,snd_seq_midi
snd_hwdep              16776  1 snd_usb_audio
snd_seq                66144  2 snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  17 saa7134_alsa,snd_hda_intel,snd_usb_audio,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
```

Just to make sure your sound device is detected properly in the same terminal type:

```
aplay -l
```

you should get a result that looks like this:

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Jim

---

### Post by RogueS on 2009-01-10
rogues@rogues-desktop:~$ lsmod | grep snd
rogues@rogues-desktop:~$ aplay -l
aplay: device_list:205: no soundcards found...

---

### Post by skern03 on 2009-01-10
> **RogueS said:**
> It worked great til today, how do I upgrade? I dont even know which one im using :(

You can find out which release by clicking System, About Ubuntu. If you see 8.10, that's the current stable release. 8.04 is also good - and by some reports, less troublesome than 8.10.

---

### Post by cariboo on 2009-01-10
If your sound card isn't being found, upgrading will not help. In a terminal type:

```
sudo lshw -C multimedia
```

and paste the output in your next post.

Jim

---

### Post by RogueS on 2009-01-10
*-multimedia UNCLAIMED  
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

---

### Post by RogueS on 2009-01-11
Any ideas? Kids are really bugging me to watch movies! HEAAAAALLP!

---

### Post by skern03 on 2009-01-11
> **RogueS said:**
> Any ideas? Kids are really bugging me to watch movies! HEAAAAALLP!

Yikes! Don't want tykes after you!!!

Anyway, try this for an experiment. If you have the Live CD, stick it in your CD/DVD drive, and restart. Let it boot from the CD (note that your BIOS must be set to boot from the CD first, but it probably is).

When you get to the install screen, select the option that runs it from the CD. Don't select the install option. This will be a bit slow, but you'll be running more-or-less "native" ubuntu.

When your system starts, run the same string you ran earlier in a terminal window:
```
sudo lshw -C multimedia
```
Check the results and compare it to the one you posted earlier in this thread. See if it finds your card.

I found a thread that exactly matched your problem - right down to the card! Unfortunately, nobody responded to the post :(

Here's a search string you might try in this forum:
> "multimedia unclaimed" nvidia
Make sure you include the quotes around the first two words.

---

### Post by RogueS on 2009-01-11
Eeep I don't have a live CD.

I have a burner and some cds around...I'll figure this out maybe? eep!

---

### Post by RogueS on 2009-01-11
SCORE! OK! FIXED!

Don't know how but anyway.. I mucked around with the bios ran live ubuntu from a disk, it had sound! So I was like hmmmm restarted and BAM sound. 

Nice Eh?

Thanks Guys!

---

### Post by skern03 on 2009-01-11
> **RogueS said:**
> SCORE! OK! FIXED!

Don't know how but anyway.. I mucked around with the bios ran live ubuntu from a disk, it had sound! So I was like hmmmm restarted and BAM sound. 

Nice Eh?

Thanks Guys!

Way to go!!!!

Are you running a PCI sound card on a motherboard with onboard sound? And if so, when you edited the BIOS, did you turn off the onboard sound chipset so that it used the sound card?

In any case, please mark the thread solved (click Thread Tools link at top of this thread page, and select mark solved).

---

### Post by RogueS on 2009-01-12
Actually I just changed the boot order and then put it back normal afterward! Weird eh?

Booting it up on the cd as live loaded up all the drivers apparently!

When it loaded them all up I guess that did something and the sound worked off the cd so maybe they just all loaded for me that way?

Either way thanks! Your idea is the one that solved it and thanks for telling me how to mark this as resolved!

---

