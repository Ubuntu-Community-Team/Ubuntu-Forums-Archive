---
title: "LiveUSB: Create a LiveCD from a LiveUSB"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by frankiebaby on 2009-09-26
Does anyone know how to convert a LiveUSB setup to a LiveCD directly from the LiveUSB, without needing to install Ubuntu on the hard drive of a computer?
 
I have tried by just creating an ISO file of the LiveUSB and burning it onto a DVD, but it won't boot. I am sure I am missing something simple, but I don't want to convert using any command line method, as this would make it difficult for friends to do the same.
 
It would be very handy to be able to easily create a LiveCD from a LiveUSB to share with friends. It can also act as a back-up of a LiveUSB that has a persistence set up.
 
Thanks

---

### Post by MontelEdwards on 2009-09-26
Yes, I guess you could just remove syslinux, and rename the folder syslinux to isolinux

---

### Post by frankiebaby on 2009-09-26
I gave the suggestions a go, but no luck.
 
With regards the suggestion:
 
"...just remove syslinux"
 
I understood this to mean remove all files named 'syslinux.cgf'? I did this but still no luck. I also renamed the the folder syslinux to isolinux. 
 
I then burnt onto a Re-Writable DVD, but it did not boot.
 
With regards the syslinux.cfg files I deleted, one was inside the original syslinux folder and one was outside of all the folders.
 
Any other suggestions would be most welcome.
 
Thanks
Frank

---

### Post by Paqman on 2009-09-26
Boot into your LiveUSB session and use [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")? It'll generate an .iso from any system.

---

