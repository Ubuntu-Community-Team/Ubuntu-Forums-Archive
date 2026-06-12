---
title: "suddenly, no wireless detection and no sound! Help me to not throw my laptop away!"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by endtheembargo on 2009-05-14
I turned my computer on today, and there was no internet connection and also I couldn't control the volume (it's turned all of the way down).

Here are the specs of my computer:

toshiba a135-s4427
Intel core duo processor T2250
802.11a/b/g wireless-LAN
I'm running Hardy 8.04 

Internet problem:

I think the problem is that the computer is no longer detecting that I have a wireless device, and thus won't display any possible wireless networks for me to connect to - but I can't be sure. I'm not very computer saavy and I need to be walked through this very simply.

Sound Problem:

On the control panel the volume icon has a little "x" next to it. I can't seem to adjust the volume anymore from the computer. When I double click the icon I get the following message:
"No volume control GStreamer plugins and/or devices found."

Help me ubuntu community, you're my only hope!

Ondine

---

### Post by TheDilettante on 2009-05-14
Re: wifi, let's start simply.  What kind of wifi card are you using?  Is there an external switch on the computer?

Re: sound,  what kind of card are you using? Also, go into Synaptic (system/admin/synaptic package manager) and search for Gstreamer.  List the packages you have installed.

---

### Post by endtheembargo on 2009-05-14
Ok. When I searched for gstreamer in the synaptic package manager, I found lot's of them. Which ones are you looking for/what specifically am I looking for?

Also, where can I look up what wifi card and sound card I have?

---

### Post by oldrocker99 on 2009-05-14
Use lspci in the terminal for a list of all the devices on your laptop.

That's a place to start. Double-click the speaker icon to open the minimixer. See if you can move the sliders up.

If your Linux wireless drivers don't work, you can use a program called ndiswrapper which allows you to use a Windoze driver. I use it on my Toshiba laptop and it works FAR better than the Linux driver.

:guitar:

---

### Post by endtheembargo on 2009-05-14
Unfortunately I can't double click the speaker icon because when I do, it tell me that I don't have gstreamer or I don't have my sound card configured.

when I typed lspci into the terminal it tells me that my audio device is Intel corporation 82801G (ICH7 Family) High def. audio controller. I can't seem to figure out from the list of other stuff what would be the wireless device, if it's even listed.

---

### Post by NightwishFan on 2009-05-14
Did you have sound when you first installed Ubuntu?

As for wireless, do as the previous poster did and make sure the card is physically turned on. If so we can proceed further.

---

### Post by sim-value on 2009-05-14
Everything did work correctly before - on Ubuntu and its just today that this problem occurs right ?

---

### Post by LowSky on 2009-05-14
open a terminal type this command

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by endtheembargo on 2009-05-14
Yep, everything was working fine, until today. The wireless card is turned on I checked. There is  a little orange light indicating it's on.

I tried to type "sudo apt-get update && sudo apt-get upgrade" into the terminal and I got a message saying that it failed to fetch several things.

Thank you everyone for your patience and your help.

---

### Post by rustutzman on 2009-05-14
It sounds like you have more issues than just ubuntu. Try this if you haven't already. Shut down the laptop and remove the power connection. Remove the battery. Wait about five minutes than replace the battery. Replace the power connection and turn the laptop back on. Check to see if everything works. If not do you have the installation cd? Put it in an just boot to the live cd and see if things work. If no change post back and let us know.

Russ

---

