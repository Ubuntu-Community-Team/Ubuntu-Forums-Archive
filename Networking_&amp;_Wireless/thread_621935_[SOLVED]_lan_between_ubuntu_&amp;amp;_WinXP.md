---
title: "[SOLVED] lan between ubuntu &amp;amp; WinXP"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by zazze on 2007-11-24
Hi, I'm an italian boy, so i coul don't speak english very well.
I have a fixed PC where is installed Ubuntu dapper drake 6.06 lts, an a notebook where is installed WinXP.
Now, both PCs are conntected to a router, in particular the Ubuntu pC is connected through an Ethernet wire, while WinXP PC is connected by a wirelless Pen.
So, i've assigned a static IP on the pc with ubuntu, while a dhcp IP address on the pc with winXP.
Now, if i ping winXP from Ubuntu, i 'haven't response from winXP, while if i ping the router from Ubuntu, i have responsens.
So, why i haven't responses from winXP?
I hope that  I've explain the problem well.
Thank yuo.

---

### Post by zazze on 2007-11-24
Can you help me, please?
If i have not explained very well the problem, please you tell me it.

---

### Post by zazze on 2007-11-24
OK, i have understand. The problem is that i have winXP, don't it?
In this case, i tell you that i don't like winXP, but i'm working as networker and i must resolve this problem for a company!
I'm using ubuntu 5.4 since 1 year ago!

---

### Post by jetsam on 2007-11-24
HI.  Sometimes it just takes a little time to get a response.  

It's possible the Windows XP firewall is dropping the request.  Go into the firewall settings through the XP control panel and make sure "don't allow exeptions" is NOT checked in the general tab and that under Windows Firewall-->Advanced-->ICMP Settings, "allow incoming echo request" IS checked.

Hope that helps.  

I'm assuming both computers have net access, so it isn't a connectivity problem.

---

### Post by zazze on 2007-11-24
thank you JatSam, It is the first time that i write in this forum and i'm happy that someone has understood my question although i don't speak english very well.
Yes, both computers have net access. Now i'm testing what you said.

---

### Post by zazze on 2007-11-25
I have verified what it has been said above, and it is all OK.
So, what is the problem?Please, help me.

---

### Post by mellowd on 2007-11-25
You mean OK in the sense that it still isn't working?

---

### Post by zazze on 2007-11-25
I  want to say that "don't allow exeptions" is NOT checked in the general tab and that under Windows Firewall-->Advanced-->ICMP Settings, "allow incoming echo request" IS checked.
However, the network still isn't working.

---

### Post by mellowd on 2007-11-25
Can you ping the ubuntu box and router from xp?

---

### Post by zazze on 2007-11-25
Yes, I can.
I can also ping the router from ubuntu

---

### Post by mellowd on 2007-11-25
This is probably pointless but I want to have a look at this command as well. On the ubuntu box type this:

traceroute x.x.x.x


Where x.x.x.x is the ip address of your windows box. If traceroute isn't installed I reccomend installing it because its very useful and very small

---

### Post by jetsam on 2007-11-25
Darn.  

Some kind of firewall is the most likely cause of this.  Is it possible there is another firewall installed on the machine (Zone alarm, Norton)?  Some VPN clients can also cause this problem.  

Temporarily disabling the windows firewall entirely might be a good idea.  This could rule it out as a cause.  

Can you ping the xp machine from itself?-- like so:
```
ping 127.0.0.1
```
If you can't, something is very messed up with the xp machine.  

Can you ping the xp computer from the router?  You need to log into the router's administration page to do this, and then find its diagnostics functions.  This is often available by opening a web browser to  192.168.0.1 or 192.168.1.1, but the exact address and password depends on the router and its configuration.  

A google search turned up this long thread in a networking support forum of people being quite frustrated by this problem.  It might help, but it is very long and complex: [http://forums.speedguide.net/showthread.php?t=190294]("http://forums.speedguide.net/showthread.php?t=190294")

There's also a chance the issue is malware related.

I don't _think_ it should matter, but is the XP computer set up to share files?  Enabling sharing might make it more responsive.

---

### Post by zazze on 2007-11-26
OK. I've resolved the problem. I have disabled and after enabled the windows firewall and after that ubuntu ping XP. 
I'm very happy to have receved your assistance, thank you very much. 
Goodbye!!!

---

### Post by mellowd on 2007-11-26
Mark the thread as solved if you get the chance :)

---

### Post by zazze on 2007-11-26
Ok

---

