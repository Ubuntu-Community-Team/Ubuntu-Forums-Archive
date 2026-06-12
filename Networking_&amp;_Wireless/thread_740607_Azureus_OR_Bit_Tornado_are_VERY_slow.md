---
title: "Azureus OR Bit Tornado are VERY slow"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by Crash90 on 2008-03-30
I have been using Azureus for the past 3 years. I switched over to LInux and resolvingthe NAT problem frustrated me to no end. I correctly set up port forwarding and a static IP - still would received the NAT/firewall problem. My download speeds were highly erratic and would never reach full potential.


I then switched over to Bit tornado and am having the same problem. I NEVER reach my full d/l potential and rarely are my d/l speeds very fast. I avg probably 17 kbps. On a 6210/712 connection, that is just wrong.

Any idea's where to start? On bit tornado my light stays yellow and I never have an upload speed. 


I am behind a WRT150 router. Using a static ip w/ port forwarding or a DHCP steup


Currently Azureus is showing that I am firewalled. I have stopped Moblock and I have no iptables configured - how can I be firewalled? I don't use any firewall programs.

---

### Post by dmizer on 2008-03-31
had this trouble ages ago.

neither of these clients work well with the open version of java shipped with ubuntu.  so, install sun java using any of the multitude of options available to you.  then set it as default with this howto:
[https://help.ubuntu.com/community/Java?#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java?#head-fef9352fb26820bb774df978180c9dd3a60e777b)

---

### Post by Tomatz on 2008-03-31
Check that you port is forwarded correctly in the upnp plugin (azureus)

If not manually open the port in your router settings :)

---

### Post by Crash90 on 2008-03-31
> **Tomatz said:**
> Check that you port is forwarded correctly in the upnp plugin (azureus)

If not manually open the port in your router settings :)

I disabled the upnp plugin so it's not there.


How would I manually open the port? 


Update: I am running a d/l right now. I am maxing out my upload speed (76kb) and achieving medicore speeds (fluctuates from 40kb/s to 90 kb/s)

It still shows I am firewalled? I need to recheck my settings to see if I can increase the d/l speed and figure out why I am still shown as firewalled.

---

### Post by Tomatz on 2008-03-31
> **Crash90 said:**
> I disabled the upnp plugin so it's not there.


How would I manually open the port? 


Update: I am running a d/l right now. I am maxing out my upload speed (76kb) and achieving medicore speeds (fluctuates from 40kb/s to 90 kb/s)

It still shows I am firewalled? I need to recheck my settings to see if I can increase the d/l speed and figure out why I am still shown as firewalled.

Well if you disabled the upnp plugin i would say thats your problem :)

---

### Post by Crash90 on 2008-03-31
> **Tomatz said:**
> Well if you disabled the upnp plugin i would say thats your problem :)

UPNP enabled shows no difference.


Why does it show I am firewalled? I have disabled moblock and my iptables have never been modified.

Though my download speed is better this connection should be much faster.

---

### Post by cozmicharlie on 2008-04-01
It could be your IP throttling you down.  If you have the ports correctly forwarded and firewalls off then it should work. 

 Maybe something here could help - [http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu](http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu)

---

### Post by Tomatz on 2008-04-01
> **Crash90 said:**
> UPNP enabled shows no difference.


Why does it show I am firewalled? I have disabled moblock and my iptables have never been modified.

Though my download speed is better this connection should be much faster.

Because your router has a firewall built into it.

I doubt it is your isp throttling you because they only usually throttle at certain times of the day. My isp only throttles me between 4pm and 12pm if i download more than 350MB between those hours.

Check that upnp is enabled in the **router settings** if it's not enable it then test azureus. If it is enabled type in google *"[router model number] port forwarding"* you should find a howto somewhere.

To enter the router settings (for most routers) put this in your browser url bar:

192.168.1.1

or

192.168.2.1

:)

Explanation of port forwarding:

[http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding)

---

### Post by Crash90 on 2008-04-01
> **Tomatz said:**
> Because your router has a firewall built into it.

I doubt it is your isp throttling you because they only usually throttle at certain times of the day. My isp only throttles me between 4pm and 12pm if i download more than 350MB between those hours.

Check that upnp is enabled in the **router settings** if it's not enable it then test azureus. If it is enabled type in google *"[router model number] port forwarding"* you should find a howto somewhere.

To enter the router settings (for most routers) put this in your browser url bar:

192.168.1.1

or

192.168.2.1

:)

Explanation of port forwarding:

[http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding)
Ha! I am silly. I didn't set up the port forwarding rules in my iptables!
Next question. How do I get my startup boot to have those iptable rules?

I am reading the azureus wiki, but it simply says "create a file" I used the touch command, but it will not create a file!

With the port opened my d/l is more consisent, it stays at higher speeds, but I am still below the average swarm speed!

---

### Post by Tomatz on 2008-04-02
If you use the touch command anywhere but your home folder (usually) you need to do a sudo before touch to grant the command root permissions. E.g

**sudo touch /myfile**

Maybe thats the problem :)

---

### Post by Crash90 on 2008-04-02
> **Tomatz said:**
> If you use the touch command anywhere but your home folder (usually) you need to do a sudo before touch to grant the command root permissions. E.g

**sudo touch /myfile**

Maybe thats the problem :)

that did the trick

Any ideas on how to increase my d/l speed? While I sometimes go above the swarm avg speed (on this torrent), I am generally below it by 20-30kbps. 

I have already used the good settings wiki. The problems I run into are the firewall for dht and it later turns yellow and says "NAT ok?". Meaning reachability ok but no incoming connections recently.


UPDATE: I have changed NOTHING. All of a sudden, I get a green light on DHT and on my torrent. HOWEVER, my connection is still well below the average. On a fast connection, this should not be happening. My upload is reaching full potential (76k).

I don't believe this is a throttling issue, as at times I will hold a higher than average speed (only for 1-2 minutes). However, when this happens the torrent avg. speed dives.

---

### Post by Tomatz on 2008-04-03
This maybe a silly question but are there plenty of seeds on the torrent you are downloading?

---

### Post by Crash90 on 2008-04-04
> **Tomatz said:**
> This maybe a silly question but are there plenty of seeds on the torrent you are downloading?

Yes

---

### Post by Tomatz on 2008-04-04
Have you forwarded both **tcp** and **udp**. If not then that's defiantly the problem as the behavior you describe sounds like it's only connecting via **tcp** :)

---

