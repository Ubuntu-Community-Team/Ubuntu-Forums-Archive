---
title: "Dial up?"
date: 2005-09-21
forum: Networking &amp; Wireless
---

### Post by BrianB on 2005-09-21
I am having a little trouble with my dial-up internet connection in that it doesn't work :???: . Well it did for a while... I searched the forums and found a how-to for DNS issues and this solved it for a while but then out of the blue it stopped working again. Firefox gives the error "xxxxxxxxx can't be found please check the name and try again" and synaptic doesn't work either. Can anyone help?

---

### Post by Christopher999999 on 2005-09-21
How do you set it up to use dialup?

---

### Post by BrianB on 2005-09-22
Under networking in hoary. I'm pretty sure everything like username, password etc. are set up right.

---

### Post by mlomker on 2005-09-22
If you know the right settings you can manually edit the /etc/resolv.conf file to plug in the DNS server entries.  

My recommendation, though, is to download a package called **resolvconf** in Synaptic.  It automatically manages that file and does a much better job than the system does on its own.

---

### Post by BrianB on 2005-09-22
well i've already tried that (editing /etc/resolv.conf) and it worked for a while but stopped working again. And how do I download the resolvconf package if synaptic will not work?

---

### Post by mlomker on 2005-09-22
[QUOTE=BrianB]well i've already tried that (editing /etc/resolv.conf) and it worked for a while but stopped working again. And how do I download the resolvconf package if synaptic will not work?[/QUOTE]

If editing resolv.conf doesn't work then that package won't help, anyway.  That package just edits resolv conf for you...in a more intelligent way than out of the box.

You can download things using [http://packages.ubuntu.com](http://packages.ubuntu.com) on another machine and then copy it to your box somehow.  It's not convenient, but in a jam...

---

### Post by az on 2005-09-22
resolv.conf is supposed to be written by pppd everytime you make a connection.


From a terminal, type

sudo pppconfig
and enter all your info by hand.  Do not forget to save.

Open another terminal and type

tail -f /var/log/messages

and type 
sudo pon 
from the other terminal.  Does that connect you properly?  If not, can you post what is displayed in the messages terminal when you do that?

---

### Post by BrianB on 2005-09-23
Thanks azz it worked! :) Can I use system > networking to connect?

---

