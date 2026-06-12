---
title: "Bluetooth problems"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by MauroKTM on 2006-12-18
I've installed on my laptop (Dell d620) the 6.06. 
I've configured the computer to connect internet by UMTS- bluetooth connection with a HTC TyTN PocketPC Phone.
I've followed this procedure. ([http://italy.copybase.ch/blog/informatica/linux/connessione-gprsedgeumts-su-ubuntu-con-nokia-6630-via-bluetooth/](http://italy.copybase.ch/blog/informatica/linux/connessione-gprsedgeumts-su-ubuntu-con-nokia-6630-via-bluetooth/))

All works fine until I've tryed to use this [http://www.ubuntuforums.org/showthread.php?t=50932&highlight=bluetooth+activesync](http://www.ubuntuforums.org/showthread.php?t=50932&highlight=bluetooth+activesync)
to sync the PDA with evolution.

The sync doesn't work... And the Bluetooth connection rfcomm doesn't work too...

Any Idea?

Many thanx

M.

---

### Post by Divan Santana on 2007-01-26
I don't know if its possible to sync this to Evolution/Kontact yet??
I am getting one and hoping that someone has done it!

Anyone?

---

### Post by Nik_Doof on 2007-01-26
Windows Mobile 5 right? I've just managed to get my Wizard to talk to Ubuntu by compiling a SVN version of Synce.

I don't understand Italian, but from what I can gather your connecting to your mobile from Ubuntu, to get the sync working i had to setup a link from the mobile to ubuntu. 

The 2nd one is a good guide to setting up the relevent tools by hand, just one side note: in the instructions its tells you to do a "sdptool add SP", instead do "sdptool add ACTIVESYNC" or your bluetooth won't advertise the service. Also that will only support PocketPC and not WM5, so you may need to compile libsynce and relivent stuff by hand.

---

