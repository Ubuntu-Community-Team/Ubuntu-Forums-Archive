---
title: "Activation of network connection failed Ubuntu 18.04"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by jacobseed15 on 2018-06-20
This has happened before on 16.04 about a year ago. I've never been able to connect to the WiFi or Ethernet on any Linux distro on my desktop (custom built if that helps with anything). I've looked hours for solutions but nothing that has worked for my yet.
[Here]("https://pastebin.com/bGBbmL4F") is my system's wireless info

I would appreciate simple answers, for I am still very new to Linux, thank you.

---

### Post by TheFu on 2018-06-20
Does the wired etherent work?  That is usually much easier to solve.  
Does the wifi and ethernet work with other computers?

When you say it doesn't work, what exactly do you mean?
Can you ping the router by IP address?
Can you ping 8.8.8.8?
Can you ping google.com?

I'll take a look at the pastebin, but my wifi-fu is weak.
In general, you'd look at the device model, google that with "ubuntu" and find solutions that have drivers or settings to make it work.

The realtek  driver used for the ethernet card often works, but sometimes dropping back to the r8168 (not r8169) driver version works better for people. Google will find lots of guides for that.

The wifi is seeing 4 different wifi networks (SSIDs), so you'll need to connect using valid credentials to 1 of those. The RedLightDistrict_2GEXT has lower power than I'd like for the closest AP.  For example, mine Quality=65/70 going through a few walls about 20 ft away.

---

### Post by jacobseed15 on 2018-06-20
Ethernet is not an option, but I have tried to connect an ethernet cable to my laptop(Win10) to try to transfer the WiFi.
WiFi and Ethernet works on everything except my Ubuntu. I dualbooted my PC alongside Windows 10, and Windows 10 can use WiFi and Ethernet perfectly fine.

None of the pings work
[ATTACH=CONFIG]280166[/ATTACH]












I will look it up, but just in case it helps, my WiFi card is TP-Link TL-WDN4800

RedLightDistrict is our WiFi network, but there are 3 networks that it has: RedLightDistrict, RedLightDistrict_2GEXT, and RedLightDistrict_5GEXT.
RedLightDistrict_2GEXT always appears in visible networks, RedLightDistrict occasionally appears, and RedLightDistrict_5GEXT never appears. (All 3 of them appear on all other devices, just not Ubuntu)
The Modem is just in the room below mine, so it's not that far away.

---

### Post by TheFu on 2018-06-21
I googled "ubuntu TL-WDN4800"  [https://askubuntu.com/questions/443842/installing-tp-link-tl-wdn4800-adapter-with-ath9k](https://askubuntu.com/questions/443842/installing-tp-link-tl-wdn4800-adapter-with-ath9k) was the result. Did you try that?
[https://ubuntuforums.org/showthread.php?t=2260471](https://ubuntuforums.org/showthread.php?t=2260471)  was also found, though your adapter seems to be working on some level.
Can you try to connect to the router, then ping the router by ip please?  You'll need to know the IP for the router for the ping to work.

From the info I've seen, that wifi adapter should "just work" with Ubuntu.  Could it be incompatible with the AP?  I've seen issues with Netgear APs over the years.

---

### Post by jacobseed15 on 2018-06-21
I took a look at both of the links, and neither of them give a solution that works in my case. From the first link, he said go to the terminal and type "sudo apt-get install firmware-atheros" and I did, but I got this in return:
```
Reading package lists... Done
Building dependency tree
Reading State information... Done
E: Unable to locate package firmware-atheros
```

I did this several times, but nothing. 

I brought my desktop downstairs, and connected it directly to the router, and I still get "Activation of network connection failed"

By the way thank you for trying to help me, I appreciate it

---

### Post by TheFu on 2018-06-21
You have a chicken-egg problem.  You cannot install packages over the internet until you get the internet working.  Getting wire networking working is usually 100x easier than wifi, if there are issues.  

I tried to install that package on my system (knowing I could break out ) and it isn't found.  Wild goose chase, sorry.

Can you make a bootable flash drive with ubuntu and get online?  This is just another test.  After all, the installation program probably got online just fine, right? "Try Ubuntu" is what you want. This is a basic skill for handling all sorts of Linux issues, BTW.

BTW, I'd hoped that one of the wifi experts here would have responded by now.  I saw one of them active yesterday.  Guess the title for this thread didn't jump out at them. 

What type of wifi-router are you attempting to connect with?

---

### Post by jacobseed15 on 2018-06-21
I tried booting up the "Try Ubuntu" from a flash drive, and still the same exact issues.

The only thing I could possibly think of is maybe downloading drivers onto my Windows 10 partition, boot up Ubuntu, go to my files and find the drivers that were download onto Win10, then transfer them to my Ubuntu partition and then install them. Do you think that would be possible? I doubt it would, but what would I know

Also our provider is Comcast, and we are using the default Xfinity modem-router they have provided us with.

---

### Post by jeremy31 on 2018-06-21
What does the Try Ubuntu give for results in terminal for ```
iwconfig
```
Or any chance of wireless script results from Try Ubuntu?

---

### Post by jacobseed15 on 2018-06-21
> **jeremy31 said:**
> What does the Try Ubuntu give for results in terminal for ```
iwconfig
```
Or any chance of wireless script results from Try Ubuntu?

On Try Ubuntu, the iwconfig results were:
[ATTACH=CONFIG]280175[/ATTACH]

Here is the wireless script on Try Ubuntu: [https://pastebin.com/iWiedD7T](https://pastebin.com/iWiedD7T)

---

### Post by jeremy31 on 2018-06-21
I would look at the answer at [https://askubuntu.com/a/810780/300665](https://askubuntu.com/a/810780/300665)
Make the changes on the installed Ubuntu, reboot and ```
sudo iwconfig wlp6s0 txpower 18
```
See if you can connect but you might need to delete that Hotspot connection

---

### Post by jacobseed15 on 2018-06-21
I took a look at that link, and did as the solution said, and what do you know, it worked! WiFi and Ethernet works perfectly now, and now all 3 of my networks show up in "Visible Networks" all the time now. Thank you everyone from helping me out with this problem, I thought I would never find a fix for this. :D

---

### Post by acero6 on 2018-12-06
If a dual boot with Windows 10, you may need to disable the fast startup options first. See link...

I needed to do this for a wired connection to start functioning

[https://youtu.be/ZGdlDR2FC_A](https://youtu.be/ZGdlDR2FC_A)

---

