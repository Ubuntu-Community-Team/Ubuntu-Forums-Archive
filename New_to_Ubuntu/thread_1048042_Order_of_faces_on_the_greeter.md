---
title: "Order of faces on the greeter"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Dirjel on 2009-01-23
I set up another user on my computer, but now when I first boot up, the other user's account shows up above mine in the face list.  It's my computer, and I want my name to be on top.  How can I rearrange it?

I tried simply switching the order of the names in /etc/passwd, but that didn't do it, and I tried virtually every option in the "Login Window" properties.  Is the order of the names caused by the User ID number?

On a side note, I can't set a .ogg sound to the login ready option.  It just blasts out super-loud static.  A .wav worked fine, though, strangely enough.

Anyway, any help would be appreciated.

---

### Post by Dirjel on 2009-01-23
I tried a bunch of different things.

Looks like the faces are sorted alphabetically by username.  I set up a new user, changed the ownership of the home folder, and got rid of the old one.  Everything's good now.

...Except for the static noise thing.  That's weird.

---

### Post by halovivek on 2009-01-23
can you post the output ?
code
lspci

---

### Post by Dirjel on 2009-01-23
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

I can play .ogg files with rhythmbox, totem, and off of the internet (Firefox/Pandora).  It just won't work on this one thing, which is weird.

---

### Post by SunnyRabbiera on 2009-01-23
so you know with the login sounds only .wav works

---

