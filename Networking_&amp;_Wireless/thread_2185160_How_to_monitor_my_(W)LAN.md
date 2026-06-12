---
title: "How to monitor my (W)LAN?"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by LinuxUser666 on 2013-11-01
Hello fellow Ubuntu users, I am running 32-bit Xubuntu 12.10 and I am curious how to monitor my home network.
I have few questions: 
    1. How can I see all the devices currently connected to my Wi-Fi? (And can I? Since I am using computer that is connected over ethernet cord)
    2. How can I shut them off the my network?
    3. Is there any way to protect myself from possible MITM attacks? 
    4. Does any GUI-based app for full network monitoring exists? 

My regards, stay brutal. :guitar:

---

### Post by tgalati4 on 2013-11-01
1.  Log into your wireless router's webpage, typically [http://192.168.1.1](http://192.168.1.1) to view connected devices.
2.  You can use MAC address filtering to only allow specific devices to connect.  The MAC addresses are shown in 1. above.
3.  Number 2 above helps, but describe the scenario for Man in the Middle attack.  Unless there is a white van parked in front of your house, it's hard to imagine such an attack with the short range of WiFi.  The bigger threat is router firmware penetration and of course ISP monitoring by much larger entities.
4.  I like *etherape*, but there are a bunch of tools that you can use:

```
apt-cache search TCP monitor
```

---

### Post by LinuxUser666 on 2013-11-01
Yeah I already knew that, I will just try to find some exploit tool that could me of more use for monitoring my network. One extra question, is there a way for me to be a MITM for all the devices on my (W)LAN? 
And that advice about seeing devices connected by accessing my router's UI and see it all is of no use to me.
What if I am on network where I do not know the data required to connect to router's UI and see the devices? I need a tool that strictly scans both wired and wireless connected devices. Please give me more details and instructions. I have been googling and hitting the wall, I get results for wire connected devices but nothing solid on how to handle wireless.

My regards, stay brutal. :guitar:

---

### Post by tgalati4 on 2013-11-01
You need penetration tools to explore a wireless network that you do not manage. I was under the impression that this was your network that you wanted to monitor.  The explanation of where to find and how to use those tools are beyond the Code of Conduct of this forum.

---

### Post by wildmanne39 on 2013-11-01
> What if I am on network where I do not know the data required to connect to router's UI and see the devices? I need a tool that strictly scans both wired and wireless connected devices.Then you have no business trying to see what devices are connected to someone else's network, I suggest you try the backtrack forum.
Thread closed!

---

