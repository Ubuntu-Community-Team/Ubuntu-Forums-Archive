---
title: "voip cheap"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by donhinrichs on 2010-10-12
I want to use voipcheap phone service on ubuntu.  I downloaded xlite as directed by the voip web site.  I extracted the files but how do I install the program to make it work in ubuntu 10.4

---

### Post by ibizatunes on 2010-10-12
i have voip cheap install but not on xlite i couldnt get to work on ubuntu 8.10 (last time i tryed) it may be fixed now or make life easy for yourself just go to software center
download ekiga
and enter these setting
	SIP port : 5060
	Registrar : sip.VoipCheap.com
	Proxy server : sip.VoipCheap.com
	Outbound proxy server : leave empty
	Account name : your VoipCheap username
	Password : your VoipCheap password
	Display name/number : your VoipCheap username or voipnumber
	Stunserver (option) : stun.VoipCheap.com

if you want to use xlite you need to download the tar file then extract it

INSTALLATION:

Untar the file:

cd to ~/Downloads
> tar -zxvf X-Lite_Install.tar.gz

This should expand the files into xten-xlite directory.
> cd xten-xlite

The executable is xtensoftphone, it should already have +x permission. If it does not, change the permission:
> chmod +x xtensoftphone

To run the executable:
> ./xtensoftphone

Copy the executable to a defined $PATH if you so wish.

---

### Post by donhinrichs on 2010-10-12
How do I install a program (x-lite_install.tar.gz

---

### Post by s.fox on 2010-10-12
Threads merged.

Please do not create multiple threads with the same problem.   Thank you.

---

### Post by gradinaruvasile on 2010-10-12
Why bother with xlite when you have alternatives in the Ubuntu repos like ekiga, sflphone, linphone etc (Empathy in theory should work too, but i found it flaky).
I found linphone to work best.

---

