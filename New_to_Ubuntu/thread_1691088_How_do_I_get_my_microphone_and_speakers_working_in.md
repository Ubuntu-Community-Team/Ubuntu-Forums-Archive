---
title: "How do I get my microphone and speakers working in Maverick"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by donnacipolla on 2011-02-19
Hello,

I am new to Ubuntu and have discovered that my speaker and microphone ports do not seem to be working. I ma running Maverick i386 on a Fujitsu Siemens Amilo laptop.
My hardware is :-

description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:c0000000-c0003fff

I cannot see any device shown for my microphone, screen-shot attached.

How do I resolve this?

---

### Post by bwallum on 2011-02-19
following lidex (thank you!)

First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog OR open a terminal with Applications>Accessories>Terminal and type in:
     Code:
      ```
gnome-alsamixer
``` 
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.

-----------------------
If gnome-alsamixer is not present - To install:
     Code:
     ```
sudo apt-get install gnome-alsamixer 
```
------------------------

Then go to 'Sound Preferences' (right click on speaker icon in top panel) to select and unmute your mic in 'Input' tab.

Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.

TIP: When you have 'Terminal' highlighted in the Applications>Accessories menu, left click on it, hold and drag to the top (or bottom) panel. That will give you a shortcut. You can use this for any main menu item.

---

### Post by donnacipolla on 2011-02-19
Thanks for your reply.

I have installed the gnome-alsamixer, and checked all the profiles were as you suggested but it doesn't seem to have made any difference. Still no mic seems to be detected.

I know the mic itself works as I can use it with no problem on other machines running the same system.

Does anyone have any other suggestions?

Please, I'm all ears! :)

---

### Post by deconstrained on 2011-02-19
The most common mistake (and it's easy to make) is that a channel/device has been left muted or with the volume all the way down. Double-check this in System->Preferences->Sound under the 'Input' tab, or in alsamixer (used through command line). I don't prefer gnome-alsamixer because in plain old alsamixer it's easier to see the settings of everything, but that's just me.

alsa can be quite confusing, and the controls differ from device to device, so you're not alone. Just have faith in yourself and keep experimenting, and you'll eventually get it to work ;-)

---

### Post by bwallum on 2011-02-20
When you run gnome-alsamixer do you get something like the screenshot attached? 

Check the mic settings when going to Edit>Sound Card Properties in the Gnome ALSA Mixer window. Check the mic and front mic (if you have that) boxes to ensure they are ticked. Then close the Sound Card Properties window.

In the Gnome ALSA Mixer window, is mic volume about two thirds and mute is unchecked?

---

### Post by bwallum on 2011-02-24
This an untested howto but may be relevant:-

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by Julian Luna on 2011-02-28
Please help my ubuntu 10.10 doesnt detect any sound hardware
I'll tell you fast what happened
My ubuntu 10.10 used to work well with sound
Tried this to make my microphone work
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
Untill the step where I need to write by second time
"cat /proc/asound/version"
Which answer was "No such file or directory"
I didn't see that this guide was for ubuntu 10.04
Now I tried a lot of things
My sound devices are both Azalia.
I tried installing by the package manager "libsdl-1.2debian-all" Or whatever its called
Just omg im really frustrated there is no sound at all

---

### Post by bwallum on 2011-03-01
> **Julian Luna said:**
> Please help my ubuntu 10.10 doesnt detect any sound hardware
I'll tell you fast what happened
Can we try a step by step approach. Please try to avoid doing too many things at once as it may complicate the solution.

Firstly, in the top panel, to the right hand side, you should see a speaker icon if you have audio hardware connected. Left click on the speaker icon and make sure it is not mute. If it is, unmute and test your speakers again.

---

### Post by Gato303co on 2011-03-01
I have the same problem, I already checked if the volume was muted and it wasn't.
When I go to Menu>System>Preferences>Sound I got this window in the Tab "Hardware"

See attachment "Pantallazo.png"

Looks like Ubuntu is not recognizing the Sound Card

And when I run on a terminal "gnome-alsamixer" I got a window in blank.  And if I try to enter in that same Window the option "Edit>Sound Card Properties" I got an error "Segmentation Fault" and the window crashes and close.

See attachment "Pantallazo2.png"

I don't know what to do, I have tried installing several OSS, reinstalled Pulse-Audio, and other Sound-Related packages, reboot pc but sound still doesn't work.

Please if somebody may help me solve this problem

---

### Post by bwallum on 2011-03-02
> **Gato303co said:**
> I have the same problem, I already checked if the volume was muted and it wasn't.
When I go to Menu>System>Preferences>Sound I got this window in the Tab "Hardware"

See attachment "Pantallazo.png"

Looks like Ubuntu is not recognizing the Sound Card

And when I run on a terminal "gnome-alsamixer" I got a window in blank.  And if I try to enter in that same Window the option "Edit>Sound Card Properties" I got an error "Segmentation Fault" and the window crashes and close.

See attachment "Pantallazo2.png"

I don't know what to do, I have tried installing several OSS, reinstalled Pulse-Audio, and other Sound-Related packages, reboot pc but sound still doesn't work.

Please if somebody may help me solve this problem
Looks quite a mess to me. Lets have a go at tidying up first. Go to System>Administration>Computer Janitor and agree to anything that needs fixing. 

Now we will check that the hardware is seen by the system. Open a terminal and enter ```
sudo lshw -c sound
```Post the output back in this thread.

---

### Post by Gato303co on 2011-03-02
> **bwallum said:**
> Looks quite a mess to me. Lets have a go at tidying up first. Go to System>Administration>Computer Janitor and agree to anything that needs fixing. 

