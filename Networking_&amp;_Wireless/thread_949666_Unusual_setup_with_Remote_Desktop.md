---
title: "Unusual setup with Remote Desktop"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by MatthewHSE on 2008-10-16
I have an Ubuntu computer that is only meant to run as a proxy server on our LAN.  It doesn't have its own monitor or keyboard (KVM switches haven't worked for me so far), so I like to use Remote Desktop for periodic administration.

The problem I'm having is that I can't connect to this computer via Remote Desktop over our LAN *unless* there is a monitor and keyboard attached to it, which defeats the purpose.

Normally, this computer runs without a monitor, keyboard or mouse - only a power cord and network cable are connected.  Since it's running as a network proxy, I can easily verify that it is indeed running properly, has a working network connection, etc.

What do I need to do so I can connect to Remote Desktop on this computer?  I should mention that this exact setup worked fine on my last Ubuntu install, but it stopped working when I did a clean reinstall of Hardy.

Thanks for any ideas,

Matthew

---

### Post by jimv on 2008-10-16
Why not use SSH for administration?  Then you can ditch the overhead for the GUI.

---

### Post by MatthewHSE on 2008-11-17
> **jimv said:**
> Why not use SSH for administration?  Then you can ditch the overhead for the GUI.

I could use SSH if administration was really *all* I planned to do, but I had really hoped to use the GUI occasionally just to get used to Ubuntu and see about switching my own computer to it.  So it would be nice to get Remote Desktop working if possible.

Thanks,

Matthew

---

