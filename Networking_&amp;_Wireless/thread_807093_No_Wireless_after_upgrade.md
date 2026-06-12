---
title: "No Wireless after upgrade"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by dm6257 on 2008-05-25
It may be a coincidence but my wireless connectivity on my ThinkPad Z61 stopped working after a kernal upgrade last night.  It connects after a restart but drops out after a minute or so.  Same with roaming or manual configuration.  I am typing this on Vista Home Premium on the same machine so I know it isn't the box.

Anyone else experience this problem?

Thanks,
dm6257

---

### Post by xfceuser on 2008-05-25
Hi, Firstly see if you are using a firewall, then look at the "Hardware Drivers" or "Restricted Device Drivers" in administrative or system menu, and see if your wifi driver is enabled.

---

### Post by dm6257 on 2008-05-25
Thanks for the suggestion.  I didn't change anything and it does connect for a few minutes then drops out.

---

### Post by dm6257 on 2008-05-25
I looked at my hardware drivers and didn't see anything listed for an Intel PRO/Wireless 3945.  

Do I need to reinstall a driver?

Thanks,
dm6257

---

### Post by xfceuser on 2008-05-25
when it connects, before disconnecting, are you able to use internet?

---

### Post by dm6257 on 2008-05-25
Yes.  I can use the internet until it drops.  Then it suddenly shows the name of my essid and 0% -- all bars are gone.  This happens every time.

Thanks,
dm6257

---

### Post by xfceuser on 2008-05-25
it might be a hardware problem. try the LiveCD and see if the problem exist there or not. also check if you are running a firewall. after updating the settings may change.

---

### Post by dm6257 on 2008-05-25
I used Acronis to restore a 7.10  backup from before the Hardy upgrade and my wireless connection works fine.  I have seen others on this forum describing the same problem so I am assuming it is not hardware related.

I will stay with the old version for a little longer.

Thanks,
dm6257

---

### Post by xfceuser on 2008-05-26
> You made a suggestion about a driver for my Intel PRO/Wireless interface.  Hardy didn't list any proprietary drivers.  After I reinstalled 7.10 the restricted drivers section listed one for my Intel PRO/Wireless.  Did my driver get destroyed during the update?
 

this may be because there is a new open source driver being developed and included, so the proprietary one is not being used in the new distribution. this also explain that your problem is because of the new driver.

---

### Post by cjbarrow on 2008-05-27
I had a similar problem following the upgrade, although I could see my wireless network it was stuck trying to connect with a message waiting for key.

I have an Acer Laptop with a broadcom wireless card and have been using the ndiswrapper. When checking Hardware drivers under administration the network card no longer shows. I can revert during bootup to the previous kernal which allows me to connect.

Any ideas as to what I should try to fix this, do I need to stop using the ndiswrapper, or maybe uninstall and re install it?

Chris.

---

