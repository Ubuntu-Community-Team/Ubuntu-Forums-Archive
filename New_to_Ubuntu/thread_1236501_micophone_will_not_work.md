---
title: "micophone will not work"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by kimberley on 2009-08-10
[SIZE=3]I am a new user as of yesterday and[/SIZE][SIZE=3] I have an urgent problem in that I cannot get my microphone to work[/SIZE].[SIZE=3] I have an Acer monitor and [/SIZE][SIZE=3]previously did not have a problem using IMessenger.[/SIZE]
[SIZE=3]I need to be able to use Pidgin and Skype. I have already tried numerous options from the forum to no avail. Can anyone please help.  [/SIZE]

---

### Post by LowSky on 2009-08-10
go to sound preferneces (the little icon on the top panel, it looks like a speaker), go to advanced, make sure you have microphone and front microphone check and not on mute, and see if that works.

---

### Post by kimberley on 2009-08-10
[SIZE=3]Thank you but have already tried this and it does  not solve the problem.[/SIZE]

---

### Post by kwd on 2009-08-10
I just fixed the same problem on my computer.  I am running Kubuntu on an Asus A8N-E motherboard and I had to change settings in **TWO** places--In the KDE Control Center and the Kmix volume/mixer settings.

If you are running Ubuntu (Gnome) I don't know if this would help but you might look at its sound hardware and sound volume/mixer program's settings and see if there are similar settings you could change.


**ONE**--On my computer, these Kmix settings had to be set before the microphone would work in Skype:


KMIX settings:  (Green means activated but I am not sure what the red light indicates)
--------------
_Input Tab_:

[LIST]
[*]Microphone icon light is green at top and red at bottom and the volume slider is at max. 
[*]Capture icon light red at the bottom and slider volume is at max.
[/LIST]


_Switchs Tab_: (Yellow means it is activated)

[LIST]
[*]Mic Boost light is yellow
[*]Mic Front Input light is yellow
[*]Duplex Front light is yellow
[/LIST]

None of the other "Switches Tab" settings seemed to make any difference.
----------------

The Capture slider and Microphone icon settings were critical to make the system work at all.  The Mic Boost setting made it work much better.

Note that my access is through the computers front case not off the back of the motherboard and that is why I need the Duplex Front turned on.



**TWO**--In KDE Control Center go to "*Sound & Multimedia*" then to "*Sound System*" then to the "*Hardware Tab*" window.  In the *Hardware Tab* window make sure the "**Full duplex**" box has a check mark in it.

Hope this helps.

---

