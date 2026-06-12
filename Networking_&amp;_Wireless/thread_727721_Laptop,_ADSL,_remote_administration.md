---
title: "Laptop, ADSL, remote administration"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by huska on 2008-03-18
Hi all,
I would like to remotely administrate my mom's laptop which is connected to the internet using ADSL. It is laptop and I would like her to use internet only when she needs it. To be able to do this I have installed her rp-pppoe. 

Is there anybody who knows how to automatically turn on hamachi and reconfigure firestarter when ADSL connection is active? 

Thank you.

---

### Post by SpaceTeddy on 2008-03-19
why does hamachi need to be turned off when the computer is not connected to the internet - it will just sit the background and continously try to connect to the internet - which is not there. 

Also, why does firestarted need to be reconfigured. There is nothing to connect to, so she does not need a special firewall for then she is not connected...

i somehow think i am misunderstanding you here... sorry :(

---

### Post by huska on 2008-03-21
Hi, thank you for reply.  You are right, hamachi can stay turned in background. I have not tried that. 

Firestarter needs ppp0 device when I configure it to use pppoe. If this is not there from the beginning it will not apply chain policy on that device.

To allow hamachi to pass firestarter I need to write rules into /etc/firestarter/user-pre file. When firestarter is restarted using GUI then these policies are not used. When I restarted init script with firestarter then it worked for me.

Do you have any experience with this?

Thank you :)

---

### Post by SpaceTeddy on 2008-03-23
i have never used firestarter, but rather applied the iptables rules myself (and writing them myself). since you can write any rule for any device (existant or not) i am a little surprised that firestarter acctually prohibits this. 

in the worst case, you could probably configure firestarter, apply the stuff, then save the iptables configuration, disable firestarted and apply the saved the config when during boot. This would always apply the rules regardless of the state of ppp0... 

in general, i don't like scripts that configure iptables and try to be smart about it...

---

### Post by huska on 2008-03-24
You are right. It could be better to write own rules. 

I am using firestarter because it saves my time and I do not need to study which ports to allow... I simply trust it.

I was mistaken I thought rules applied to not active device will not work after this device will be active. Then I have to test it.

Anyway thank you for chat. It helped me to get new ideas :)

---

