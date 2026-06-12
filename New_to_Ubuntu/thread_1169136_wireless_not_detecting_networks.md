---
title: "wireless not detecting networks"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by astropunkin on 2009-05-24
I just bought a Dell Studio 15 laptop and am installing Ubuntu.  I have 8.04 and the Broadcom STA Wireless driver.  Why isn't it detecting networks??  HALP!

Update: More bad news.  When I go to System>Administration>Network Tools and I highlight eth1 then click Configure it says that the interface does not exist.  :(  What the crap is going on?!

---

### Post by h0ax on 2009-05-24
Hey there..

my friend had a similar problem with an HP.

After some searching we edited this file:

```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```to set the keyword 'managed=true' and then rebooted.

hope that helps!

---

### Post by astropunkin on 2009-05-24
I looked for that file in this system and it doesn't exist :(

---

### Post by h0ax on 2009-05-24
well that's about all i know.. sorry :[

bump for someone else to help you!

---

