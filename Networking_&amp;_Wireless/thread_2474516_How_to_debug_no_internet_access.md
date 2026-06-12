---
title: "How to debug no internet access"
date: 2022-05-01
forum: Networking &amp; Wireless
---

### Post by usjes on 2022-05-01
Hi, 

I have suddenly lost internet access on Ubuntu 18.04.6 LTS. It was working fine earlier. It seems like it stopped working when I disabled protonvpn but that may have been a coincidence. I have rebooted the laptop and also rebooted the router but still no internet access. I have tried various methods of disabling/re-enabling wireless and restarting network services but nothing has restored my internet access on this specific machine. The only error message I have seen is that sometimes when re-enabling a bubble flashes up saying: "Activation of Network connection failed.". 
- All other devices still have internet access
- When I log into the admin panel on my router it lists this machine as connected 
- The WiFi networks icon in the upper right of the desktop for this machine also shows it as connected 
- When I ping [www.google.com](www.google.com) it times out with the error message "Name or service not known"
- When I ping google's IP address all packets are received correctly. This suggests that there is nothing wrong with the hardware and that I am actually connected ? 
- On the off-chance that there was some mac address- based filtering going on on the router I took the MAC address from another device (which I then powered down) and put it in the 'Cloned Mac address' in the settings dialog for the WiFi connection on the machine without access but it still wont give me internet access
- I have tried both Chrome and Firefox but neither will connect to any site
- When I try putting Google's IP address directly into the address bar in the browser it still wont connect so it seems like it is not simply that it won't translate web addresses into IP addresses as the experiments with ping might suggest. 
So, does anyone know what steps I can follow to debug this or indeed commands to completely restart all services that might be contributing to this problem ? 

Thanks, 

usjes

---

### Post by TheFu on 2022-05-01
If you can ping 1.1.1.1 and not resolve google.com, then it is a DNS issue, not a connectivity issue. Look in that area - DNS.

---

### Post by usjes on 2022-05-01
> **TheFu said:**
> If you can ping 1.1.1.1 and not resolve google.com, then it is a DNS issue, not a connectivity issue. Look in that area - DNS.

I can ping 1.1.1.1 and indeed it is also the only address I have found that actually renders anything in Firefox. It seems I can also ping many other sites (once I know the IP address) with 0% packet loss however once I input either the IP address directly or the website URL in a browser address bar it fails to connect with the Error message: 'Server Not Found'

So, how exactly to I look into the area of DNS on Ubuntu. Is it a service I can restart ? A program I can re-install ? Some config files I can check for corruption ?

---

### Post by TheFu on 2022-05-01
> **usjes said:**
>  So, how exactly to I look into the area of DNS on Ubuntu. Is it a service I can restart ? A program I can re-install ? Some config files I can check for corruption ?

Yes.  However, the way I do it isn't the way that 99% of people do it and is probably not what you would want to do.  Sorry, I'm not any more help than saying, "you have a DNS issue. Fix that."  I got too frustrated with the changes in Ubuntu DNS handling, so I rip it all out and manually point the DNS at my own LAN DNS server.  Like I said, probably more than what most other people would want.

Hopefully, someone else will come along, help you determine which DNS setup you are using (there are multiple choices), and will be able to recommend things to change/try.

As a starting point, you could download and run either the wireless troubleshooting script or the system information script from here: [https://github.com/UbuntuForums](https://github.com/UbuntuForums)  I think that both will grab some information to answer the questions others will need to know to be able to help.

---

### Post by The Cog on 2022-05-02
A quick one-liner that should get you working until next time your connection goes down and up again is this:
```
echo nameserver 1.1.1.1 | sudo tee /etc/resolv.conf
```
It tells the PC to use 1.1.1.1 (a well known public server) as the name lookup server. But collect info about your existing configuration first so people can try to debug.

---

### Post by usjes on 2022-05-02
I finally figured out what the problem was thanks to this page ([https://www.reddit.com/r/ProtonVPN/comments/pit989/deleted_by_user/](https://www.reddit.com/r/ProtonVPN/comments/pit989/deleted_by_user/)). It was related to protonvpn. In case anyone else encounters it :
When I issued the ipconfig command there was an entry for a  strange device listed:
[I]         ipv6leakintrf0: flags=195<UP,BROADCAST,RUNNING,NOARP>  mtu 1500

[/I]Apparently this interface is intended to prevent IPv6 leaks and it is supposed to shut down once you close protonVPN but for me it did not and persisted even after I rebooted the laptop. As long as it was active it seems it was swallowing up all the traffic to my browser. To get rid of it simply issue the command:
         [I]ip link delete ipv6leakintrf0

[/I]My internet access in my browser is now restored

Thanks,

---

### Post by TheFu on 2022-05-02
Preventing DNS leaks is something that most VPN providers ignore. Good that yours is paying attention, though it is bad that the program start/stop isn't handling it correctly.

---

