---
title: "Gaim - Proxy - Feisty"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by Peter Sommer-Larsen on 2007-09-12
Hey im having problems getting my gaim working at my university.
To get firefox working I have to go to network-proporties and mark

(.) Automatic-Proxyconfiguration-URL: [http://proxy.aau.dk/proxy.pac](http://proxy.aau.dk/proxy.pac)

How do I do this in Gaim ?

---

### Post by Peter Sommer-Larsen on 2007-09-12
Ah Crap - my xterm or synaptic can neither connect to the internet..
plz help.. I really need it..

---

### Post by Peter Sommer-Larsen on 2007-09-12
Ok it was simple..had to type:
$ sudo wget [http://proxy.aau.dk/proxy.pac](http://proxy.aau.dk/proxy.pac)

---

### Post by brothermalcolm on 2007-10-25
hi peter

i have got exactly the same problem at my uni network as you , being able to get firefox to work by typing in autoconfig url:
 
[http://www.dur.ac.uk/Admin/proxy.config](http://www.dur.ac.uk/Admin/proxy.config)

which my uni provided with me
but i'm unable to do the same for gaim or skype
i hav tried typing in 

sudo wget [http://www.dur.ac.uk/Admin/proxy.config](http://www.dur.ac.uk/Admin/proxy.config)

without really knowing what it does and it says:

'proxy.config' saved

but still nothing exciting has happened

gaim 2.0.0 beta6
msn account
tried account settings | proxy | tried both gnome settings and enviromental settings

please help!

---

