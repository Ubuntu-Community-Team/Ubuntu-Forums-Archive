---
title: "can't get nvidia ethernet in live cd!"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by dennis1200 on 2006-12-19
I am hoping to put some Ubuntu-ness on my mom's home PC, but before diving into an installation, I'd like to have internet. The chipset is all nVidia, all the time, nForce2. Specifically, lspci gives the ethernet as: nVidia Corporation nForce2 Ethernet Controller (rev a1), but the ethernet isn't working. there isn't an /etc/iftab file in the live cd, so i'm not sure how the system is trying to name the connection, but neither eth0 or eth1 work (though they appear in the network-admin applet, both as wired connections. it seems like nvidia is all included in the restricted-modules and a couple of other packages, but so it goes. any help?

my posts have a history of low/non-existent response. let's make this one a go for the sake of a new ubuntu user.

---

### Post by chronusdark on 2006-12-19
as far as i know the nforce onboard devices work with default drivers....

try this for me...add the network monitor applet to the gnome-panel and see if it shows up as connected or lists an ip if not then try clicking in the combobox and trying a different device...i think that your connection may just be bad or on a weird device

---

### Post by dennis1200 on 2006-12-19
I think I located the problem, which didn't occur to me since I haven't worked with this setup before. The internet is DSL, which goes to the router via phone, and (here's the possible hitch) the router is transmitting data to the computer via USB, not ethernet cable (though there are the available ports - I'll try getting a short cable for that before going any farther with tinkering). Still, under Network Tools, it gave all of the device info (other than MAC and name and mode (i vaguely remember hearing about problems with nvidia and ipv6 - should I be worried?)) as not available. Again, we'll see what a cable brings.

---

### Post by MetalMusicAddict on 2006-12-19
Really odd. I have a NF2&4 with zero issues. What board make?

Sorry Im not more help.

---

### Post by dennis1200 on 2006-12-22
Ethernet cable fixed it. I saw several other posts in the forums on this make of router with a usb connection. Might be something I'd do for me, but for my mom, it just needs to work.

---

