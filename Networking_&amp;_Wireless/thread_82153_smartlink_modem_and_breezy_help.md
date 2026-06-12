---
title: "smartlink modem and breezy help"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by vinzer on 2005-10-26
hi, i hope i can get better help than the nonexistent one i got the last time i posted here. with the new breezy release, i was hoping they would do a mandriva or a suse and at least help people get their internet working via modem so any other help they'd need can be accessed online ASAP. apparently, that's not the case as the release didn't include modem drivers again. 

so here i am, hoping to move to ubuntu once again (i tried moving from hoary but then modem issues again prevented me from moving) from mandriva, and still i can't seem to install the modem drivers properly.

there are packages for the smartlink modem for breezy, but i can't compile them. funny how the default compiler available in breezy won't compile the packages supposedly made for breezy.

anyway, i'm hoping someone could direct me to a solution for this, either by helping me how to compile the source (sl-modem-source and/or sl-modem-daemon, i don't know which i should use) or provide ready-made .deb packages for the default breezy install. 

i've posted here in the past, and no one replied, and the same happened in the #ubuntu irc channel. i hope i can feel some of the purported "community spirit" that's supposed be in the ubuntu community. i wanna be part of the community, but no one's giving a hand the last time. :(

---

### Post by xbaez on 2005-10-26
the .deb files don't work for you?
Ubuntu was the ONLY distro in wihch all I had to do was
#apt-get install sl-modem-daemon, I rebooted and now I'm using my dial-up without any problems

I didn't had problems for Hoary neither

Or you can download the source, and just read the readme
I think it's as easy as #make, #make install

---

