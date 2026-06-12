---
title: "Wireless disappeared from Network Manager (nm-applet)"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by buggi22 on 2009-07-20
I used to be able to connect easily to wireless networks via the Network Manager (nm-applet), but my wireless access recently stopped working.  This happened right after my computer froze pretty badly (in a gnome-terminal, I was running some inefficient Java code I wrote -- it took up so much of my CPU that it froze everything else that was open, including Firefox).

My computer no longer connects to the wireless network automatically, and it does not show up in the menu when I click on the nm-applet notification icon.  However, the wireless network DOES still show up under "wireless" under nm-applet's "Edit Connections."

I'm not sure if the following will help, but here's my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
```Similarly, here's what I get from iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.


```I don't know what to make of the above output, because I know nothing about configuring wireless, but I saw that people in similar threads posted this kind of information in order to get help.  :)

Also, in case it might help to diagnose the problem... I noticed some other strange symptoms right after the crash: The icons on the notification area changed right after I restarted.  Specifically, the nm-apps icon, the laptop battery icon, and the volume control icon all look different.  They look "older" in some sense -- not as smooth or fancy looking as they were before... I didn't change anything, so I think the crash might have had something to do with it.

Any help tracking down this problem would be much appreciated.

(Also, if anyone could explain the output I'm seeing above, as well as the related utilities, that would be amazingly helpful!)

====

Update: Might also be relevant that I'm using a Dell Mini 12 (LPIA architecture), with pretty much everything at default settings from Dell.

---

### Post by nothingspecial on 2009-07-20
Few things you can try

Get a wired connection and install wicd. It is an alternative network manager and sometimes fixes peoples wireless problems.

See if any errors are displayed when typing dmesg

Post some more imformation about your wireless card a see if anyone else has had these issues

```
sudo lshw -C network
```

---

### Post by buggi22 on 2009-07-20
Thanks for the reply.

Re: #1, thanks for the suggestion.  I'll definitely keep it in mind if I give up on Network Manager... For now, though, I'm still stubbornly holding out hope, because I know it used to work on this hardware.  :)

For #2, I can't find anything obviously wrong, but I'm not familiar with using dmesg... any suggestions on what to look for?  The only part that looks related to wireless or ethernet is the following:
```

[   26.816750] buffer underrun 0x0
[   33.751795] r8169: eth0: link up
[   33.751816] r8169: eth0: link up
[   35.659333] hda-intel: Invalid position buffer, using LPIB read method instead.
[   37.182804] eth0: no IPv6 routers present
```For #3, I apparently don't have lshw.  I get the error "command not found", even when using sudo.  Is there any other way to track down my hardware information & configs?

---

### Post by buggi22 on 2009-07-21
Also, another interesting development...

I opened up the menu item System > Administration > Hardware Drivers (not sure if this is specific to Dell, GNOME, or something else...), and I noticed one entry there -- for my wireless card ("Broadcom STA").  It is currently listed as "enabled" but also "not in use".  If I disable it and re-enable it, it claims to be in use, but wireless networks still don't show up in Network Manager.  At this point, Ubuntu tells me I need to restart; however, when I do this, the Broadcom wireless status goes back to "enabled" but "not in use".

Does this give anyone an idea how to diagnose this problem?

---

### Post by pranjal on 2010-01-27
If yo are still looking for solution::
Check if you have some "hardware key" to enable wireless. If yes, enable wireless by toggling or pressing the key as the case may be. Normally all laptops have hardware enable key.

---

