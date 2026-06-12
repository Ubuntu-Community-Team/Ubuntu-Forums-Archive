---
title: "Kubuntu 9.04 doesn't select correct sound card. server 2008 uses correct one"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by darksidedude on 2009-06-27
Hey everyone. I'm having an issue here with this machine. in server 2008 it uses the correct sound card. (in windows its realtek HD) (in linux it is HDA Nvidia)

I have my other sound card in here for sound editing and what not. It is a sound blaster audigy ( dont know windows driver) in linux it is CA0106

windows will default to the sound card my headphones are pluged into. linux says Sound blaster or nothing. I don't know how to change it to use the HDA Nvidia. since this machine is heavy,80lbs. I cant keep moving the computer to move the headset. well I could, but I don't know any chiropractors:D 

hope you got the info you need thanks

---

### Post by mgmiller on 2009-06-27
I have often had problems when more than one sound card is installed, especially if 1 is built into the mobo and the other is pci or pci-e.

Try disabling the onboard sound in your bios.  That should force Ubuntu to use the pci card.  I assume that since you added the card, that's the one you want to use anyway.

If you want to use analog headphones from a front audio jack, etc.  You will need to unplug the front audio leads from your mobo and plug them into the appropriate spots on the sound card.

Good Luck.

---

### Post by darksidedude on 2009-06-27
thanks for the help, however I want to use the onboard one for ubuntu and the external one for Server 2008. if that is possible. or should I just start reaching into this box a pull it out. ( it has hotswap PCI and PCI-x)

---

### Post by mgmiller on 2009-06-28
The only times I have run across this is when someones computer came with onboard sound and the manufacturer added an external sound card either as an option or becasue they did not want you to use the onboard sound for some reason, so disabling the onboard card was the fix.

To try to use both sound devices simultaneously try the following:

A good place to start is the standard volume control in the top panel.  If you click on it and click the "Volume Control" button, you will get the master control panel with all the sliders.  At the top is the drop down for "Device".  You should be able to select between the sound cards from there.

Also, at the bottom of the window, is the preferences button which will allow you to select which sliders, switches and options are visible for each device.

Another place to look is in System > Preferences > Sound
On the devices tab, next to each line that says "Sound Playback" is a drop down, which by default is set to "Autodetect".  Click it's drop down arrow and see if you can select the hardware device you want for each purpose like sound events, music & movies and Audio conferencing.  Click the Test button to see if it works.

In addition, you may be able to get more flexibility with both sound cards if you install the pulse audio volume control gui.  It can select and configure all sorts of things in audio input and output streams.

```
sudo apt-get install pavucontrol
```That may allow you to select different hardware for different purposes.

I am curious why you need to use different sound cards for each OS.

**Edit:  I just noticed you are running kubuntu. ** The first 2 suggestions above are for Ubuntu.  I don't know if KDE even uses Pulse Audio, so the 3rd suggestion may not work for you either.  I have no experience with KDE, only Gnome.  

Have you asked at the kubuntu forums?
[http://kubuntuforums.net/](http://kubuntuforums.net/)

You could try running a live CD of Ubuntu to see how it resolves the sound issues.  I am fairly certain that KDE and Gnome have very different sound subsytems.

If you find that Gnome works, you can install it without losing kde.
You would then select which version you use from the login screen.

---

