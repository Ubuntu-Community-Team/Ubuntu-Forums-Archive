---
title: "Unable to connect to School Wifi"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by iceabeam on 2014-09-18
Hi guys, I've recently installed Ubuntu 14.04 on my Chromebook and have been having lots of difficulties with it. I have reinstalled six times so far and everything works great on this installment, but I found out that I am unable to connect to my school wifi while I can connect to my home wifi. My home and school wifi are both WPA, WPA2 and I do not understand why the school's wifi doesn't work. I can connect to the school's wifi on ChromeOS, but switching into Ubuntu will say I'm connected when reality I am not connected.

 I ran the wireless script here while connected to my own wifi and [this ]("http://pastebin.com/t0uh6QeE")was the result. If needed, I will run the wireless script tomorrow while connected to the school wifi. T

hank you so much for all the help and please let me know if I am missing any more details.

---

### Post by Bucky Ball on 2014-09-18
You possibly need some details from the school IT. DNS server IPs could be it if you are connected by can't actually get out of the LAN to the WAN. So, you're connected to the school network, just can't get to the internet and browse the web? Tried asking the IT department?

---

### Post by iceabeam on 2014-09-18
Possibly, it says that I am connected to the Wifi but I am constantly disconnecting. When attempting to browse the website, I get a "Resolving Host" error. And unfortunately I am not sure if we have an IT department at my school.

---

### Post by Bucky Ball on 2014-09-18
Well, there must be someone overseeing the server, or even just the router/access point that allows people to connect wirelessly. Might pay to have a talk with them and see how things are set up at their end. 

You might want to research the problem and trawl through here:

[https://duckduckgo.com/?q=resolving+host+ubuntu](https://duckduckgo.com/?q=resolving+host+ubuntu)

Tweak the search criteria to get more specific.

---

### Post by iceabeam on 2014-09-18
Sounds good, thank you for  your help!

---

### Post by Bucky Ball on 2014-09-18
Let us know how you get on and update with any developments. Clues might jog the brain.

Here's one clue:

> ... make sure the name in /etc/hostname is the same one that you use in /etc/hosts.

From [HERE.]("http://ubuntuforums.org/showthread.php?t=1022133&p=6439577&viewfull=1#post6439577") Do you receive the 'Unable to resolve host' error whenever you use 'sudo' in a terminal? If it is at another time, please describe exactly when the error occurs and provide terminal output, if possible, or anything else you can think of.

PS: Whatever you have in /etc/hostname should be the same as the entry for 127.0.1.1 in /etc/hosts ...

---

### Post by iceabeam on 2014-09-18
I'll try that tomorrow, when I am at school. 

Also, how can I get to /etc/hostname? 

Sorry, and thank you so much for your continued help.

---

### Post by Bucky Ball on 2014-09-18
I've jailed your duplicate post, but don't panic. That's what we do. We don't delete posts.

Open a terminal and use:

```
nano /etc/hostname
```

Open another terminal and:

```

nano /etc/hosts
```

See if they match. Try this when 'connected' to your school's network.

---

### Post by varunendra on 2014-09-20
@iceabeam,

I think you *should* run the script when connected to school network, and post back its report too.

**PS:**
Not related to the school network problem, but I also thing you should change your own router's encryption to pure WPA2-PSK with AES (CCMP). Not only it offers a stronger encryption, but usually a better connection/speed too. The 'TKIP' part of the WPA/WPA2 mixed mode compromises the speed and overall performance.

---

