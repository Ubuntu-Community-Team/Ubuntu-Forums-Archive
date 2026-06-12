---
title: "Microphone not working in Skype"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by Phelixfil on 2011-03-23
I'm having a lot of trouble getting my microphone to work in any programme but especially skype.  I've looked through various threads and it seems that I am not alone although all the treads are about three years old.  I've tried to follow some of their recommendations but to no effect.  Can anyone help please?

---

### Post by arochester on 2011-03-23
The sound settings for Skype are IN Skype and NOT in the computer sound settings.

Go Skype> S Button (bottom left)> Options> Sound Devices. You will need to experiment with the various microphone settings and then make a test call.

---

### Post by IWantFroyo on 2011-03-23
What do you get with the microphone? What kind of computer is it?
If none of them are working, you might want to try a new kernel or a microphone-friendly distro (Fedora is a good choice). These kinds of problems are almost always fixed in new releases or with updates. My microphone refused to work with Ubuntu for a month, then an update came and everything is perfect.

---

### Post by mörgæs on 2011-03-23
There are several people trying to help you, for example here:
[http://ubuntuforums.org/showthread.php?t=1709038](http://ubuntuforums.org/showthread.php?t=1709038)

Please don't open more threads on the same problem.

---

### Post by Phelixfil on 2011-03-23
The computer is black and says intel core 2 duo.  It also has a 32bit kernel.  As to whether I should do something with the kernel or even what the kernel is I am at a bit of a loss.  That it might just fix itself in some future update is a reason to be optimistic but I kid of need to get it working so I'll try anything even if it means changing my kernels.  Any suggestions gratefully received.  Cheers, P

---

### Post by ajgreeny on 2011-03-23
Run ```
alsamixer
``` in terminal and check that the levels of inputs and outputs are not set too low.

Move from side to side, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by Phelixfil on 2011-03-23
That was looking hopeful for a moment.  I opened the window with the slider controls and two of them were not showing.  I've turned them up but still no joy on the skype test call

---

### Post by Phelixfil on 2011-03-28
Went to .. System
           Preferences
           Sound
           Input (tab)
Set "Connector" to "Microphone"
Move input volume control to 3/4 
make sure not "Muted"
Talk into the Mic and input level indicator should move.
Did a test call on skype and .. 
it worked a bit.
Saw some movement in the mic bar but now nothing!!!

                                                       
Source of original suggestion  [http://forum.skype.com/index.php?showtopic=468941](http://forum.skype.com/index.php?showtopic=468941)

---

### Post by Phelixfil on 2011-03-30
That seems to achieve something but the problem continues.  This is becoming very frustrating.

---

### Post by adduds on 2011-03-31
> I had the same problem, especially with Skype. After searching some forums, someone recommended installing Pulse Audio (you can find it in the Software Center "PulseAudio Volume Control"). Once installed, go to the Input Devices tab and put the front left on "Max" and the front right on "Silence". That should solve the problem. You will also have to go into Skype options - Sound Devices and make sure that the box is unchecked for "Allow Skype to automatically adjust my mixer levels." That will throw it off every time.

this worked like a charm for me acer aspire timeline x

---

### Post by Phelixfil on 2011-03-31
This has been driving me nuts for weeks now.  I have had occasional eureka moments only to be disillusioned later.
Yup, I think I must have read that post about "PulseAudio Volume Control" as it is already installed.  
Here's the snag....
I go into the "input devices" tab and set "Front Left" on 100%
Next step "Front Right" on 0%
Arg!!!!!
The two slider controls are linked and it's not possible to move one without the other
Other options...
There's a box marked "Port"
Here I can select "line In", "Mic 1" and "Mic2"
No joy
There's also a box marked "Show"  This gives me the options...
All input devices
All except monitors
Hardware input devices
Virtual input devices
Monitors.
Tried 'em all but nothing

Like all these things it is surely a question of making one tiny change and the problem is sorted.
Any further suggestions gratefully received:)

---

### Post by Phelixfil on 2011-03-31
I was a bit premature in my celebrations.  Still no joy:(

---

### Post by adduds on 2011-03-31
ya phelix i had the same problem with the two slides being linked

when your in the input tab with those two sliders there'll be a lock... click it then you can move each channel individually hope that fixes it

My volume control in pulse hardware input devices is selected in the drop menu then click that lock and that should hopefully fix ya mate

---

### Post by Phelixfil on 2011-04-01
r-senior posted
                                  **Re: Microphone problems**             
                                                                So it's a plain mic with a little 3.5mm stereo jack? Or is it mono? How many black stripes are on the plug - one or two?

Could you perhaps go to Sound Preferences and make screenshots of the middle three tabs (Hardware, Input and Output)?

Does sound work OK?

---

### Post by Phelixfil on 2011-04-01
Ok, so it's a plain stereo mic.  It looks like the jack for an ipod.  It has two black stripes.
Sound works fine.
I don't know how to make a screen shot to show you those tabs...
Cheers,
P

---

### Post by r-senior on 2011-04-01
My ideas were pretty feeble, especially as I don't have a microphone with a stereo jack to test, but I'll post them anyway. I was going to suggest you set your sound prefererences like the attached, then make a test recording with Sound Recorder.

The important points being duplex on your sound card (in and out), make sure all the volumes are turned up, and make sure you are selecting the external microphone rather than any internal one, dummy or otherwise.

If you can get that far, you isolate the problems to Skype.

But I think you are further on than that, albeit with no solution.

---

### Post by Phelixfil on 2011-04-01
Ha Ha! I remain completely in the dark.  I have learned quite a bit about this Ubuntu thing though:)
I had already tried the sound recorder but it doesn't seem to work at all.  
The solution has to be there somewhere...

---

### Post by r-senior on 2011-04-01
> **Phelixfil said:**
> I had already tried the sound recorder but it doesn't seem to work at all.
That's possible, but it could also be that your microphone doesn't work or the drivers are incorrect. My strategy would be to prove that I could use the microphone with Sound Recorder, on the basis that it's a pretty standard sound app. Then focus on Skype.

There's a chain, and you need to figure out where it breaks:

Microphone -> Cable-> Machine -> Drivers -> Sound Recorder -> Skype

---

### Post by Phelixfil on 2011-04-01
Ok so I bought a new mike and that didn't solve it.
I crawled under the table and checked several times that it was plugged into the right socket.  
It is.
Drivers......
How would I check that?

---

### Post by Lateralis on 2011-04-01
Can you type in the following commands into a terminal and post the output:

```

arecord -l
sudo lshw -C multimedia

```

The first command uses a lowercase 'L' and will tell us if your sound card (and more specifically, your recording devices) are being properly detected by Ubuntu.  The latter provides more info on your hardware and which driver modules are being loaded into the kernel. 

If after "arecord -l" it shows multiple sub devices you may want to follow the advice give in [this link]("https://help.ubuntu.com/community/SoundTroubleshooting").  Pulesaudio and ALSA by default listens to sub "device #0", but if, for instance, you are trying to record using "sub device #1" then nothing will happen.

---

### Post by Phelixfil on 2011-04-02
HI Thanks for that.  This is what I got for the two command lines
 
**** List of CAPTURE Hardware Devices ****

card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: SB [HDA ATI SB], device 2: ALC888 Analog [ALC888 Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 1: USB20Camera [USB2.0_Camera], device 0: USB Audio [USB Audio]

  Subdevices: 1/1

  Subdevice #0: subdevice #0



       bus info: pci@0000:00:14.2

       version: 00

       width: 64 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list

       configuration: driver=HDA Intel latency=32

       resources: irq:16 memory:fdef4000-fdef7fff





sudo lshw -C multimedia
*-multimedia            

       description: Audio device

       product: SBx00 Azalia (Intel HDA)

       vendor: ATI Technologies Inc

       physical id: 14.2

       bus info: pci@0000:00:14.2

       version: 00

       width: 64 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list

       configuration: driver=HDA Intel latency=32

       resources: irq:16 memory:fdef4000-fdef7fff



 As yet all that means very little to me.  The only other things I can offer are;
I am pretty sure the kernel on my computer is 32bit
The Microphone I have connected is Logitech.

Thank you very much for your time on this.  I hope I can contribute something back some day soon:)
Cheers,
P

---

### Post by Phelixfil on 2011-04-06
Still nothing:confused:.  I have tried everything that has been recommended in this thread.  Sometimes I get a garbled play back from Skype test call but even this is not consistent.  I realized that I have two mic jack sockets on the computer and have tried them both.  In one of them I can talk and amplify my voice through the speakers.  On the other nothing.  And in skype Still nothing.  
So it's not the hardware.  I can only think that there's some little box somewhere which has or has not been marked.  It's not set on mute so please don't suggest that.
I live in a very remote village with nine inhabitants five of whom live in my house.  I can speak to them without the aid of digital technology and I, with my 14 beans am the Ubuntu expert.  Skype is absolutely vital for communication with the outside world.  Go on feel sorry for me and suggest something. Please!

---

### Post by Lateralis on 2011-04-06
Hi Phelixfil.  From the looks and sounds of things I would say that Ubuntu is detecting your hardware just fine and that hardware isn't the problem.  It is almost certainly a software issue, whether that be a problem with the kernel modules, i.e. the wrong one is being loaded, or a problem with Skype.  

We can rule out the latter by testing your hardware setup using a different program.  Have you tried recording something using the Ubuntu sound recorder?  If you can record something in there without any problems then the issue is with Skype.  If you are unable to record using the sound recorder then the problem is with something else, possibly with the kernel modules.  I did read in a recent thread that Ubuntu was using the wrong kernel module for their sound card, which may be the case here.  I unfortunately can't remember which thread I read that in, but it might help if you could tell us precisely the manufacturing make and model of sound card that you are using.  

For what its worth I did actually have some sound card troubles with 10.10 (Maverick Meerkat) on my laptop which prompted me to revert back to the long term support release of 10.04 (Lucid Lynx).  So which version of Ubuntu are you running?  And have you ever had the microphone working in a previous installation of Ubuntu?

---

### Post by Phelixfil on 2011-04-06
Hi,  I'm using Ubuntu 10.10 maverik meerkat.
I'm completely new to Ubuntu and was running Windows before.  Skype worked fine there.
Sound recorder doesn't play back any sound.  The progress bar also jumps forward in 1 second chunks which looks suspicious.  
I don't know how I would find out the manufacturer, make and model of the sound card.  In a post from four days ago I was told to type some commands into terminal to reveal hardware devices and something else.  You can see the results a few steps back.  I didn't know what to make of it although I did notice it said something about 64 bit kernel when I'm fairly sure my pooter is 32 bit.  
I hope that might spark some light bulb in your head.  I remain in the dark.
Cheers,
P

---

### Post by Lateralis on 2011-04-06
Yeah I think I was the one that gave you those commands.  They were essentially designed to see if Ubuntu was detecting more than one sub device and which kernel module was being loaded.  From the looks of things Ubuntu is detecting a sound card, but I have what might be an unhealthy and totally unfounded suspicion of Maverick when it comes to sound.  (As I said, I had problems which prompted me to go back to Lucid and someone else recently said Ubuntu was loading the wrong kernel modules.)  

I am unfortunately rather tied up in RL at the moment so might not be able to help that much, or that rapidly.  But if you know the details of the computer then you can look up the specifications from the internet and find out what the details of the sound card are.

---

### Post by Phelixfil on 2011-04-06
Thanks for that.  I'm trying to find out the info from the people who cobbled it together.  It's definitely 32bit
Cheers,
P

---

### Post by Phelixfil on 2011-04-08
Hallelujah!!!!!:D
Here's the answer

Use gnome-alsamixer and pulseaudio volume control. If you are showing  input levels and everything works except skype, try this fix:
Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:


sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

This was originally posted by lidex in a thread entitled **v10.04 SONY VAIO SR11M FRONT MIC doesn't work**

---

### Post by kirbyw on 2011-04-09
I have the same problem... (also, I named my computer Desi because I'm a nerd. That's why that's there)

I tried that and this is what I get from the Terminal:

kirby@Desi:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-21-generic


So now what do I do?

---

### Post by Phelixfil on 2011-04-09
Copy each of the three command lines into terminal one at a time and hit return after each.
You then need to restart your computer.
Test things out with sound recorder or preferences, sound, input tab.  
If those don't get the results then go back to terminal and type in
alsamixer.  
That will open a window with all sorts of slider controls.  
Select the controls you need with the cursor keys and move between screens using tab
Turn all the sliders up to full.
I hope that does the trick.
Cheers,
P

---

### Post by maureenc on 2012-01-24
And another HUGE THANK YOU from me in 2012...

Ubuntu 10.4 and a new Logitech mic and it just wouldn't work....

I have a feeling that the bit about " DO NOT Allow Skype to automatically adjust my mixer levels." was very crucial in the solution as none of the other stuff worked until I did that...

Anyway.... Thank you for helping solving this new Linux mystery for me!

Mo

---

### Post by Rosscopico on 2012-02-09
> **adduds said:**
> I had the same problem, especially with Skype. After searching some forums, someone recommended installing Pulse Audio (you can find it in the Software Center "PulseAudio Volume Control"). Once installed, go to the Input Devices tab and put the front left on "Max" and the front right on "Silence". That should solve the problem. You will also have to go into Skype options - Sound Devices and make sure that the box is unchecked for "Allow Skype to automatically adjust my mixer levels." That will throw it off every time.

I can confirm this works with 10.04 on an Asus Eee PC 1005HA.
Thanks!

---

