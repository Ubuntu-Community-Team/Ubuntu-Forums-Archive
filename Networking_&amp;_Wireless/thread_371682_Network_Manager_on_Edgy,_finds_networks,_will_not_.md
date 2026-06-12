---
title: "Network Manager on Edgy, finds networks, will not connect..."
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by MDFreak76 on 2007-02-27
Ok so I am a Windows user looking to leave the dark side before the Vistapocolypse, but i am having SERIOUS problems getting this wireless system down... i'm on my 3rd re-install in just as many weeks and i am tryin my damnedest not to lose the faith... 

  i am running a dell 600m with the 2195 (using the ipw2200 driver, v1.1.2). my ethernet card is shot which sucks, so wireless is my only option, and to add insult to injury, my work does not have a wireless connection, so i am using an Ad-Hoc network with connection sharing on my work's desktop. i have connected a few times using command line crap, but i have to enter the EXACT parameters for EVERYTHING from iwlist and put them in iwconfig, and even then MAYBE (rarely) it will connect. at this point i figured there cant be anything out there that is MORE of a pain in the ***...

...enter "Network Manager", stage right...

  At the moment i am using an unencrypted network with no key (altho i have tried everything), and when i go to connect, i get two gray dots with a blue comet guy flyin around. the comet burns a little trail on my monitor for a minute or so, and then nothing else ever happens. back to square one... 

simply put, here is my problem:
  i can detect networks, but i cant connect to any of them. 


Anyone wanna throw me a bone???

---

### Post by MDFreak76 on 2007-03-06
<cough>::bump::<cough>

anyone? anyone?

 ...Bueller?

---

### Post by MDFreak76 on 2007-03-08
well... i've searched high and low, and i still dont have an answer, so heres what i've decided on doing (to anyone who may be watching this thread)...

since the only way i can connect is thru manual configuration, i think i am gonna figure out how to write a little script guy so i can just click on him to set all the needed parameters (essid, mode, channel, and key).

i'm gonna go figger this stuff out; i'll be back with my results...

---

### Post by chili555 on 2007-03-08
I think all these parameters can simply be placed in /etc/network/interfaces, like this: ```
iface eth1 inet static
wireless-essid linksys
wireless-key 1234567890abcdef
wireless-mode managed
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1
``` Of course, these parameters can be used with static or DHCP.

---

