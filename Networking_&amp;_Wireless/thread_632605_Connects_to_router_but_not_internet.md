---
title: "Connects to router but not internet"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by xxtodd91xx on 2007-12-05
I have a D-Link AirPlus XtremeG DWL-G510 wireless card and i am running ubuntu 7.10  gusty gibbon. I can see my wireless router but when I go to connect it like searches for the network key or whatever and then it just stops searching. When I go to manual configuration I try static IP and I also try DHCP and it also does not work. Please help.

---

### Post by jasmuz on 2007-12-05
Do you have it working with a Static IP address or a DHCP one?
If so, are the DNS servers properly located on such configuration.

Go check that!

---

### Post by xxtodd91xx on 2007-12-05
I have DHCP one clicked. Should i try to put it on static IP and all?

---

### Post by xxtodd91xx on 2007-12-05
anyhelp?? now it does not connect to my router anymore but i can still see my router. !

---

### Post by diplo on 2007-12-05
It would be worth a try.

If you can see your router that will be your gateway

I.E :  192.168.0.1

So set your static IP to say 192.168.0.10 and your mask to 255.255.255.0

I can't see it being the router not giving you out a DHCP address as this is pretty much standard setup but it's worth a try. If this does work it may be worth logging into the routers web interface IE : [http://192.168.0.1](http://192.168.0.1) and looking at the network settings and turning on DHCP.

---

### Post by xxtodd91xx on 2007-12-05
I tried that. didnt work. still can see my router but cannot connect. I also went into my router web interface and DHCP is already on...

---

### Post by xxtodd91xx on 2007-12-05
Can someone please help me. I have no clue pn what to do I'm not experienced with Linux and all I only know windows. I still can see my router and I keep trying to connect but it done  Work!!!!!

---

### Post by MikeyXX on 2007-12-05
What do you mean you can see the router but not connect? Do you mean you can see the wireless AP but it won't let you connect to it?

---

### Post by xxtodd91xx on 2007-12-05
YeA when I got to look what wireless networks are in my area I can see mine but when I try to connect it wonnt let me

---

### Post by lionel47 on 2007-12-05
Do you get some kind of error when you try to connect?  How about walking us step by step with what's happening?

---

### Post by mellowd on 2007-12-05
Open a terminal and type the following:

```
sudo apt-get install traceroute
```

Once that is done, still in the terminal type this:

```
traceroute www.google.com
```


when that is completed type this:

```
ifconfig
```


Paste all your results here please.

---

### Post by xxtodd91xx on 2007-12-05
ok. i go up to the little network thing at the top of the screen and then i left click on it and click on my network and then it will say trying to connect and then it goes off and it makes me have to click on my network again. my computer is dual booted with windows xp and ubuntu and on xp it works fine but on ubuntu i cant acess internet

---

### Post by xxtodd91xx on 2007-12-05
ok i will do that now mellowd

---

### Post by MikeyXX on 2007-12-05
Yes, step by step. IE you click the wireless icon up at the top and you see the wireless ap's available. Is yours shown with an antenna and a shield or nothing?

Not to jump the gun, But you may want to remove the WEP or WAP security on your AP to see if it'll connect. As well, remove any filters on your AP such as MAC address filters etc. IE reset it to factory.

---

### Post by MikeyXX on 2007-12-05
Oh man, I was out of sync on the conversation, didn't realize we had two pages.

---

### Post by xxtodd91xx on 2007-12-06
ok still having problems I changed the first post up some.

---

### Post by MikeyXX on 2007-12-06
Did you reset your router to default and attempt connection? Did it work then?

---

### Post by mellowd on 2007-12-07
I'm still waiting for you to post the results of the commands I asked you to type

---

### Post by xxtodd91xx on 2007-12-07
yes I restored my router to default and tried it but no luck. I didnt have a way to post all the info mellowd I am doing them steps right now

---

### Post by gubemton on 2007-12-08
woah, bugmenot account worked

anyways, i have the same problem, this screenshot basically sums it up

it can connect to router (i'm assuming, because the router recognizes it), and it can scan for hotspots

---

