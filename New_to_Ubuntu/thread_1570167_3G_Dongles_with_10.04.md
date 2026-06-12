---
title: "3G Dongles with 10.04"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Blojic on 2010-09-07
I would refer you all to:

[http://ubuntuforums.org/showthread.php?t=1427304&highlight=huawei+e122]("http://ubuntuforums.org/showthread.php?t=1427304&highlight=huawei+e122")
I've found that by typing ```
sudo apt-get install usb-modeswitch libusb-dev
```
sorts everything nicely and all's okay.

The trouble is that you need an internet connection to fix the problem/...
If, say, I'm installing a fresh Lucid onto a machine who's only connection with the outside-world is via the aforementioned offending dongle - is there a way I can do this?

(Please bare in mind that I'm thick, have been brought-up with MS-DOS, Windows et el, so a Disney (Mickey-Mouse) walk-though would be appreciated!)

Anyone's help would be appreciated. Cheers people.

---

### Post by Blojic on 2010-09-07
/... what I'm basically trying to say is How do I get```
sudo apt-get install usb-modeswitch libusb-dev
```onto a USB stick to install onto new machine if I cannot connect to Internet 1st? I appreciate that it's me being "dull" but my command of the terminal/console is "poor" - to say the least!

---

### Post by Hobgoblin on 2010-09-07
Neither of my USB dongles has needed modeswitch installing to work under 10.04, what model are you using?

I have had a thought, initially my vodafone dongle had to be plugged in before switching the laptop on for it to work.  This seems to have been fixed somewhere along the line but it's worth a try.

---

### Post by Blojic on 2011-11-27
just my 2d's worth: -

There's a script that I've come across called sakis-3g
[http://www.sakis3g.org/]("http://www.sakis3g.org/")
It has Modeswitch built-in and has served my very well in the past for the very reason that op mentioned - you can transfer it with a usb stick, make it executable and Bob's your uncle.

Blob

---

