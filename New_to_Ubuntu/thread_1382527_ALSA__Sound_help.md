---
title: "ALSA / Sound help"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Danwhelan on 2010-01-16
Hi there 

I'm using - Karmic 9.10

Basically I've tried to update my ALSA driver set to get my microphone working... I used the instructions found here 

[http://ubuntuforums.org/showthread.php?t=927270](http://ubuntuforums.org/showthread.php?t=927270)

Now I've no sound at all, I've tried trying to diagnose the problem however can't seem to find anything specific to this issue. 

My sound settings page is just blank on the hardware tab

Various tests have shown that the sound card is detected... but no joy 

Can any one help with this? 

Many thanks 

Dan

---

### Post by Danwhelan on 2010-01-16
Anyone????

---

### Post by MarkC502 on 2010-01-16
I would say you could try running the following command and make sure you see that the sound is turned up on all the devices you are trying to use.

sudo alsamixer

You can use your arrow keys to move and control volume levels of your devices.

I am not sure if you might find something is turned down in these settings but I have seen before where Gnome's volume controls said full volume and alsamixer said low volume and when I turned it up it fixed my low sound issue.

---

### Post by Danwhelan on 2010-01-17
Thanks for the input - I will give this a go. However on the hardware tab of that dialogue I'm not showing any devices at all.

---

### Post by Danwhelan on 2010-01-17
Help :-(

---

### Post by MarkC502 on 2010-01-17
OK just a note for you to get the help you want. Your post is really vague as to what you have done and the link you gave has several people saying hers how to do it + several links so I have no idea what you have attempted and what the outcome of that was. First a few obvious questions to clear up. 

1. That thread is for an Acer Aspire , is that what you are using?

2. Did your sound work except for mic , then you tried to compile newer alsa and now have no sound or did you have no sound since installing Ubuntu?

3. Did you run ./configure , make then sudo make install on the source code you downloaded ? If you followed all those steps did they all complete error free or did you see any errors during those steps?

Let me know that info and I can help more, in general though you can usually go into the same source code directory and run "sudo make uninstall" and remove the package you installed manually. Comes in handy :-)

---

### Post by Danwhelan on 2010-01-18
Mark... thanks for replying 

Sorry if my post didn't sound to specific... 

1 - It is an Acer Aspire that I have 

2 - The sound was working prior to me playing around... however the mic was not working.

I followed the following steps 

Download <a href="[ftp://ftp.alsa-project.org/pub/drive...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2")">Alsa drivers v10.0.20

Extracted

Compiled the driver with 
 
./configure
make
sudo make install

Configured alsa-base.conf using sudo gedit - filename 
 Added the following line to the end of /etc/modprobe.d/alsa-base.conf
 
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer

To complete the disaster I rebooted

All this seemed to go off with out a problem.. as in there were no errors that I noticed... however I am from the school of never assume... and I assume that as things are not working that there must have been some sort of error. 

I'm a little worried about un-installing things as the first time I set the system up I have an issue removing some blackberry software and ended up removing the desktop and a whole load of other stuff... 

I hope that this helps 

Best and thanks again 

Dan

---

### Post by MarkC502 on 2010-01-18
No prob Dan, I never mind helping people when they are nice and also are willing to help themselves. You obviously are trying to help yourself so it makes me happy to help you do so.

For future reference ( its too late now after you did the full manual install ) when you are custom installing things what I do is as follows ( not saying my way is best etc just that a few simple precautions have saved me tons of grief ).

1. After you obtain any source code package ( such as the Alsa one you are working with ) I think it is best to always look for 2 files the README & INSTALL files and look through them for tips etc. Hopefully you already do that as most people do. But one thing most don't do is to open the makefile and see what the different make options the author has included ( these will be a turquoise color text in gedit ) . This lets you see if the Author of any given software has included uninstall as one of the options ( be careful with programs that don't as this means you would need to manually undo the changes the "sudo make install" performs in order to remove the software properly ). If the package you are trying to obtain contains uninstall as an option in the makefile then you can uninstall it and all its changes with a simple "sudo make uninstall" command in the source code folder.

I downloaded the source you linked and there is an uninstall option in the makefile, so you can uninstall this software rather easily. The only thing you would have to change back manually would be the lines you added to the config file via gedit.

2. When you start installing a custom piece of software the best advice I could give is that when you run ./configure after it completes I always scroll up through the output and look for any errors etc and if any are seen I might stop and go rectify the problem and then try ./configure again and see if I removed the error. Mostly with ./configure this comes into play when trying to install software from source that uses allot of other libraries or other utilities in its operation. Failure to do this can mean you get a program to install but some functions aren't available or do not work properly.

Next do the same thing when you run the make command as well and if you don't see any errors between ./configure & make's output then it's probably going to install :-)

