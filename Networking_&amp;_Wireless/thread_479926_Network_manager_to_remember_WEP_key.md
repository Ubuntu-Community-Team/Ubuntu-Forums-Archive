---
title: "Network manager to remember WEP key?"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by mgaskell on 2007-06-20
I have Feisty on my laptop. I use network mananger to log into various wireless networks. My home network is WEP protected. Is there a way I can have Feisty remember my WEP key when I log on to my home network?

Thanks in advance.

---

### Post by raja on 2007-06-20
If you mean you dont want to be prompted for the key everytime, do this ...
```
sudo aptitude install libpam-keyring
sudo gedit /etc/pam.d/gdm
```

Now in this file, add this line at the end
```
@include common-pamkeyring
```

---

### Post by Dieselguts on 2008-03-17
i tried inputting the second code u mentioned and it just said command not found?

---

### Post by spectrevk on 2008-03-17
I solved this problem for myself by switching from Network Manager to WICD.

---

### Post by Bubba64 on 2008-03-17
Network manager itself can save wep and hookups look at main screen on top. Network manager apparently has bugs though that I see comments on periodically.

---

