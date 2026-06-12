---
title: "No wireless after upgrading to 8.04"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by jmgrant711 on 2008-06-18
i upgraded to 8.04 and got my sound working but my wireless stopped working:confused:

---

### Post by PRMan on 2008-06-18
Can you do 

sudo lshw 

in a terminal window and find the model of the Wireless card and post it here?  Once you do that, people can help you better.

---

### Post by jmgrant711 on 2008-06-18
i tried that and it asks for a password.  So i try to type in my password and it doesn't type any letters???

---

### Post by Ayuthia on 2008-06-18
> **jmgrant711 said:**
> i tried that and it asks for a password.  So i try to type in my password and it doesn't type any letters???

Just type in the following instead:
```
lshw -C network
```
No need for the sudo.  The last portion will just show your network info.

---

### Post by rhlobo on 2008-06-19
There are some users experiencing some wireless problems when connecting thrue WEP/WAP after 06-17 ubuntu updates. The list of disponible networks works correctly but the connection process just hangs and wont connect.

If you think this is your problem, I will be checking [https://answers.launchpad.net/ubuntu/+question/36575](https://answers.launchpad.net/ubuntu/+question/36575) constantly.

Best regards

---

