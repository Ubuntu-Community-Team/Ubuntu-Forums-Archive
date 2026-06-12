---
title: "can't create bootable USB"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by JamieWrites on 2010-12-18
Hi,

I'm trying to resize my partitions using GParted and, to do this, I've tried both PendriveLinux and UNetbootin, on 2 different USB drives, and neither has worked.

What am I doing wrong? Is there a step I'm missing? 

Here's what I've done so far:

[LIST=1]
[*]using [PendriveLinux instructions]("http://www.pendrivelinux.com/install-gparted-on-usb-flash-drive-using-windows/"), I've modified my USB
[*]I've plugged the USB into my netbook
[*]In the BIOS, I've gone to the Boot page and set the 1st Boot Device to 'Removable Device'
[*]I've hit save and restart
[/LIST]
About the only thing that is making me wonder is that, in the BIOS Boot menu, both options - the HDD and the Removable Dev. - both have parentheses [ ] around them, and the message on the side menu states 'A Device enclosed in parentheses has been disabled in the corresponding type menu.'

Is there something there I need to change? I've tried everything and had no success.

---

### Post by Ichtyandr on 2010-12-18
When you restart, do you hold pressed any button, like F8 or F12 or maybe Shift or Ctr-Esc depending on your laptop?

exactly what are you trying to do? do you try to create a bootable Ubuntu Live USB?
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) shows how to do it on Windows or Linux
Also you can use unetbootin for that:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Ubuntu Live USB already has gparted installed so no need for gparted live cd

---

### Post by amjjawad on 2010-12-18
Check [your other thread]("http://ubuntuforums.org/showthread.php?t=1647784") that you created previously, I have posted a link for you so try that one.

Starting a new thread was unnecessary as this will definitely confuse you and us. You'll end up posting the same info in both threads.

---

### Post by wilee-nilee on 2010-12-18
If the thumb is loaded correctly sometimes you need to use a per-session key prompt to get a boot from menu even though the bios has the usb first. Mine is f12 at power on, it brings up a post bios; boot from menu your key prompt may be a different key.

---

### Post by Ichtyandr on 2010-12-18
Oh from another thread I figure you use ASUS netbook, so basically its "boot booster" could skip that step for you. So instead of restarting you want to shut down. Then when you start keep pressed "Ctr" and ESC keys "together" this should work

---

### Post by wilee-nilee on 2010-12-18
> **Ichtyandr said:**
> Oh from another thread I figure you use ASUS netbook, so basically its "boot booster" could skip that step for you. So instead of restarting you want to shut down. Then when you start keep pressed "Ctr" and ESC keys "together" this should work

I think it is just esc. We will find out eh.;)

---

### Post by C.S.Cameron on 2010-12-18
On my EEE just pressing Esc gives boot options.

---

