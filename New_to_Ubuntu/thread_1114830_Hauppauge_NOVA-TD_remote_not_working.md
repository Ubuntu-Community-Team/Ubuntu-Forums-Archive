---
title: "Hauppauge NOVA-TD remote not working"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by abjt on 2009-04-03
Hi,

Can someone help me please?

The problem:
Have installed Hauppauge Nova-TD (the USB one) on my HTPC but the remote doesn't seem to be working. Have tried almost all suggestions I could find on the forum but nothing seems to have done the trick.

Details:
 - Ubuntu 8.10 - 
 - Hauppauge WinTV Nova-TD - TV tuner works fine. Remote doesn't.
 - MythTV 0.21

I can see the TV and change channels, but not with my remote.
- Have LIRC installed, 
- can see entry in dmesg (something like "IR remote in usb receiver...")

The remote is the size of a credit card. I think the model no. at the back is something like DSR-0112 (not exactly sure). I am in the UK.

BTW I am very new to Ubuntu - have been on windows and previously DOS most of my life

Please help... can't figure out what I need to do.

ta

---

### Post by AlecJ on 2009-04-03
[http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php)

This is one of the best guides I have found for the remote.

You may have to select another type of remote in Mythbuntu control center, they are normal just badged copies of each other.

---

### Post by abjt on 2009-04-03
Alec,

I had installed MythTV using that guide. I think the remote got installed, but it doesn't quite work.

Will try going thru the instructions again.

ta

---

### Post by AlecJ on 2009-04-03
I had no end of trouble with any Lirc remote, I got one with every tuner I have 6 and there all crap!

