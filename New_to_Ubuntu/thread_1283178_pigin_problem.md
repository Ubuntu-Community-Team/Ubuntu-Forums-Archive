---
title: "pigin problem"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by vagelism on 2009-10-05
Finally I manage to make work my Huawei E169G usb modem that my telephone company provided me.
I connect to the internet via mozilla.
But pigin is searching for network.
If I plug my pc to the ethernet router is working fine, or even by wireless, but with this modem is like I am not connected.
ANY IDEAS?

THANK YOU.

---

### Post by wildman4god on 2009-10-05
I haven't used modems in a long time but it is possible that the modem is too slow for pidgin to connect to the server. Look in pidgin's options/prefrences and see if there is a setting for network connections, you may be able to set it for modems.
 
Edit: sorry I thought you ment dial-up modem not mobile broadband, my bad. when you try to connect pidgin to the internet does it give you and error message? Also mobile broadband modems can be tempermental at times, can you tell what your signal strength is?

---

### Post by R3ptil3 on 2009-10-05
Have You set Your accounts properly ?

---

### Post by peculiar penguin on 2009-10-05
Does Network Manager know about your modem's connection? If not that's the problem - try running Pidgin with the -f switch or disable NM.

---

### Post by vagelism on 2009-10-05
The signal is fine and I do not have any error from pigin!!!
Thank you.

---

### Post by vagelism on 2009-10-05
the accounts are ok...if I connect through wifi or ethernet works perfect!

---

### Post by twright on 2009-10-05
You might want to try the Empathy Instant Messenger which will be replacing Pidgin in Karmic - not sure why it is not working but that might work.

---

### Post by vagelism on 2009-10-05
> **peculiar penguin said:**
> Does Network Manager know about your modem's connection? If not that's the problem - try running Pidgin with the -f switch or disable NM.

How to disable network manager?
Thank you!

---

### Post by twright on 2009-10-05
> **vagelism said:**
> How to disable network manager?
Thank you!
press alt + fn2 then type in pidgin -f and see if that works.

---

### Post by vagelism on 2009-10-06
Thank you!!! 
Works perfect!!!!

---

