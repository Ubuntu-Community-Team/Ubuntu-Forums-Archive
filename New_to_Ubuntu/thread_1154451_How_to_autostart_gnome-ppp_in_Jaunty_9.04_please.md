---
title: "How to autostart gnome-ppp in Jaunty 9.04 please"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by ntu on 2009-05-09
I have just installed Jaunty and have gnome-ppp connecting my 56k dialup modem manually. I would now like to know how to get gnome-ppp online automatically each time I reboot. Could someone advise me on this please?

---

### Post by Didius Falco on 2009-05-09
> **ntu said:**
> I have just installed Jaunty and have gnome-ppp connecting my 56k dialup modem manually. I would now like to know how to get gnome-ppp online automatically each time I reboot. Could someone advise me on this please?


Have you tried adding it to **System/Preferences/Startup Programs**?

---

### Post by ntu on 2009-05-09
What do I actually add where it says "Command" please?

---

### Post by Didius Falco on 2009-05-09
I'm searching (unsuccessfully, so far) for a HowTo on setting it up to load at startup.

I don't use gnome-ppp so I can't test things out on my PC, but I'll keep looking and meanwhile maybe on of the people that know more about this than I do will jump in and help. 

Regards,

Didius

---

### Post by ntu on 2009-05-09
I have put "gnome-ppp" in the command line in System>Preferences>Startup Applications but it did not automatically start on reboot.

---

### Post by Didius Falco on 2009-05-09
Delete that from Startup for now. Open your favorite text editor and navigate to /etc/network/interfaces and open that file. Cut and paste the contents to your next post.

I've found a potential fix, but, not using gnome-ppp myself, I'm just trying to figure it out as we go.  

At this stage, we just want to see what is in it, so thre is no need for root access.

Regards,

Didius

---

### Post by ntu on 2009-05-09
/etc/network/interfaces contains:

```
auto lo
iface lo inet loopback
```

---

### Post by ntu on 2009-05-09
I put "sudo pppconfig" in the terminal and filled in my details and it will start with "pon" so I put "pon" in Startup Applications and now it autostarts on reboot. Only thing is I have nothing onscreen to tell me I am online.

---

### Post by Didius Falco on 2009-05-09
Good work figuring out how to load it by yourself.

Look in Synaptic for a package named **pppstatus** - it looks like just what you need.

Regards,

Didius

---

### Post by ntu on 2009-05-09
I downloaded pppstatus but it is not working. Anyway I am happy, luckily I have an external modem so am getting used to seeing which modem lights are showing on it when online. Thank you for your assistance here Didius and keeping me at it :)

---

### Post by Didius Falco on 2009-05-09
I was more a barracking section than a help, but good onya for getting it to work.

Regards,

Didius

---

