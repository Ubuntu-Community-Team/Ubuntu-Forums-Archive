---
title: "Recommendations for PCMCIA wireless (g) w/Dapper?"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by eltorodeoro on 2006-09-09
[FONT="Tahoma"]
Hi all,

Looking for success stories of PCMCIA wireless cards that installed cleanly, or with little fuss.  I have a Dell C610 that I want to get fired up.

Thanks!
[/FONT]

---

### Post by K.Mandla on 2006-09-09
I have a Linksys WPC11 that takes no effort at all to configure. It's recognized on installation and only needs the WEP key to connect to my router. It's only 11Mbps, though.

Atheros-chipset cards are supposedly the cat's meow. If I needed another card, I'd hunt one of those down.

---

### Post by eltorodeoro on 2006-09-10
Thanks.  I notice you're running about the same specs as my Latitude.  How is Xubuntu on that platform?  Have you tried running Gnome?

---

### Post by bmasephol on 2006-09-10
I've got a Zonet G card not sure of the model, but I stuck it in and was connected in 2 minutes... no tinkering required.  Card cost something like $15 after rebate.

---

### Post by Ripfox on 2006-09-11
One thing I figured out with my wpc54g notebook card when I was trying to get it to connect under ndiswrapper: it didn't like the wpa encryption, so I just reset my router by holding in the button for 10 seconds, then downloaded the hook up manager thingy from linksys. When I set up my connection I just chose WEP and entered the key it generated into the gnome "network" application. After this everything worked. Also, I installed all the .inf files that were extracted from the latest driver package from Linksys then uninstalled the ones that said "hadware not present". Process of elimination...btw, I know it isn't as secure and this is a noob solution, but I was sick of messing with it and also couldn't understand why the card said it was connected but no internet. Just a little feedback from a new Ubuntu convert! :)

---

### Post by Ripfox on 2006-09-11
Oh, and I forgot to mention that I configured the router from a windows box (tobe able to run the automated router install program from [www.linksys.com/support](www.linksys.com/support)) Sorry bout' the extra post, hope this helps someone.

---

### Post by eltorodeoro on 2006-09-11
bmasephol,

have you tried using any sort of encryption with your Zonet?  I should have specified in the original post that I'm also shooting for WPA.  Seems like WPA tends to be a bit hairy, judging by most of the threads in this forum.


ripfox - thx for the comments.  i'll keep that one in mind!

---

### Post by oyvindaa on 2006-09-12
My Avaya Silver 11mbps PCMCIA card worked out of the box, just had to add the WEP-key and such. Recommended!

---

