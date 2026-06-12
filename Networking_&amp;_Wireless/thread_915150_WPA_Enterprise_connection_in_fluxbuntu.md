---
title: "WPA Enterprise connection in fluxbuntu"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by ulugeyik on 2008-09-09
The only way I am aware to connect to wireless networks in my institution is to go via networkmanager and follow the instructions below:
[http://prowiki.isc.upenn.edu/wiki/Configuring_Ubuntu_For_AirPennNet](http://prowiki.isc.upenn.edu/wiki/Configuring_Ubuntu_For_AirPennNet)

I think the essence is to be able to use "WPE Enterprise" with options such as "EAP Method", "TTLS", "PAP" and enter username and password. 

NetworkManager does not appear to be compatible with fluxbuntu. Does anyone know an alternative way of connecting to a network like this? Or is there a way to get NetworkManager working under fluxbuntu?

Thanks,

---

### Post by snowpine on 2008-09-10
> **ulugeyik said:**
> The only way I am aware to connect to wireless networks in my institution is to go via networkmanager and follow the instructions below:
[http://prowiki.isc.upenn.edu/wiki/Configuring_Ubuntu_For_AirPennNet](http://prowiki.isc.upenn.edu/wiki/Configuring_Ubuntu_For_AirPennNet)

I think the essence is to be able to use "WPE Enterprise" with options such as "EAP Method", "TTLS", "PAP" and enter username and password. 

NetworkManager does not appear to be compatible with fluxbuntu. Does anyone know an alternative way of connecting to a network like this? Or is there a way to get NetworkManager working under fluxbuntu?

Thanks,

Hi Ulugeyik, Fluxbuntu uses a lightweight network manager (Apps->Net->network-config). If that doesn't do what you need it to, maybe we can help you troubleshoot the problem with networkmanager?

Personally, when I used Fluxbuntu, I used an application called 'rutilt'. I also experimented with 'wicd'. There are a number of wireless managers in the repositories, so I'm sure you'll be able to find a solution. Good luck!

---

