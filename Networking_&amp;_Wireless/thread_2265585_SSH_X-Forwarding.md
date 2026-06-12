---
title: "SSH X-Forwarding"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by zkab on 2015-02-16
I connect to a remote machine with X-Forwarding in SSH (appending -X to the ssh command line).
After login I have:

~$ echo $DISPLAY
localhost:10.0

But when giving 
~$ sudo dpkg-reconfigure locales

it don't give me the GUI list of locales which I get if I login locally ... how can that be fixed so I get it via ssh -X ?

---

### Post by lukeiamyourfather on 2015-02-16
What client are you using? If the client doesn't have X it won't work.

---

### Post by zkab on 2015-02-16
I have 'openssh-client' installed both on local and on remote  machine ...

---

### Post by steeldriver on 2015-02-16
I can't image why it should make any difference - unless maybe you have set your debconf frontend to something graphical (like the whiptail dialog option). Does it make a difference if you add [FONT=courier new]--frontend=readline [/FONT]to the command?

---

### Post by zkab on 2015-02-16
A little bit confused - where should I add '--frontend=readline' ?

---

### Post by steeldriver on 2015-02-16
I just meant

```

sudo dpkg-reconfigure --frontend=readline locales

```

---

### Post by Hadaka on 2015-02-16
Hi Zkab,
  Are you asking why you can get menu items,run programs, change browsers while "on net" on your local lan?
but cannot from "off net" outside your lan. ...ssh -X p22 user@"your-router-ip".
does that describe what is happening?

---

### Post by zkab on 2015-02-18
Steeldriver:

This is what I get ...
~$ sudo dpkg-reconfigure --frontend=readline locales
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZM.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.

but still no  GUI list of locales ...

Hadaka:

No - the remote computer is on my LAN when I issue 'ssh -X p22 user@"LAN-computer IP address'

---

