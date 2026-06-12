---
title: "Firewall Configuration"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by tyke2806 on 2010-09-06
How do I configure ufw on my remote server to allow only connections from my local windows PC? Is this worth doing for VNC, SSH etc, if I am still allowing incoming for my torrent client on a specified port? As my IP address is not fixed, how do I enter this in the firewall config?
regards
Chris

---

### Post by jtarin on 2010-09-06
There's a graphical interface "gufw" in the repositories. Check Synaptic.

---

### Post by tyke2806 on 2010-09-06
Thnaks I have installed the GUI. How do I enter an IP address when it is variable?

---

### Post by jtarin on 2010-09-06
> **tyke2806 said:**
> Thnaks I have installed the GUI. How do I enter an IP address when it is variable?Where and why do you need to enter an IP address?

---

### Post by tyke2806 on 2010-09-06
I am assuming that if I limit say ssh access to a specific address then this will be more secure than just ernabling the port for all users?

---

### Post by CharlesA on 2010-09-06
> **tyke2806 said:**
> I am assuming that if I limit say ssh access to a specific address then this will be more secure than just ernabling the port for all users?
Correct.

Do you connect from different areas all the time, or just one external IP most of the time?

---

### Post by jtarin on 2010-09-06
Why not setup something like [Webmin]("http://www.webmin.com/")  There is an ubuntu pkg downoad available and a [Dynamic DNS service (free) to administer]("http://www.dyndns.com/support/kb/dyndns.html#howto-install").
[Some more info on Dynamic DNS and Linux.]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch19_:_Dynamic_DNS")

[Webmin demo...login...demo...passwd..demo.]("http://webmin-demo.virtualmin.com/")

---

### Post by CharlesA on 2010-09-06
> **jtarin said:**
> Why not setup something like [Webmin]("http://www.webmin.com/") and a Dynamic DNS service (free) to administer.There is an ubuntu pkg downoad available.
As long as you lock SSH down - use keys only, no password authentication and limit the number of connections per amount of time, you should be fine.

---

### Post by uRock on 2010-09-06
> **tyke2806 said:**
> I am assuming that if I limit say ssh access to a specific address then this will be more secure than just enabling the port for all users?
If the server is at a remote location, which is not on your local network, then you will need it to allow the IP that the ISP gave to your router, not the 192.168.x.x that you are most likely using for hosts inside the local network.

---

### Post by tyke2806 on 2010-09-06
Apologies, I am probably not makiong myself clear. I know my ip address, but is it not fixed. My current address is 94.171.131.68 "cpc3-dudl10-2-0-cust835.wolv.cable.virginmedia.com" , how do I allow this through the firewall when the ip address is dynamic?

---

### Post by uRock on 2010-09-06
> **tyke2806 said:**
> Apologies, I am probably not makiong myself clear. I know my ip address, but is it not fixed. My current address is 94.171.131.68 "cpc3-dudl10-2-0-cust835.wolv.cable.virginmedia.com" , how do I allow this through the firewall when the ip address is dynamic?
Though it renews every day the ISOs normally do not change your IP. Hence the reason sites are able to ban users. The GUI in the router should make opening ports pretty simple. I know Cisco has help files for every screen that explains every function when accessing it via the browser.

---

