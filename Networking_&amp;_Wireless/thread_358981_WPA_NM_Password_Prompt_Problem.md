---
title: "WPA NM Password Prompt Problem"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by anthony.prime on 2007-02-11
Hi,

I'm hoping someone can advise me.

I've just installed 6.06LTS and having installed the gnome network manager to resolve the lack of WPA security I have another supplemental problem.

NM sees my router perfectly and from the shell I can scan and find it, so I'm sure my wireless card (Intel PW2200) is working fine.

Unfortunately when I click on the network to connect to in NM, I don't receive a password prompt for the security details, hence though I can see my (and other SSIDs) I can't connect as I can't input the password.

Any Thoughts?

Thanks in advance.

--
Anthony

---

### Post by wieman01 on 2007-02-12
Did you install wpa-supplicant in addition to Network Manager? That's a must.

---

### Post by anthony.prime on 2007-02-12
Thanks for replying. Yes, I did. But I don't understand why. All this is far from intuitive...

Unfortunately, I'm trying to fix this by blindly following instructions from the net - which I'm sure I have, and I'm sure would work in some circumstances.

If it will help I'll go "scorched earth" and reinstall to a given base. I just need to understand what I'm missing and why.

All seems tantalisingly close, but so far away.

A.

---

### Post by teaker1s on 2007-02-12
if you are connecting with
[COLOR="Red"]network-manager-gnome[/COLOR]
try connecting by clicking connect ot other wireless network and setting security option

---

### Post by wieman01 on 2007-02-13
> **anthony.prime said:**
> Thanks for replying. Yes, I did. But I don't understand why. All this is far from intuitive...

Unfortunately, I'm trying to fix this by blindly following instructions from the net - which I'm sure I have, and I'm sure would work in some circumstances.

If it will help I'll go "scorched earth" and reinstall to a given base. I just need to understand what I'm missing and why.

All seems tantalisingly close, but so far away.

A.
Would you post the contents of this file please (command line): 
> sudo gedit /etc/network/interfaces
And please also do a:
> ifconfig
...and:
> iwconfig
Please post the results. Perhaps you are missing something.

---

