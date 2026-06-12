---
title: "How to run GNOME-PPP with root privilages"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2009-12-15
I have a HSUPA modem that I managed to get working through the gnome-ppp dialer but the problem is I need to run it from the terminal using sudo other wise it want dial up on to the 3G network. I tried to create a launcher using "sudo gnome-ppp" but it didn't work can any one help me to with this so I can run the program with out calling it from the terminal every time I want to dial.

And another thing I also like to know how to create a customized distro with that program on board I tried to use remastersys but it's giving me errors after creating the ISO. When I run them in a virtual box ubiquty gives an error and crashers suddenly when loading the LiveCD Gnome gives an error saying it was unable to load properly I thought it might be to do something with the distro so I tried it with 8.04 but same thing happened I cant install ubuntu from that. Currently I'm using 9.10 when I use remaster on this I get the same problem.

---

### Post by Temposs on 2009-12-15
Instead of making your launcher "sudo gnome-ppp", make it "gksudo gnome-ppp". sudo is strictly command line, so if you're using the graphical stuff, you can't use it. You have to use gksudo instead.

---

### Post by sadaruwan12 on 2009-12-15
> **Temposs said:**
> Instead of making your launcher "sudo gnome-ppp", make it "gksudo gnome-ppp". sudo is strictly command line, so if you're using the graphical stuff, you can't use it. You have to use gksudo instead.

OK I'll try that thanks for the quick reply. Now can any one help me with my second problem.

---

