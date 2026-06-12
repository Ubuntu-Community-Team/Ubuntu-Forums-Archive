---
title: "How do i unblacklist my ath_pci wireless thingy"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by 30857 on 2008-11-28
Well i found a tutorial on how to install madwifi and on a previous tutorial that did not work i had to blacklist my ath_pci wireless thingy(not quite sure what it is). So my question is how do i unblacklist this ath_pci wireless thingy on ubuntu 8.10?

P.S. Please use complete beginner talk if possible I am a ubuntu 8.10 newbie

---

### Post by 30857 on 2008-11-28
Can someone please help i really need this....

Thank you hopefully in advance

---

### Post by kevdog on 2008-11-28
Just delete the line in the /etc/modprobe.d/blacklist file.  It really is that easy!!

---

### Post by 30857 on 2008-11-29
Where and how do I do that?

Thank you in advance

---

### Post by J172 on 2008-11-29
Thats a bad idea.
What you need to do is search the /etc/modprobe.d/blacklist file.

type this to open it in a Graphical text editor

***gksudo gedit /etc/modprobe.d/blacklist***

Use the find feature to the device being blacklisted. (ath something I would assume). If it is not there, then I am at a loss.

If you would like to try it command line style
open up terminal, type (if it fails add sudo in front of grep)
***grep ath /etc/modprobe.d/blacklist***
 it should show you much faster if there is an entry in there. Then you can edit it using the gksudo gedit command above.

If it doesn't display a result (grep searches for strings (by default) in files) from the blacklist file, look for any other name the device might be under. 

Don't delete files in (any OS really) Linux if you're unsure of what could happen. There are many other entires in there that save you sanity, processing power, time, etc. For example, my blacklist file contains many things

```
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

#silence the system pc speaker
blacklist pcspkr
```

Thats just an excerpt. Have a look through, maybe just to learn more. If you're 100% ABSOLUTELY SURE that none of it would effect you, you can AT YOUR OWN RISK delete the CONTENTS. Just highlight it all and press delete then save, at your own risk. I'd not advise this though.

---

### Post by 30857 on 2008-11-29
I kinda need to unblacklist it to get my wireless working so how much do i delete(I only want the ath_pci to be unblacklisted)?

---

### Post by J172 on 2008-11-29
If the device that you were looking for isn't there then I'd say its not blacklisted.
Try this
[http://wiki.debian.org/WiFi/ath_pci](http://wiki.debian.org/WiFi/ath_pci)
Not sure if the above will work, it might. Debian is what Ubuntu is based upon. The two distributions share much in common.
and this
[http://ubuntuforums.org/showthread.php?t=111467](http://ubuntuforums.org/showthread.php?t=111467)

---

### Post by 30857 on 2008-11-29
The device I am looking for is there so what do i do to unblacklist it?

---

### Post by J172 on 2008-11-29
Wait a minute.

I think I linked you to the tutorial that you tried. Maybe not. 

However, if you post the tutorial you tried, it might be easier to help you.

Do you still have it?

Why did it tell you to blacklist it? That disables the device as far as the OS is conerened.

NEVERMIND Just realized WHAT you said, sorry its 2am.
To unblacklist it, delete the entry in the blacklist file and save it. Restart.

---

### Post by 30857 on 2008-11-29
Here is the thing what do I delete to delete that ath_pci and how much do I delete:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
“blacklist ath_pci”
blacklist ath_pci

---

### Post by J172 on 2008-11-29
> **30857 said:**
> Here is the thing what do I delete to delete that ath_pci and how much do I delete:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

[B]# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
&#8220;blacklist ath_pci&#8221;
blacklist ath_pci
[/B]
Everything in bold.

You may wish to review this page
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/246969](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/246969)
You might be unaffected.
It was probably automatically generated by Ubiquity (Ubuntu Installer).

---

### Post by 30857 on 2008-11-29
I did that and hit save now it says i do not have the necessary permission to save the file /etc/modprobe.d/blacklist.

Please HELP!

---

### Post by J172 on 2008-11-29
Go to terminal
type
**gksudo gedit /etc/modprobe.d/blacklist**
enter your password
Delete the bit that was in bold
Press save
Reboot.

---

### Post by ugm6hr on 2008-11-29
The advice you have been given is correct.

Nevertheless, since you are a complete beginner, I offer the following advice:
Make sure you are asking the correct question.

There may be an easier way to get your wifi working.  Starting with the output from the command below may let us point you towards an appropriate How-to:
```
lshw -class network
```

---

### Post by gnusci on 2008-11-29
I advice you to make a backup before any changes:

**$ sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist-date-here.bkp**

You can get your file restored with:

**$ sudo cp /etc/modprobe.d/blacklist-date-here.bkp /etc/modprobe.d/blacklist**

---

### Post by J172 on 2008-11-29
> **gnusci said:**
> I advice you to make a backup before any changes:

**$ sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist-date-here.bkp**

You can get your file restored with:

**$ sudo cp /etc/modprobe.d/blacklist-date-here.bkp /etc/modprobe.d/blacklist**

Always wise advice. This is a do as I say not as I do one for me, I never back up before I mod, a BAD IDEA and I don't learn it -- ever. gnusci has the right idea here!

ugm6hr,
 I'm a complete beginner, I didn't know about that command. I've picked Ubuntu up at a fast pace (faster, WAY faster) then I thought I would. I started reading your post and was like "I thought thats how it went, I was sure of it" glad to see I wasn't giving the wrong advice. This thread has become a bookmark for me -- checking it when I can.

30857 -- has this worked for you? Any of the help we've given?

Thanks gnusci and ugm6hr. I'll remember to start telling people to backup. Configuration files are not the easiest for memorizing what you've changed -- me and Apache have had a round or 67.

This my friends, is what Ubuntu is all about.

---

### Post by ugm6hr on 2008-11-30
@J172:
As you say - this is what the community is for.

The solution to the question asked is as you have described.  However, I would normally advise using # at the start of the lines rather than deleting, since it is then easy to undo your edits (and makes backup less necessary).

Nevertheless, it is an unusual question for a beginner to ask (since it is very specific).  It is often more sensible to start at the beginning (with a "Atheros wifi not working" thread), rather than something that may just lead them round in circles.

Hence, my statement about asking the right question.

@30857:
Hope you get this working.  If you are struggling, you will see that there are plenty of people on hand to help.  The lshw command I suggested, together with a link to whatever How-To you were using would allow us to resolve this issue for you.

---

