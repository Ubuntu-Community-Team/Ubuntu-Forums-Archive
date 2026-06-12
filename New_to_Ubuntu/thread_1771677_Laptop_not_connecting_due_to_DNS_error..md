---
title: "Laptop not connecting due to DNS error."
date: 2011-05-30
forum: New to Ubuntu
---

### Post by Mindswap1 on 2011-05-30
Laptop not connecting due to DNS error, what to do? SO I had to unplug my modem, and router, and then replug them in, but now my laptop cannot connect to the internet. My desktop connects fine, its just my laptop, and all the other wireless devices i.e laptop and psp. I called my isp, and they said if the desktop works then its not their problem any more :(.

---

### Post by lordadi on 2011-05-30
Change your DNS to use Google or openDNS.

Google:
8.8.8.8
8.8.4.4

openDNS:
208.67.222.222
208.67.220.220

Let me know if you need help getting these inputted into your connection settings.

---

### Post by crispy_420 on 2011-05-30
What the ISP said is sadly the truth, if you got the internet their work is done. So if you have multiple devices not connecting we can rule out client side hardware/software. Do these devices see the wireless router?

First suggestion would be log into router and reconfigure. Start with no security for initial setup and make sure you can connect. Then move on to the security setting of your choice (WPA/WPA2).

Possibility of failing router?

---

### Post by lordadi on 2011-05-30
Actually, my bad - I didn't check to see what the problem was (I realize now that OP is not very clear as to "DNS issue").

On your laptop, what do you get when you try to go to google.com?

---

### Post by 5149.5 on 2011-05-30
The output of nm-tool will give several clues. Enter nm-tool in terminal and paste the results in a new post. Highlight the text and click the # button at the top of the window.

---

### Post by Mindswap1 on 2011-05-30
I have tried to connect to the Router's network settings through 192.168.1.1 however when I input the default username and password, it does not accept it. However when I tried on my laptop it accepts it, but I can't do anything cause every time i try to click something is say no internet connection. So it goes to the site, but then it doesn't like me click anything. 

When I try to access google.com it says cannot connect to server, and my psp says cannot connect due to DNS error. 

Here are the results of nm tool 
```

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:21:97:C4:CD:A5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         68.197.108.77
    Prefix:          21 (255.255.248.0)
    Gateway:         68.197.104.1

    DNS:             167.206.245.130
    DNS:             167.206.245.129

```

---

### Post by 5149.5 on 2011-05-30
Your router appears to be at :68.197.104.1 and your DNS servers are at: 167.206.245.130 and             167.206.245.129. Can you ping all of them? How do these addresses compare to the computer that is working?

---

### Post by prajivprasad on 2011-05-30
are you able to connect with the ip address atleast ? if yes .
try changing the dns as suggested earlier and check .

---

### Post by crispy_420 on 2011-05-30
Are you connected directly to the modem/internet with that address? That is outside of the private address listings.

---

### Post by Mindswap1 on 2011-05-30
I'm really new to all of this so I don't know how to do many things >.< how would I ping those addresses? And Also how do I change the dns >.< I can't access the router network settings like I said. And yes that input was from a computer that is connected directly. r

---

### Post by crispy_420 on 2011-05-30
Start from scratch. 
Leave all devices unplugged for a few minutes to reset ISP connection status.
Plug in modem and let it get fully operational. 
Plug in router and let it establish connection.
Try to access router page (192.186.1.1 or 1092.168.0.1 usually). You can also find this address via ifconfig on a connected linux box. It should be listed as the gateway.
Begin router setup. Verify wired connection functional.
Setup wireless. Start with no security to ensure connection works. After connection status functional, setup wireless security.

I made a lot of generalizations or brief comments on each step so feel free to ask questions.

---

