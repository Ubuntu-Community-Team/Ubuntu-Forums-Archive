---
title: "Installing wpa supplicant 0.5.7 - need guidance"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by usererror on 2007-02-02
I am trying to get my EAP-FAST setup to work but wpa supplicant 0.5.5 or whatever comes with Edgy 6.10 does not support eap fast, 0.5.7 of wpa does.

I've installed openssl-dev but i still get errors, i am not sure my .config file is right that you apparently have to make youself, no ./configure  has anyone done this?

I'm using an intel 3945 card.  if i need to provide more info just let me know!

---

### Post by wieman01 on 2007-02-05
What error messages do you get when compiling the source code? Did you find any hints in the README?

---

### Post by usererror on 2007-02-06
Well i hate to say this but I'm abandoning this thread.  I found a howto on the site that installed Network Manager from a CVS version that supports LEAP!  Now I don't have to edit my /etc/network/interfaces file each time I move from home to work!  :D

I hope no one has any hard feelings. ;)

---

### Post by wieman01 on 2007-02-06
Usererror:

No, makes sense, buddy. I'd do the same if Network Manager supported static IP. No hard feelings at all, far from it. Appreciate your help. Hope my thread will be unnecessary one day, hope this happens rather sooner than later.

---

### Post by usererror on 2007-02-06
Well, once WPA supplicant 0.5.7 is a deb package i'll give EAP-FAST another shot!

---

### Post by usererror on 2007-05-07
For what it's worth, I'm posting an update here.

in Fiesty I am able to connect to our A Radio, 802.11a secure network running dynamic WEP, LEAP/EAP FAST.

I'm connecting with the Network-Manager, and using LEAP since it doesn't have eap-fast supported.  

A Radio wasn't supported before, or I could never get it to work, or our new LWAPP system is making the difference.

---

