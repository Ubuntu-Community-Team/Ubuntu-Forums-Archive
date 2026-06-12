---
title: "Ubuntu 18.04 - Toshiba AR9462 issues"
date: 2019-06-09
forum: Networking &amp; Wireless
---

### Post by tsnmouse on 2019-06-09
Hi all,

New to Ubuntu, and linux as a whole, so i'll need baby steps and some spoon feeding. Sorry in advance! :)

I recently swapped the OS on my old Toshiba Sat Pro C70-A-17L to Ubuntu 18.04, as a test platform for learning my way in to this world.
The install seems to have gone fine and everything seemed okay, until i unplugged the Ethernet cable and apparently the WiFi card doesn't want to play.

I did a little google-foo and rfkill shows the wlan hard-blocked, but I can confirm the fn+f12 switch is on, and the laptop shows a little orange light for the wifi.
(if i fn+f12 again the light goes out, and the item disappears from the rfkill list)

The wifi in these models should be the qualcomm atheros ar9462 - is this supported in the linux world?

Thanks for any help in advance, i'll keep searching the forums too.

Regards,

Martin 'Mouse'

---

### Post by jeremy31 on 2019-06-09
Moved to networking, please see the wireless script link in my signature and post results

---

### Post by tsnmouse on 2019-06-09
Done as commanded - Sorry for posting in the wrong area!
Wasn't sure if networking is hardware related or not!

[http://paste.ubuntu.com/p/ntZpQMv4FK/](http://paste.ubuntu.com/p/ntZpQMv4FK/)

---

### Post by jeremy31 on 2019-06-09
See if going into BIOS settings and reset to default clears the hard block, or you may have to power down, remove the power cord and battery and press the power button for 20 seconds

---

### Post by tsnmouse on 2019-06-09
I'd done the reset to default before, so pulled out the battery and held the power button down.... it seems to work now.... showing up as "?" in the top right, but seems to get back to this webpage okay.

Can I ask what the issue was? I was wondering if it was something like LAN/WAN switching but couldnt see a setting for it in the BIOS (BIOS on here is really sparse it turns out)

Seems like my education starts here!

---

### Post by jeremy31 on 2019-06-09
BIOS is where the OS gets the hard block info in most cases, it just needed to be reset.  See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) for some info to make Ubuntu work well with that wifi card

---

### Post by tsnmouse on 2019-06-09
Man, I thought the Reset to defaults would of done that already.
Time to read up on the battery trick... thanks again! 

Is there an up-vote / reward / acknowledge system on these forums, respect where respect is due :)

---