I bought this one in the end
[http://www.letsautomate.com/11992.cfm](http://www.letsautomate.com/11992.cfm)

Totally transformed the machine, can't tell you how relaxing myth is to use now.
Let me know if you go down this route I can let you have my lircrc file with all the buttons working, it is also programed to switch th TV on and off and can restart the frontend when it crashes.

---

### Post by freak42 on 2009-04-03
does the command 'irw' connect to lirc and output anything when you press keys on your remote?

does your remote perchance produce some output in a text window if you press for instance numbers or cursor keys?

---

### Post by schmidtbag on 2009-04-03
I have a PCI TV/FM tuner and that too works fine (mostly, I get sound issuess with S-video and composite) and it also has a remote.  The remote works but only the basic keys you'll find on any remote.  The problem is, it can't be detected by lirc, so therefore my remote is  considered useless.  What I would recommend is find a USB IR receiver and connect LIRC to that.  I haven't done that yet myself but I will, they're cheap and can work on any computer.  Its a good last resort problem

---

### Post by freak42 on 2009-04-03
> **schmidtbag said:**
> I have a PCI TV/FM tuner and that too works fine (mostly, I get sound issuess with S-video and composite) and it also has a remote.  The remote works but only the basic keys you'll find on any remote.  The problem is, it can't be detected by lirc, so therefore my remote is  considered useless.  What I would recommend is find a USB IR receiver and connect LIRC to that.  I haven't done that yet myself but I will, they're cheap and can work on any computer.  Its a good last resort problem

hal is picking up your remote before lirc can and therefore your remote acts like a keyboard.. maybe this thread can help you:
[http://ubuntuforums.org/showthread.php?t=1050558](http://ubuntuforums.org/showthread.php?t=1050558)

hth

---

### Post by schmidtbag on 2009-04-03
hmm interesting, I don't have all the stuff with me right now but I'll definitely get to trying this out, thanks.

---

### Post by abjt on 2009-04-03
> **freak42 said:**
> does the command 'irw' connect to lirc and output anything when you press keys on your remote?

does your remote perchance produce some output in a text window if you press for instance numbers or cursor keys?

Tried irw... just comes back to command prompt.. nothing.

i now remember it does produce something in the syslog. don't remember exactly message but something on the lines of "unrecognised key pressed......" or something like that

---

### Post by abjt on 2009-04-03
> **AlecJ said:**
> I had no end of trouble with any Lirc remote, I got one with every tuner I have 6 and there all crap!

I bought this one in the end
[http://www.letsautomate.com/11992.cfm](http://www.letsautomate.com/11992.cfm)

Totally transformed the machine, can't tell you how relaxing myth is to use now.
Let me know if you go down this route I can let you have my lircrc file with all the buttons working, it is also programed to switch th TV on and off and can restart the frontend when it crashes.

Hmmm.... you seem to be reading my dreams..:lolflag:
Will definitely want to look into this. Will do so when I get home tonight.
thanks a lot..

---

### Post by abjt on 2009-04-03
> **abjt said:**
> Alec,

I had installed MythTV using that guide. I think the remote got installed, but it doesn't quite work.

Will try going thru the instructions again.

ta

it worked !!! Went thro the guide again... the only change I made was in the /etc/lirc/hardware.conf.
Added "event6" to the Device - actually in the parker guide, it refers to DEVICE while my hardware.conf had REMOTE_DEVICE. Still it worked !!

Am trying it out to check what all works. So far, the navigation ( i.e. up-down etc) and playing (forward, back etc) works.
thanks all for your support guys.:popcorn:

Just while at it. Have a couple of questions if you can help with

1. The sound on mythtv sometimes "squeals" and "squelchs". It is quite irritating and spoils the fun. Any ideas why this might be happening and what can I do to fix it?
2. I just checked in the system logs and found a few entries that said "ppdev0: unregistered pardevice" and also a few "kernel: [  860.252600] dib0700: Unknown remote controller key: 00 01 06 f9"

any suggestions on these?

again... thanks for the help.

---

### Post by AlecJ on 2009-04-03
Great, 

That device number will change if you unplug the keyboard or mouse.

My PC lives under the TV and has no keyboard or mouse, I use VNC from one of the other pc to it when needed. 

You now have to build your lircrc file from the button names displayed in "irw" and the Key binding within mythbuntu.

sudo nano ~/.mythtv/lircrc

---

### Post by abjt on 2009-04-03
> **AlecJ said:**
> Great, 

That device number will change if you unplug the keyboard or mouse.

My PC lives under the TV and has no keyboard or mouse, I use VNC from one of the other pc to it when needed. 

You now have to build your lircrc file from the button names displayed in "irw" and the Key binding within mythbuntu.

sudo nano ~/.mythtv/lircrc

will give it a go... trust, if I copy-paste from your post it should do the trick?

---

### Post by AlecJ on 2009-04-03
> **abjt said:**
> will give it a go... trust, if I copy-paste from your post it should do the trick?

yes, that will open your lircrc file, in the nano text editor with super user rights, where you can edit what the buttons do when pressed.

If you have another terminal running irw you will find the button names as you press the buttons. (from lircd.conf)
If there are "dead or nameless buttons" you will need to edit the /etc/lirc/lircd.conf file and add the code (from irw) with a name per button. You may have to restart lirc after this to read to changes.

The supplied Lircrc  file only has the basic buttons and commands assined.
You will need to add any new buttons on the bottom of the file, the layout is clear to follow.
Don't re-order the file layout it's not sequential and it likes it that way, I did and there was fun infact, back it up before you start

sudo cp ~/.mythtv/lircrc ~/.mythtv/lircrcback

will copy the lircrc file to lircrcback in the same folder, with super user right's cos it's not your folder.

to restore the original file use

sudo cp ~/.mythtv/lircrcback ~/.mythtv/lircrc

this will overwrite the messed up file.

The list of key commands for myth are assigned in myth Utilities/Setup - Edit Keys
or you can get them from Mythweb when you point a browser from another PC on the network at your box's ip address.

The biggest problem you will find is "miss presses" i.e you press button A, but myth gets command B. Which will drive you mad and is what made me buy the mce remote.

for the sound here is a great guide.
[http://www.mythtv.org/wiki/Sound_Troubleshooting](http://www.mythtv.org/wiki/Sound_Troubleshooting)

---

