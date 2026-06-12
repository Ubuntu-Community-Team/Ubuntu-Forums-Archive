---
title: "Ethernet/modem conflict"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by scooby on 2005-05-30
I use dialup for internet, had to "sudo pppconfig" to set up that connection, using the Modem Lights applet to connect. Works fine by itself.
I just installed a linksys 10/100 card and "system configuration/networking" under the Computer menu found that fine. Set up a samba 'workgroup' with my M$ machine, everything good there too -by itself.
 But whenever I enable Ethernet LAN Card eth0, I can't go online. the modem will dial out (can hear it), but neither Firefox nor Synaptic (or ping either) find anything. Is there a way to enable both a modem and ethernet card at the same time? I'm still learning linux by experiementation, so thanks in advance for any help.

---

### Post by fdoving on 2005-05-31
[QUOTE=scooby]I use dialup for internet, had to "sudo pppconfig" to set up that connection, using the Modem Lights applet to connect. Works fine by itself.
I just installed a linksys 10/100 card and "system configuration/networking" under the Computer menu found that fine. Set up a samba 'workgroup' with my M$ machine, everything good there too -by itself.
 But whenever I enable Ethernet LAN Card eth0, I can't go online. the modem will dial out (can hear it), but neither Firefox nor Synaptic (or ping either) find anything. Is there a way to enable both a modem and ethernet card at the same time? I'm still learning linux by experiementation, so thanks in advance for any help.[/QUOTE]
 Check your default gateway settings. If the default gateway is set on the Ethernet card you can experience problems with dialup.

- Frode

---

### Post by scooby on 2005-06-01
[QUOTE=fdoving]Check your default gateway settings. If the default gateway is set on the Ethernet card you can experience problems with dialup.

- Frode[/QUOTE]

Okay, I'll check that.  Do you mean on the Network configuration on the Computer dropdown menu? That only detects the ethernet connection. I set up a ppp0 connection which doesn't work to connect, but does seem to activate whenever I use the modemlight applet to connect (or type sudo pon). I set that as default to internet in Properties; it didn't change anything. I still have to disable the ethernet connection in order for synaptic or firefox to see the modem. Or is there another place/method to check those settings? 
I'm extremely new to networking (and linux!) so if I need to configure something manually on the hardware, I didn't do it. I can only tell you I have identical configuration on the windows box and it works fine on both. 
I do seem to remember reading in the forums that someone else was having the same issues- and his solution was to disable the LAN in order to surf   the net via modem. Thanks:?

---

