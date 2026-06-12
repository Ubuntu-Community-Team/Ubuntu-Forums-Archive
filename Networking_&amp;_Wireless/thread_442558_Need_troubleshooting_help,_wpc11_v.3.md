---
title: "Need troubleshooting help, wpc11 v.3"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by Jay_in_TN on 2007-05-13
My linksys wpc11 v.3 card works flawlessly in Edgy. I have installed Feisty Fawn three times and had the same problem each time. I have followed several suggestions found in similar threads to no avail.
I have a "wireless connection (wifi0) which doesn't seem to work.
I have a "wireless connection (eth1) which seems to be the one to use (although I am just saying that because that is how it configures in Edgy and in other linux distribs.)

The card sees my network. It even allows me to connect if I manually choose the eth1 option in the network manager. But after connecting it has no IP address from my DHCP server.

If I keep messing with the network manager I get a lockup every time.

If I boot with the card plugged in I get a lockup prior to boot every time.

Help, please??

I am standing by to work this out.

Jay

---

### Post by Jay_in_TN on 2007-05-13
I know this wireless/Feisty topic gets old but is there anyone who can help me?
Anyone?

Thanks,
Jay

---

### Post by konik134 on 2007-05-13
ok the network manager does not like this wirelles card  listen go to ad/remove aplication uninstall network manager then go from administration-networking configurate your card when u tiping name of the network (essid) on the end of the network name add x or any leter in my case was "linksysx" hope this works  :lolflag:

---

### Post by RomeReactor on 2007-05-13
Hi. I don't have any experience with your card, but it seems to me that if Ubuntu locks up during boot while the card is in, then you have conflicting drivers. Run this in the terminal:

```
lspci
```

and post the output here. You may need to blacklist a module.

---

### Post by Jay_in_TN on 2007-05-13
Thanks--I gave up. This is third time I have installed and tried to get it to work,
Perhaps I will try again in a few days.
BTW--I did blacklist a module to no avail.
I did not try to uninstall the network manager.
Maybe next time.
Thanks for the help.
Back to Edgy for now.
Jay

---

### Post by ChangBeer on 2007-05-14
Hey, I may be able to help:

   I also had problem with that Linksys WPC11 v3, while it works great when you boot from the Feisty live CD, after installing Feisty my laptop would not boot with the wireless card in.

   When I plugged the card in after booting I saw that it  was using the "hostap" driver, which from what I had read, should be the right driver.

  However, when booting from the CD, it used the "orinoco" driver, and worked fine, even though I thought orinoco was not right for the v3 version.

  Anyway, I added "blacklist hostap_cs"  to the /etc/modprobe.d/blacklist file, and now I can boot and use the card with no problems.

  There may be a better way to fix this, and I'm still confused about the right driver for this card, but at least it works.

---

### Post by ChangBeer on 2007-05-14
SORRY----

on my last post, should read:

blacklist hostap_cs


sorry for the typo

try it, it worked for me

---

### Post by Jay_in_TN on 2007-05-21
Thanks for the help. Yes--I noticed the exact same driver issue but I did not know how to change them.
If I get the gumption to install Feisty Fawn again I will do as you suggested and hope it works.
Jay

---

