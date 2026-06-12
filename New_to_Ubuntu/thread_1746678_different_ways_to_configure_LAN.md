---
title: "different ways to configure LAN"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Imesmi on 2011-05-02
I have to talk about  LAN configuration in Linux.
But I am not able to find sth appropriate that explains me the different ways to configure
LAN in linux . I would be really grateful if you could talk me in general about LAN 
configuration. THANKS IN ADVANCE
please help me I have tried a lot alona but as i am a beginner in LAN it's quite difficult for me to analyze this topic. please pleasssssssee

---

### Post by anant_crp on 2011-05-02
open terminal,
sudo -i, it needs root password...
#gedit /etc/network/interfaces
add following lines
address (ip address for ethernet) Ex:10.12.1.2
netmask (Sunet mask of the n/w) Ex: 255.255.0.0
gateway (gateway the network) ex: 10.12.1.1
 
Then restart the n/w services with command as follows
#/etc/init.d/networking restart
 
Thank 
Anant
 
 
> **Imesmi said:**
> I have to talk about LAN configuration in Linux.
But I am not able to find sth appropriate that explains me the different ways to configure
LAN in linux . I would be really grateful if you could talk me in general about LAN 
configuration. THANKS IN ADVANCE
please help me I have tried a lot alona but as i am a beginner in LAN it's quite difficult for me to analyze this topic. please pleasssssssee

---

### Post by Zill on 2011-05-02
> **Imesmi said:**
> ...I would be really grateful if you could talk me in general about LAN configuration...
Google will give you plenty of information about LANs, such as [this]("http://en.wikipedia.org/wiki/Local_area_network") Wikipedia article.

However, you may get more help on these forums if you ask *specific* questions, clearly indicating *exactly* what you wish to achieve and what system(s) you currently use.

---

