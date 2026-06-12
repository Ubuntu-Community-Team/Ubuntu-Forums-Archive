---
title: "DWL-G122 help + general networking queries"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by The_k3rnel on 2007-02-25
Hi all,

For the last few days I've been struggling to get my wireless Belkin PCMCIA card to work with ndisrapper so I've dug out a D-link DWL-G122 usb wireless adapter instead.

I can get the D-link working without ndiswrapper, however I have to do the following:

[LIST]
[*]Start machine without adapter inserted
[*]insert adapter (dmesg output shown below)
[*]run iwconfig and set the wep key (even though the wep key is set in the networking gui under the system menu)
[*]run "ifconfig rausb0 up"
[/LIST]

After that little sequence the card works.

I have some questions:
[LIST]
[*] Why do I need to do an "ifconfig rausb0 up" if the networking gui already recognizes the card?
[*] Why do I need to set the wep key using iwconfig if it's already set in the networking gui?
[*] Can I be sure that i'm not using the ndiswrapper driver (lsmod output shown below)? Can someone tell me what driver it is using?
[*] How do I automate the process of putting in the card and it either automatically adopting its last settings (including wep key) or scanning  through the available networks to give me a list of options etc?
[*] could someone please explain what the "interfaces" file does and how it ties in with ifconfig, ifup and ifdown?
[/LIST]

important info that may help is attached to this post:
[LIST]
[*]dmesg output
[*]lsusb output
[*]lsmod output
[/LIST]

I know that's a lot to ask but I'm a bit stuck!

Thanks a million,
Richard

---

### Post by The_k3rnel on 2007-02-25
also attached is the output of iwconfig.

Thanks, Richard

---

### Post by The_k3rnel on 2007-02-26
Sorry to bump this thread but I could really do with some help....anyone ;)

---

