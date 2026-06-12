---
title: "rt73usb driver and WPA"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2007-08-08
Hi everyone,

I have been trying for a long time to make my DWL-G122 rev C1 dongle connect to my WPA-encrypted network.  This stick is supported by the rt73usb driver that's included by default in the Feisty kernel, but unfortunately, no matter what I do, I can't get it to connect to my network.  I've edited /etc/network/interfaces according to the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73), and I've also tried to negotiate the WPA passphrase using iwpriv, as the instructions in the README for the rt2x00 driver say you might have to do.  Nothing has come close to working, however.

This stick definitely supports WPA; I can use it with no problems in Windows.  I can also connect to WEP networks with it using the rt73usb driver, but WPA is a different story.

I understand that rt73usb is not 100% stable yet, so I don't if there's a bug with it or what.  If anyone has managed to use the rt73usb driver to connect to a WPA network, I would really appreciate an outline of what you had to do.

Alternatively, the legacy driver for this card, which is called just rt73, is supposed to work flawlessly with WPA by using wpa_supplicant (rt73usb does not support wpa_supplicant, it seems; that's why I tried using iwpriv).  However, from what I've read, the rt73 driver doesn't support SMP, which is the kernel I'm using.  But if anyone knows of a patch or a later version to make rt73 work on an SMP kernel, that link would be really useful as well.

If I really have to, I guess I could just install the 32-bit kernel and use the rt73 driver, but I would be disappointed if I have to use that kernel after having spent so much money on a fancy 64-bit processor.

Thanks very much for any help.

---

### Post by kevdog on 2007-08-08
See the following thread:

[http://ubuntuforums.org/showthread.php?t=40023](http://ubuntuforums.org/showthread.php?t=40023)

---

### Post by pytheas22 on 2007-08-08
Thanks for your response.  Are you sure that's the right link, though?  It's about playing mp3's, which doesn't have much to do with the rt73usb driver :)

---

### Post by kevdog on 2007-08-08
That's weird -- try this then:

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

I think the last number got cut off on the original post

---

### Post by pytheas22 on 2007-08-08
Thanks again...however, I've been all through that how-to already.  It doesn't work because it has you download the rt73 driver (the legacy one) to replace rt73usb (the one included by default in Feisty).  rt73 doesn't work with SMP kernels; hence, when I compiled it and loaded it with modprobe, my card wasn't recognized.

Thanks for the help anyway though; if anyone has any other ideas, like where to get an rt73 driver that will work with SMP, please let me know.

---

### Post by pytheas22 on 2007-08-09
Actually I'm reading now at [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21944&sid=427d5c23ccc04346eac894a00bd3b55a](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21944&sid=427d5c23ccc04346eac894a00bd3b55a) that the latest rt73 legacy driver from serialmonkey should support SMP and 64-bit, so I will try using that driver again and see what happens.  I tried it once and it didn't recognize my card, but maybe I didn't try hard enough.  Will post results.

---

### Post by kevdog on 2007-08-09
Keep us posted on the results -- Im curious myself

---

### Post by pytheas22 on 2007-08-09
Finally got it to work.  The how-to at 
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) actually is right; I was being an idiot...because I had originally configured a (non-working) interface called wlan0 using the rt73usb driver, when I tried to bring up wlan0 using the rt73 legacy driver from serialmonkey after compiling it, it didn't work, because with rt73usb blacklisted, there was no driver to recognize the wlan0 interface.  I had been blaming my SMP kernel for this, but it was all just my fault.

Eventually I typed iwconfig and realized that the interface to which the rt73 driver was attached was called wlan1.  So I did ifconfig wlan1 up, and using RutilT (GUI configuration interface available from serialmonkey), I can connect to my WPA network and get an IP address.  For some reason I can never get an IP on the first try, even though my computer is less than three feet from my router, but it always works on the second try, so it's good enough.

Thanks for your help; sorry for my ignorance at first.

PS, does anyone have any ideas why the new rt2x00 drivers are now merged with the kernel if they don't always work???  I would have saved a lot of time if rt73 had just been in the kernel to begin with, instead of this unstable rt73usb nonsense...

---

### Post by kevdog on 2007-08-10
In Gusty, supposedly the new drivers will be included in the kernel

---

### Post by pytheas22 on 2007-08-10
If that's true, I hope these drivers become stable before October!

---

