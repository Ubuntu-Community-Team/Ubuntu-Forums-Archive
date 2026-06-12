---
title: "[SOLVED] noob question. bridge br0 op to late?`"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by vaalbygaardsvej on 2007-12-18
i have set up a ubuntu machine running router. and when i find an atheros chipset wifi card, i will make it an access point aswell.

so far it runs smoothly when DNS, DHCP and NAT (via firestarter) is started. but it seems like my bridged connection Br0 comes up too late, that is after the servers try to start. therefore the do not start because Br0 isn't up yet. so every time i reboot the machine i must manually restart DNS, DHCP and firestarter for the box to start routing.

my bridge is defined in /etc/rc.local

as i said noob. but where shoul i define the bridge for it to be up sooner during bootup?

---

### Post by anubhavrocks on 2007-12-18
I am assuming that you have a script that set's up your bridge(using brctl ),lets call that bridge.sh.Here are the steps you follow
```
mv bridge.sh /etc/init.d/
ln -s /etc/init.d/bridge.sh /etc/rcS.d/S41bridge.sh
```

---

### Post by vaalbygaardsvej on 2007-12-18
> **anubhavrocks said:**
> I am assuming that you have a script that set's up your bridge(using brctl ),lets call that bridge.sh.Here are the steps you follow
```
mv bridge.sh /etc/init.d/
ln -s /etc/init.d/bridge.sh /etc/rcS.d/S41bridge.sh
```


actually no i have no seperate script. the brctl commands are just added in /etc/rc.local this works. but brings up the bridge way to late :(

ill give this a try and make a separate script like you say :)

---

### Post by vaalbygaardsvej on 2007-12-18
i made a script in init.d and put in the brctl commands. and ran the commands you posted. now the bridge doesn't even come up :confused:

what is necessary for the script: bridge.sh to be run at startup?:(

---

### Post by anubhavrocks on 2007-12-18
check if you can run it manually
```
sudo /etc/init.d/bridge.sh
```

---

### Post by vaalbygaardsvej on 2007-12-19
> **anubhavrocks said:**
> check if you can run it manually
```
sudo /etc/init.d/bridge.sh
```

doesn't seem like i can. is it something to do with wheather or not it has execute bits set or somthn' like that:confused:

still beeing noob here ;-)

---

### Post by anubhavrocks on 2007-12-19
Yeah that can be possible,make your script executable
sudo chmod +x bridge.sh

---

### Post by vaalbygaardsvej on 2007-12-19
this solved the problem (and the fact that i'd forget to successfully paste the commands into the script ::OOOOPS::)

but with the commands in the script and the exec bits set. it worked.. and the servers started on bootup..

thankyou thankyou thankyou

as a conselation to the following we probably will never meet (different countries) i would set up a nice big smashing kiss for you. you just saved the day :)

---

### Post by anubhavrocks on 2007-12-19
You are welcome :) .Please mark the thread as Solved,so that others can benefit

---