I would suggest you look at Alsa's site as the version you are downloading is a bit old and there is a alsa-driver-1.0.22.1 version on their site from Dec 2009 which I would probably try since you are using 9.10 and dependencies should probably work out. I would recommend always starting at the Authors site and obtaining the latest stable version of a program to start an install attempt, unless you are following some guide or advice that the newest does not work etc.

Link To Latest Stable Alsa Driver

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2)

Hope this helps you with some things to try :-)

---

### Post by Danwhelan on 2010-01-18
Hi there 

Thanks Mike for all the help - I do try with the linux command thing... but I can't seem to get my head around some parts of it. 

OK - I've reinstalled a fresh copy of the driver with the configure make make install dialogue... 

I watched the install and it went through with no errors. 

On some of the installation descriptions I have read they configure the utils and the lib folders as well.. however the package that I've downloaded from your link had a configure file that seemed to include the utils section and it had no lib folder. 

As usual everything else is fine except the sound... the sound hardware tab shows no hardware installed at all.

One good thing is that the ALSA mixer comes up when asked...  it didn't before. 

lspci gives me the sound card shown... so I know it's there... something can see it which is a step in the right direction. 

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

lshw gives me 

   *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:30 memory:fc200000-fc203fff

However still no sound... can't think of anything else to do right now

Any ideas?

---

### Post by MarkC502 on 2010-01-18
Only that you could uninstall any alsa stuff you installed , reboot and see if it reverts back to the standard one. If it doesn't then open synaptic and reinstall alsa in there. 

To uninstall the alsa drivers package you only need to be in the source directory at a command prompt ( just like when you ./conifgured and installed it ) and run the single command "sudo make uninstall" and it will uninstall alsa that you installed. I would do that and see if after a reboot your system goes back to the default one where everything but our mic worked. Then I would start over if the mic is important , but at least then you will know that you can revert and you can then start a fresh attempt to install it.

---

### Post by Danwhelan on 2010-01-18
In addition 

Alsaconf also runs fine... and says sound card configured 

Still no sound 

:-(

---

### Post by MarkC502 on 2010-01-18
You might look at the output of

sudo lspci -v

And look for your audio device, my output looks like the output below on one of my boxes. You can see the kernel driver in use with this.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: Jetway Information Co., Ltd. Device a625
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

See what yours says. Also you said alsamixer command now loads, do you see any interfaces displayed ?

---

### Post by Danwhelan on 2010-01-18
Thanks for this Marc 

Mine says 

Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Acer Incorporated [ALI] Device 0133
Flags: bus master, fast devsel, latency 0, IRQ 30
Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
Capabilities: [100] Virtual Channel <?>
Capabilities: [130] Root Complex Link <?>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

Which is annoying as it looks on the face of things like yours. 

The alsamixer shows me master headphone pcm and front all at about 80 db line in mic and mic boost are all zero 

Card: HDA Intel                       
Chip: Realtek ALC268              
View: [Playback] Capture  All   
Item: Master [dB gain=-12.00] 

This should be working :-( 

Sound system settings 

Hardware is - empty 
Input is - empty 
Output is - Dummy output.... which oddly is in Stereo

I'll keep looking 

Dan

---

### Post by MarkC502 on 2010-01-18
Just as a try, try the following command. this would only fix it if somehow the driver module is not loading correctly.

sudo modprobe snd-hda-intel

Then see if alsamixer hardware changes. Worth a shot :-)

---

### Post by Danwhelan on 2010-01-18
OK it did something 

Now my mouse over read out on the sound Icon shows 

Output 98%
-.53 db
Dummy output 

Prior to this is was all zero'd 

So it did something 

I think the answer lies in the alsa-base.conf file 

I just have no clue where 

Thanks again...

---

### Post by Danwhelan on 2010-01-18
Sorry 

Alsamixer read out the same 

Card: HDA Intel                   
Chip: Realtek ALC268
View: [Playback] Capture  All
Item: Master [dB gain=-12.00] 

D

---

### Post by Danwhelan on 2010-01-21
Sorry Marc I was away for a few days and I'm back with this same problem... 

An update - although it seems that it's only you, that knows what you're talking about, as everyone else seems to be ignoring the thread... 

Sh**  though windows was - people pitched in to help. 

The sound is actually now working.. however only in firefox. 

GNOME GUI still shows dummy output

Alsamixer functions well as a program... but like the labout party actualy does nothing... there is no control of the sound at all it's either on full volume or off

Alsa conf - again runs through and picks the sound card... sets it up, says OK... no sound still dummy output 

Alsa force-reload produces 

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release. (approx 35 times) 

ALSA mixer - key F4... mic is set to capture in red.. so something is working but it's not the Mic 

Mic source only gives me the option of front mic.... on the pre 9.10 versions this was a problem for ACER... since it takes about 8 months to get people to answer forum questions I have to assume that this is still the case. 

Arms up in defeat 

Thanks again marc, my question is what would happen if I purged alsa and went again?

I'm worried about it taking out other programs.. 

Best 

Dan

---

### Post by Danwhelan on 2010-01-23
Anyone?

---

