---
title: "New to ubuntu tasked with vpn setup"
date: 2019-01-15
forum: Networking &amp; Wireless
---

### Post by ricea93 on 2019-01-15
Hello All. 

Hopefully this post is in the right spot. I have been tasked with setting up an sstp eap-mschapv2 connection on a Ubuntu box. I have successfully loaded sstp-client and all dependencies and packages but I cant get the eap check box to stop being grayed out... 
Which brings me to this forum. Does Ubuntu support eap-mschapv2 for sstp? If so can anyone provide me with further information on the process. 

Thanks, 

Alex.

---

### Post by ricea93 on 2019-01-15
Hello All. 

I am trying to setup a vpn client on my Ubuntu V18 box. I have sstp-client installed and configure but when I go to setup my vpn eap is grayed out... Does Ubuntu not support eap-mschapv2 with sstp? 

Any information would be quite helpful. 

Thanks, 

Alex.

---

### Post by QIII on 2019-01-15
Threads merged.

Please don't create duplicate theads.  I dilutes the community's efforts by scattering effort and having different people trying to answer in each thread.

If you would like to have a thread moved, use the "Report post" button to bring you request to the Forums Staff.

Also remember that the community is all volunteer, spread around the world, and everyone has a life outside of the Forums.  You may not get an answer right away.  Rather than starting a new thread, just add a new post to your thread with the word "bump" or similar (please wait 12 hours).  That will bring your thread back up to the top of the heap.

Cheers.

---

### Post by ricea93 on 2019-01-15
Ok thanks, I noticed that the first post was most likely under the wrong section hence the new post. I was going to mark the old one to be deleted.

---

### Post by ricea93 on 2019-01-16
Bump.... 

A simple not possible would have been acceptable.. jeez active forums much?

---

### Post by SeijiSensei on 2019-01-17
MSChapv2 is a Microsoft protocol that hardly any of us would ever use.  [OpenVPN]("http://openvpn.net/") is by far the more common VPN method.  So you'll need to be patient with us, find the documentation you need online, or consider changing VPN methods.

---

### Post by ricea93 on 2019-01-17
That would be a no go captain. As to comply with Nist requirements and other business we work with the standard is a must. I can get mschapv2 support with the sstp-client add on but it wont allow eap. I think I have a few other ideas to try. Thank you for your response though much appreciated!

---

### Post by ricea93 on 2019-01-18
Just sharing the information with everyone for future reference. SSTP is possiable on ubuntu with chap & mschapv2. But from all of my reading eap is not supported at all. I hope this helps someone else when searching! 

Thanks, 

Alex.

---

