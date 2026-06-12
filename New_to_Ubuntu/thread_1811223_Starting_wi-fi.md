---
title: "Starting wi-fi"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by JACKTE on 2011-07-24
Hi,

Can someone please advise me where should I put this line so my wi-fi will start up automatically everytime when pc is rebooted?

 sudo wpa_supplicant -B -Dwext -iwlan0 -c /etc/wpa_supplicant.conf

Thanks,

---

### Post by CaptainJamie on 2011-07-24
I'm not sure if this is what you're after but you could go to a program called "startup aplications" and click add, then paste it into the "command" space.

---

### Post by androssofer on 2011-07-24
CaptainJamies's will work, but i think it works on a per user basis? (might be inccorect)

you could add it to 

```
/etc/rc.local
```

and it will run as root on start up. as its root you could take off the sudo part. and this will mean it runs for all users..

---

### Post by JACKTE on 2011-07-24
I don't have GUI this is a server edition, and it was switched off today for 15 min.
Started up with no wi-fi network, typed that command 
wpa_supplicant -Bw -Dwext -i ra0 -c/etc/wpa_supplicant.conf
and it started to work.

I have those lines in etc/network/interfaces

pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
 post-down killall -q wpa_supplicant

but still after reboot it will not start up wi-fi I need to do it manually

---

### Post by JACKTE on 2011-07-24
Hi

androssofer

Should I just add this one line to /etc/rc.local? 

wpa_supplicant -B -Dwext -iwlan0 -c /etc/wpa_supplicant.conf

Thanks

---

### Post by JACKTE on 2011-07-24
yes that resolved the problem

---