### Post by kimberley on 2009-08-11
I am running gnome and do not appear to have any of the settings which you describe - I have completely different features and failed to locate any of the ones you mention but thank you for the detailed explanation and I am only sorry it did not work for me.:(

---

### Post by tom66 on 2009-08-11
Could you please do the following:
  - Accessories > Applications > Terminal
  - type "lspci" and press enter
  - select all the information and use Shift-Ctrl-C to copy it, then paste it here (Ctrl-V). Note terminal uses different key shortcut.

---

### Post by kimberley on 2009-08-11
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
flower@flower-desktop:~$ 


Hope this is what you need - many thanks

---

### Post by tom66 on 2009-08-11
Have you installed Restricted Drivers (System > Administration > Hardware Drivers). Sometimes these are required for sound to work.

---

### Post by tom66 on 2009-08-11
Had another thought.

Try typing "arecord -l" into the terminal, that's 'arecord', followed by a space, followed by a dash, followed by a lowercase L. 

If it comes up with 'no soundcards found', let us know...

---

### Post by MrJoeyUK on 2009-08-11
Sorry for sort of interupting this thread, but I also have the same problem.. my sound is working fine, and it also works fine through my headset, but the mic doesn't work at all in sound recorder or skype.

In my 'recording' tab in volume control, all three are muted.. If I unmute them, close volume control and open it again they're all muted again. The same applies in my 'switches' tab.. the ExtMic isn't enabled, if I enable it.. it disables itself again when I re open volume control. I might have a totally separate problem, but I know this is a common problem for ubuntu and none of the fixes I've read about have worked.

Help?

And again.. sorry for hijacking the thread.

---

### Post by Buuntu on 2009-08-11
The problem might have to do with skype.  If you go to preferences > the audio tab, then if you set the input, output, and whatever else is there all to pulse it might work.  Have you tried testing the mic in sound recorder?  
 
Another thing you could do is go to Volume Control > Preferences.  Check everything and make sure nothing is muted in the volume control tab and that all the input or mic settings are set high.  
Also, in advanced (under volume control) try switching the input from front mic to just mic.

---

### Post by kimberley on 2009-08-11
flower@flower-desktop:~$ arecord-l



No poroprietary drivers are used on this system  

I am really impressed with all the help I am receiving:P

---

### Post by kimberley on 2009-08-11
I have tried setting everything to pulse, also checked that nothing is muted and changing from front mic to mic.  I have not been able to find sound recorder anywhere - how do I check this?

---

### Post by Buuntu on 2009-08-11
Applications > Sound > Sound Recorder

---

### Post by kimberley on 2009-08-11
flower@flower-desktop:~$ arecord-l

Sorry, I think I have got my response out of sequence!

---

### Post by kimberley on 2009-08-11
I was not able to record anything - message says `stream contains no data`

---

### Post by running_rabbit07 on 2009-08-11
What brand is the mic/headset?

---

### Post by Bramkaandorp on 2009-08-11
Assuming you are using a desktop computer, have you plugged the mic in the front or in the back?

I just switched, and it works! Plugging in the back that is. Of course your settings have to match, but when my mike was in the front plug, the mic didn't work in any configuration.

If you haven't tried this already, I strongly suggest you try it.

---

### Post by kimberley on 2009-08-12
This  is going to sound really dumb but I don`t know the make of the microphone as it is and integral part of my Acer monitor which is plugged into the back of my tower.  My speakers are Altec Lansing and I had no recording problems using MSN.

---

### Post by ngrieb on 2009-08-12
There is a check-box in the sound mixer that needs to be checked under switches. Have you checked the "Mic Capture" option?

---

### Post by kimberley on 2009-08-12
Yes, I have ticked the **Mic Capture Option but have just realised it reverts to mute** again with a cross through it .

Here are my sound playback settings in case these are the problem:
[B]Sound Playback - auto detect
Music and movies - auto detect
Auto conferencing - auto
Sound capture. Alsa - advanced Linux sound architecture [/B](I have triedall the capture settings but none work)
[B]Volume control:
Capture device HDA ATI SB Alsa mixer
Volume control preferences - all are ticked_[COLOR=Black] except[/COLOR]_[COLOR=Black] the IE settings[/COLOR]

*I am trying everything but feel I am lost in the jungle!!*
[/B]

---

### Post by kimberley on 2009-08-12
After reading through some more forum advice and following instructions, this is the  message I got:


flower@flower-desktop:~$ vumeter -r&
[1] 12637
flower@flower-desktop:~$ bash: vumeter: command not found
vumeter -r &
[2] 12640
[1]   Exit 127                vumeter -r
flower@flower-desktop:~$ [1]+  Exit 127                vumeter -r
bash: vumeter: command not found

I now have some background noise coming on `replay`but still no voice.

At least some progress I think?

---

### Post by kimberley on 2009-08-12
A friend suggested I plug a mike in a usb port to test for sound and the replay works ok!
So......... I think this must mean that the microphone in my Logitech Quickcam is not set up properly for Ubuntu and this is why Skype and Pidgen are not working.

Has anyone had this problem?:lolflag:

---

### Post by kimberley on 2009-08-13
After hours of trial and error entering different data I have now **solved the problem** of no sound from my** Logitech Quickcam Chat **- it seems so simple and here is the solution that worked for me on gnome.

Go to the Sound Device on Skype and use the following:

Sound In:  USB Device 0x46d:0x8da(hw:UOx46d 0x8da,0)
Sound Out:  pulse
Ringing:  pulse

Problem no. 2 remains!  Camera is working OK and I get a reasonably good picture but  on Skype all I get is green and red lines.

I will mark my mike problem as solved and search the forum for an answer to the camera problem.

Many thanks everyone for all of the above advice - I realise I may have misled some as I did not realise my problem was solely the web cam. :)

---

