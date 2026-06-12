---
title: "Network Security of Ubuntu"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by babacan on 2007-08-09
Greetings
First of all , let me tell you my computer setup: I am using ADSL with a such setup: Zoom x4 Route Modem -> Switch -> 3 computers that are having windows and Ubuntu dual boot.

Now comes the question , I recently disabled DMZ of ADSL modem thus opened all ports , in Windows I am covering this with Kaspersky Internet Security which is having firewall and when I do a port check , all ports showing as "Stealth" , which is I think good. 

However at Ubuntu , I am not sure if it is secure to use DMZ as some saying Ubuntu doesnt have build-in firewall and some says it is. When I check ports under ubuntu , most are showing closed however afew are showing Open and no stealth ports.

So what do you lads suggest me ? Shall I install a 3rd party firewall , if so can you name a free and good one. If no firewall needed , then what to do ?

Regards , Sorry for my bad English as it is not my mothertongue :p

---

### Post by babacan on 2007-08-09
A shameless bump

---

### Post by ruibernardo on 2007-08-10
> **babacan said:**
> 
When I check ports under ubuntu , most are showing closed however afew are showing Open and no stealth ports.


Hi babacan,

when Ubuntu is installed it doesn't have any open ports (it doesn't install any server), so it is secure. No servers, no possible connections to your box.

If you do have a server installed (SSH, SMB, FTP, P2P, whatever) then yes, you need to configure the firewall (iptables). 

Apparently you do, as you say that "a few are showing Open". You can run "sudo netstat -natp!grep 0.0.0.0" on a terminal to confirm that.

There are many ways to configure iptables. The easiest and popular is Firestarter as it has a GUI for configuration and you can see active connections and a log events.

Cheers.

---

