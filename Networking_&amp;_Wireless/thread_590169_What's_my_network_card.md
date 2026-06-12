---
title: "What's my network card?"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by red_forman on 2007-10-24
How can i see my network cards name is???
Im useing a Acer Aspire 5630 laptop.

I need to know couse in XP my network card dosent work and i cant see the name there and if i downloaded the drivers thrue ubuntu it probebly would work.

My english is real bad as you can see. :)

Regards

---

### Post by wolanIT on 2007-10-24
You can check your card  **(Aplication>Accesories>Terminal)**

then: ```
 lspci
``` 

and there will be your card model 

for example: 

```

...
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev02)
[B]05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
[/B]
...

```


And thats all.
Sorry but  my English is really bad

---

### Post by froy02 on 2007-10-24
Go to the System menu > Preferences then click on "Hardware Information".  It would show you a lot about your installed hardware.

---