Now we will check that the hardware is seen by the system. Open a terminal and enter ```
sudo lshw -c sound
```Post the output back in this thread.

Hello and thanks for answering my questions
 The output to the command "sudo lshw -c sound" is as follows:
________________________________________________
[I][FONT=Microsoft Sans Serif]arquitectura@arquitectura-desktop:~$ sudo lshw -c sound
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
       resources: memory:dff78000-dff7bfff[/FONT][/I]
_________________________________________________

I hope this information might help solve the problem

---

### Post by lidex on 2011-03-02
> **Julian Luna said:**
> Please help my ubuntu 10.10 doesnt detect any sound hardware
I'll tell you fast what happened
My ubuntu 10.10 used to work well with sound
Tried this to make my microphone work
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
Untill the step where I need to write by second time
"cat /proc/asound/version"
Which answer was "No such file or directory"
I didn't see that this guide was for ubuntu 10.04
Now I tried a lot of things
My sound devices are both Azalia.
I tried installing by the package manager "libsdl-1.2debian-all" Or whatever its called
Just omg im really frustrated there is no sound at all

I don't recommend compiling alsa that way as it tends to bork your audio if you don't know what you're doing. I recommend re-installing alsa at this point:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by bwallum on 2011-03-02
> **Gato303co said:**
> Hello and thanks for answering my questions
 The output to the command "sudo lshw -c sound" is as follows:
________________________________________________
[I][FONT=Microsoft Sans Serif]arquitectura@arquitectura-desktop:~$ sudo lshw -c sound
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
       resources: memory:dff78000-dff7bfff[/FONT][/I]
_________________________________________________

I hope this information might help solve the problem

Ubuntu sees your hardware. It is purely a software issue. Follow lidex.

---

### Post by lidex on 2011-03-02
@Gato303co
You're likely to have several issues. Did you completely remove OSS? I would suggest doing the reverse of this guide.
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
You'll need an alsa re-install but it won't take if OSS is still configured.

---

### Post by Gato303co on 2011-03-02
> **bwallum said:**
> Ubuntu sees your hardware. It is purely a software issue. Follow lidex.

You mean I should follow the suggestion Lidex gave to Julian Luna??[B][FONT=Arial][SIZE=2][COLOR=Black]
[/COLOR][/SIZE][/FONT][/B]

---

### Post by Gato303co on 2011-03-02
> **lidex said:**
> @Gato303co
You're likely to have several issues. Did you completely remove OSS? I would suggest doing the reverse of this guide.
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10511665](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10511665)
You'll need an alsa re-install but it won't take if OSS is still configured.

I am sorry I can't quite understand.  I don't know if I completely remove OSS.  The link you put redirects to this same thread, so what should I do? execute the command you suggested to Julian Luna?

---

### Post by bwallum on 2011-03-03
> **Gato303co said:**
> You mean I should follow the suggestion Lidex gave to Julian Luna??[B][FONT=Arial][SIZE=2][COLOR=Black]
[/COLOR][/SIZE][/FONT][/B]Yes follow lidex. I appreciate the link in lidex's quote is scrambled so don't let that confuse you. I don't want to add to the confusion so I would prefer lidex to resolve as he carries more knowledge than I do. In essence remove OSS then re-install alsa with:- ```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

---

### Post by Gato303co on 2011-03-03
> **bwallum said:**
> Yes follow lidex. I appreciate the link in lidex's quote is scrambled so don't let that confuse you. I don't want to add to the confusion so I would prefer lidex to resolve as he carries more knowledge than I do. In essence remove OSS then re-install alsa with:- ```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

I executed the code and rebooted, nothing changed, i executed again and still have no sound, got the same  pic I posted before in "Sound Preferences", I am starting to think I would have to reinstall Ubuntu.

---

### Post by Gato303co on 2011-03-03
Finally I got the sound back,  I used Synaptic and checked for complete uninstall all OSS related packages, reboot and finally i have sound again.

Thanks for all your help

---

### Post by bwallum on 2011-03-04
> **Gato303co said:**
> Finally I got the sound back,  I used Synaptic and checked for complete uninstall all OSS related packages, reboot and finally i have sound again.

Thanks for all your help
Well done! You have some stamina! Could you relay to anybody following, the OSS packages that you removed? Removing OSS is critical to recovery as you discovered and more detail in how to do it would be useful to those with similar problems. Name those files!

---

### Post by Gato303co on 2011-03-13
> **bwallum said:**
> Well done! You have some stamina! Could you relay to anybody following, the OSS packages that you removed? Removing OSS is critical to recovery as you discovered and more detail in how to do it would be useful to those with similar problems. Name those files!

Oops! I don't remember the packages I uninstalled, is it possible to find a log in Synaptic, so I can post the name of the packages?

---

### Post by Gato303co on 2011-03-16
> **bwallum said:**
> Well done! You have some stamina! Could you relay to anybody following, the OSS packages that you removed? Removing OSS is critical to recovery as you discovered and more detail in how to do it would be useful to those with similar problems. Name those files!

Hello again, yes Synaptic has a log (history) of packages installed and uninstalled.
Here I post a copy of the log
---------------------------------
Commit Log for Thu Mar  3 15:44:29 2011


Quitó completamente los siguientes paquetes:
audiooss
flashplugin-nonfree-extrasound
libao-ruby1.8
liboss-salsa2
libsox1b
oss-compat
oss-preserve
oss4-base
sox

Quitó los paquetes siguientes:
libao-ruby
libsox-fmt-alsa
libsox-fmt-base
oss4-gtk
------------------------------------

I hope this will be helpful for other people having similar problems with audio
Gato303

---

