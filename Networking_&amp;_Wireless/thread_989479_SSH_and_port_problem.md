---
title: "SSH and port problem"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by danggrianto on 2008-11-21
i can't access my home pc through ssh.
it is said that connection timed out.
i tried in my campus and it works fine. maybe it is because of the network.
when i used port tolls at canyouseeme.org and put any port it just said that connection timed out.
i tried to contact the ISP and they said they never block any port instead port 25.
can somebody help me?
it is the default installation so im sure i dont have any firewall on me.

---

### Post by jonobr on 2008-11-21
Hello


Could you define a bit more?

You use PC1 to connect via SSH to PC2

PC1 OS = ?
PC2 OS = ?

When connecting from Campus , you have PC1 going to PC2 and all is ok.

When you go from somewhere else? Dont know where you dont work.
Are you using PC2 or another machine, is it the same machine?

If you open a terminal, and you type,
telnet <ipaddress of other pc> 22
what do you get?

Can you access the other machine on other ports outside of port 22?
eg FTP, port 80 etc?

---

### Post by doas777 on 2008-11-21
my first guess would be that a firewall is in the way. is your home PC set to allow tcp 22 traffic? if you have a router, did you forward tcp 22? also can you connect to ssh locally? if not then it may be a problem with ssh itself.

good luck,
franklin

---

### Post by danggrianto on 2008-11-21
> **jonobr said:**
> Hello


Could you define a bit more?

You use PC1 to connect via SSH to PC2

PC1 OS = ?
PC2 OS = ?

When connecting from Campus , you have PC1 going to PC2 and all is ok.

When you go from somewhere else? Dont know where you dont work.
Are you using PC2 or another machine, is it the same machine?

If you open a terminal, and you type,
telnet <ipaddress of other pc> 22
what do you get?

Can you access the other machine on other ports outside of port 22?
eg FTP, port 80 etc?

here is the description:
i use 3 device:
1. PC - ubuntu linux
2. laptop -ubuntu linux
3. n95 to access ssh and also ftp

i tried to access either PC and laptop through ssh either way. pc access laptop and laptop access pc. but didnt work. also i cant acces both of them through n95.
when i was at my campus i tried to acces my laptop using my n95 and it worked.
so i think the problem is my home network.
i am using comcast cable and my router is linksys wrt54g

however i can access remote desktop using vinagre (local only tho.)

---

### Post by superprash2003 on 2008-11-22
when accessing locally ensure that you are using the internal static ip

---

