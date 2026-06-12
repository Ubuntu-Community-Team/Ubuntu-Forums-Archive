---
title: "Bluetooth preferences dialog a bit confusing."
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by K_V_B on 2008-11-19
Hello,

System -> Preferences -> bluetooth brings up a dialog where you can set bluetooth preferences.

This dialog will show a list of "known devices". Below this list are four buttons. 
- A plus button which adds a device.
- A "trashcan button which removes a device.

And then two other buttons.
- A button with a plug/socket symbol.
- A button with a four pointed star.

What is not there is any form of hint or documentation that explains to the user what these buttons do. Does someone know? I've searched the ubuntu doc, and I've searched the bluez website, but without result.

Does anybody know more?

---

### Post by Chonnawonga on 2008-11-23
*bump*

Seconded. What are these buttons and why aren't we told?

For that matter, what happened to the "Services" tab? I can no longer use my cell phone as a remote control. :mad:

---

### Post by John Jason Jordan on 2009-01-11
> **Chonnawonga said:**
> Seconded. What are these buttons and why aren't we told?

I wonder if either of you ever figured out the answer to what the icons in System > Preferences > Bluetooth mean.

When I used Hardy I had a bluetooth mouse that would disconnect every couple of days. I could reconnect it from the command line with "hidd --connect <address>." I also have a bluetooth headphone (Sony BT50) which worked perfectly in Hardy.

After upgrading to Intrepid the mouse now works without disconnecting. But the headphones no longer work at all. And "hidd --search" does not reveal anything - not even the mouse. The System > Preferences > Bluetooth dialog box shows the headphones with a gold star and a key next to them. I cannot figure out what those icons mean. If I click on the + button I have the option of adding a device, but the only device that appears is the mouse. You have to select a device in that dialog box to configure it and the headphones do not appear.

I'd try "hidd --connect <address>" if I knew the address of the headphones. But when I do "hidd --search" it does not display the headphones (or the mouse). Wish I knew how to find the address of the headphones.

I've searched and searched the forums but what few posts I have found about this issue died without any solution.

---

### Post by John Jason Jordan on 2009-01-24
I finally got my bluetooth headphones paired up, but can't get sound out of them. There are several how-tos, but they all require a pactl command to tell pulseaudio that the headphones exist. I've been working for days to get that command to work, but every option I have tried just hangs pulseaudio with a tiemout error message on the pactl command.

One of the things that the how-tos mention is to go into the bluetooth configuration dialog box and enable audio services. I have Intrepid and there is no such option.

Does anyone know how to enable bluetooth audio services in Intrepid?

---

### Post by DellMiniNewbie on 2009-02-04
I agree that the new preference screen is confusing and for some reasons I have issues with my device pairing, it takes forever for my system to notice it, I seem to be able to speed things up by using hcitool to scan and cc it, but it's annoying. Anyways, that's not why I write. I think you may be able to help with this info:

It seems that with the new bluez (v4), the bluetooth headsets get configured in a different way in alsa after pairing. Try this command:

aplay -D headset /usr/share/sounds/somesoundfile.wav

That works for me to get sound out. I still haven't figured out how to have the sound from all the applications go through this magical "headset" device that is created automatically when my headphones pair up, but I thought I'd let you know about what I found.

Good luck!

---

### Post by raymondvillain on 2009-02-04
This is all very familiar.  I'm trying to get my bluetooth headphones to wrok.  When I try the command

pactl load-module module-alsa-sink device

all's I get is "Failure:  Module initialization failed"

and no services tab in the bluetooth icon.

Any help would be greatly appreciated.

---

### Post by Endolith on 2009-06-03
Still no one can figure out what these buttons do?  This is a major fail.  Isn't there any documentation anywhere as to what these do??

[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/383438](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/383438)

---

### Post by J-D-Cronin on 2009-06-10
I'm guessing here, but it seems that the first button plus '+' sign(Red) adds a device. The "plug" (blue) tells the computer to connect to the highlighted device (see that I'm connected to the Stowaway mouse by the icon to the right). The 'i' icon (green) is the one I'm not sure about - I think it might control whether your computer automatically connects to the device. The last one (yellow - trash can) probably deletes the bluetooth device.

Those are my best guesses, maybe someone can give us a definitive answer.

-Jordan

**Edit: I'm running 9.04**

---

