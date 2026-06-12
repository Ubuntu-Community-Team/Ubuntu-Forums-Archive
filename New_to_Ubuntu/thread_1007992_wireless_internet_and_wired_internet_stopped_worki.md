---
title: "wireless internet and wired internet stopped working"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by ja660k on 2008-12-11
i actually have 2 things i need help with, the wireless internet is the one i need fixed tho, 

i have atheros wlan card, i installed ndis and all that the driver, and it worked. today i try log in and my network manager cannot find my wireless network, but i know its there cos my mac is connected to it

as for the wired, i plug it in and nothing, i need to run sudo dhclient eth0 to force it.. success but i dont use wired that much

for the wireless i ran iwconfig and everything seemed fine. the result is
```

ja660k@ja660k-linUx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

if anyone could help :)... also how can i mount .iso images to my computer. like without burning it to a cd and then running it, i need to cut out the burning to cd part...

---

### Post by 2hot6ft2 on 2008-12-11
Might try this for mounting the iso's I got this from a thread on cool apps but haven't had use for it yet.

"Gmount-iso For me is the easiest way to mount iso images in a directory. it will always ask for admin password in order to mount though. It's in the repositories"

---

### Post by ja660k on 2008-12-11
anyone...

---

