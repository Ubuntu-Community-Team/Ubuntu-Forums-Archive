---
title: "Lost sound on ubuntu certified netbook"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Houli on 2009-05-20
Hi I've got Toshiba NB100 netbook.I installed the latest updates and i've lost sound. When I try to open the volume options I get this error message No volume control GStreamer plugins and/or devices found. Could someone help me find a fix to this issue?

---

### Post by MontelEdwards on 2009-05-21
Are you still on Hardy?
Because that was 2 releases back...

---

### Post by Karaden on 2009-06-08
Hi - I'm having the same problem. My mother just bought the same netbook, and the same thing has happened.

The netbook is running Hardy - I would consider updating it, but I thought Hardy was the latest LTS distro? My mother is very new to Linux, so I'd hoped to leave her with the most stable solution possible... 

Are there no other suggestions besides updating to Jaunty?

---

### Post by Johan-Steyn on 2009-06-08
Hi,

What kernel are running in Hardy? Let's an adaptation of the post from dave.YNA.

Type "**uname -a**" in the terminal to find out.

[COLOR=black]Type "**sudo mv /lib/modules/[COLOR=Red]2.6.24-19[/COLOR]-lpia/updates/sound ~/sound**", replacing the listed kernel with the one listed for your version; if not the same.

[/COLOR]Type your password when prompted and the type "**sudo depmod -a**".

And restart.

Let me know if it worked.

Regards,

JS

---

### Post by LowSky on 2009-06-08
I had a simular issue, open a temrinal

type

```
sudo apt-get install ubuntu-restricted-extras
```

it will install all the gstreamers and anything else required. Also give supprt for java and flash if you dont have it already.

---

### Post by Karaden on 2009-06-08
Fantastic! That worked a treat, JS - thank you so much! :D

(For the record, my kernel was the same as the one you listed.)

---

