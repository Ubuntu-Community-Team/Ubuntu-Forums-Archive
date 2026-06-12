---
title: "firefox can't load https"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by illumeo on 2009-07-20
I want to use ubuntu one with my server (9.04) so i installed the gui and used firefox. http pages load fine but when i go to a https page like the ubuntuone page, it just times out. i have a line in my iptables to accept https port 443

any ideas?

thanks

---

### Post by Clorow on 2009-07-20
I doubt this, but it might be a problem with your [about:config](about:config). Go there, and check the entries that start with "network.protocol-handler."

---

### Post by illumeo on 2009-07-20
have had a look but can't see anything there that it might be... but thanks for trying.

---

### Post by Garyhans on 2009-07-20
I think there is settings under preferences/advanced or security that you set the https ssl to what ever. I use Https all the time..

---

### Post by y-lee on 2009-07-20
Hmm strange. 

If you start firefox from a terminal, do you get any error messages in the terminal when you visit secure sites?

Have you tried creating a new firefox profile?

```
firefox -profilemanager

```

Do you still have the same problems?

Have you tried reinstalling firefox?

```
sudo apt-get install --reinstall firefox
```

---

### Post by illumeo on 2009-07-20
thanks for that, I have tried both but so far no luck...

---

### Post by y-lee on 2009-07-20
Ok then it might be the iptables thing or something else. Unfortunately i am currently on a windows machine so I will have to look into it latter if no else responds. BTW have you looked thru all your firefox preferences? Have you tried another browser, like opera or Konqueror? I am not suggesting changing browsers just curious whether this is a firefox issue or some system problem.

---

### Post by Garyhans on 2009-07-20
I'm using Firefox 3.5 now.  Maybe you should install Shiretoko and give it a go. My work requires Https and I haven't had any issues.

---

### Post by illumeo on 2009-07-20
fixed.....

thanks very much for your help

in the end, although i had the inbound line in the iptables i had forgotten the OUTPUT line.

cheers

---

