---
title: "State of 802.11g in Ubuntu and/or Linux?"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by Mighty_Ferguson on 2006-07-21
Hello,
I've done some searching in the forums and I couldn't find a good answer to this question. I apologize if it's been answered somewhere. If so, please point me to the thread.

My question is, what is the state of 801.11g (as opposed to 802.11b) in Ubuntu and Linux in general? I'm fairly new to both, Ubuntu Dapper being my first real attempt at using Linux as a desktop OS. I used the thread located [here]("http://ubuntuforums.org/showthread.php?t=185174") with some success, and I can get my Linksys WAP54G card to connect in 802.11b mode, but not 802.11g.  Is this a problem that's related to this card/chipset in particular, or is it most cards?  I tried using the "iwconfig eth1 rate 54M" command recommended in the linked thread, but it made no difference for me.  

Now, I realize most people would say that 11Mb is good enough for most use, and you should use a wired connection for large file transfers, etc. But that's not really why I'm asking (although I have read that if you set your wireless access point to mixed mode, it forces all your 802.11g devices to run at 802.11b speeds... not sure how true that is). I'm asking because I'd like to know if there's a way to get the card working to it's full potential, and also to get a sense of the state of wireless in the Linux/Ubuntu world. I'm learning a lot using Ubuntu, and so far I'm impressed.

Thanks for any insight.

-Mighty

---

### Post by reacocard on 2006-07-21
works perfectly for me, even with wep enabled. I use network manager to handle my networking though. perhaps you could try that?

---

### Post by Mighty_Ferguson on 2006-07-21
> **reacocard said:**
> works perfectly for me, even with wep enabled. I use network manager to handle my networking though. perhaps you could try that?

Per the instructions in the How To thread I linked to, I am using Network Manager to handle the connection. I don't see an option for 802.11g vs 802.11b in there though. Am I missing it? After scanning through the How To, it seemed like I wasn't the only person who couldn't get it running with 802.11g. 

Thanks,
-Mighty

PS - While on the subject of Network Manager, is that the best wireless GUI there is for Ubuntu? It doesn't appear to show a list of available access points and their related details.

---

### Post by reacocard on 2006-07-21
Network manager should use 802.11g if it is available. I know it works because my home wireless is set to g-only. And yeah, it's the best I know of. Don't know what you're complaining about. Just click the applet and it gives you a list of available networks and their signal strengths. Looking at the tutorial, I see it's for broadcom wifi cards. Unfortunately, they don't work too well in Ubuntu. I have the Intel 2200 b/g wireless card, which works perfectly.

EDIT: just remembered, network manager needs your /etc/network/interfaces file to be set up in a particular way. everything except the entry for lo needs to be commented out.

---

### Post by awaldram on 2006-07-22
and on the other side I dont think network mangers much good in Dapper.

It doesnt start till gnome starts so no network during boot.
It cant recover gracefully from a suspend
Wont work with mixed networks wep/open/wpa as wpa_supplicant is used to attach to all and doesnt work with wep open for many cards.
And requires 1 password entering for every wpa key set, at boot -- I have 5 !!!!!!!!

Wifi-radar on the other hand

Starts at boot connecting to any network registered with it.
After suspend will do the same (add wifi-radar -d to reume scripts)

And most importantly uses native tools for wep/open and wpa_supplicant for wpa.

On the down side it does require setting up rather than network mangers "Just Works" which as stated should be "Just Might Work if your Lucky"

---

### Post by Mighty_Ferguson on 2006-07-22
> **reacocard said:**
> Network manager should use 802.11g if it is available. I know it works because my home wireless is set to g-only. And yeah, it's the best I know of. Don't know what you're complaining about. Just click the applet and it gives you a list of available networks and their signal strengths. Looking at the tutorial, I see it's for broadcom wifi cards. Unfortunately, they don't work too well in Ubuntu. I have the Intel 2200 b/g wireless card, which works perfectly.

EDIT: just remembered, network manager needs your /etc/network/interfaces file to be set up in a particular way. everything except the entry for lo needs to be commented out.

I'm not complaining, I'm just asking questions and trying to learn. I'll try to find some info about how to edit the interfaces file you're describing.  By the sounds of it, it might just be a problem with my particular wifi card, which was part of my original question.

> **awaldram said:**
> and on the other side I dont think network mangers much good in Dapper.

It doesnt start till gnome starts so no network during boot.
It cant recover gracefully from a suspend
Wont work with mixed networks wep/open/wpa as wpa_supplicant is used to attach to all and doesnt work with wep open for many cards.
And requires 1 password entering for every wpa key set, at boot -- I have 5 !!!!!!!!

Wifi-radar on the other hand

Starts at boot connecting to any network registered with it.
After suspend will do the same (add wifi-radar -d to reume scripts)

And most importantly uses native tools for wep/open and wpa_supplicant for wpa.

On the down side it does require setting up rather than network mangers "Just Works" which as stated should be "Just Might Work if your Lucky"

Thanks, I'll take a look around for information about wifi-radar. Sounds like it might be more what I'm hoping for.

-Mighty

---

### Post by msak007 on 2006-07-22
Mighty_Ferguson, the post you linked to uses bcm43xx-fwcutter in conjunction with the open source Broadcom driver. That driver currently has a limitation of 11 mbps - if you want to take advantage of the full speed of the card, you must use ndiswrapper for now. I was excited when I first found out that there was an open source driver and I could get away from ndiswrapper, but after finding this piece of info I quickly switched back. I currently use ndiswrapper with my WMP54GS (in conjunction with knetworkmanager in Kubuntu) and it connects in 54g mode. I used a couple of resources on these forums to set this card up, but mostly [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-b3e888974e3f23d9367ca6f2f32edcb3764613a5") wiki for reference. If you decide to go that route and need some help, let me know.

---

### Post by Mighty_Ferguson on 2006-07-23
> **msak007 said:**
> Mighty_Ferguson, the post you linked to uses bcm43xx-fwcutter in conjunction with the open source Broadcom driver. That driver currently has a limitation of 11 mbps - if you want to take advantage of the full speed of the card, you must use ndiswrapper for now. I was excited when I first found out that there was an open source driver and I could get away from ndiswrapper, but after finding this piece of info I quickly switched back. I currently use ndiswrapper with my WMP54GS (in conjunction with knetworkmanager in Kubuntu) and it connects in 54g mode. I used a couple of resources on these forums to set this card up, but mostly [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-b3e888974e3f23d9367ca6f2f32edcb3764613a5") wiki for reference. If you decide to go that route and need some help, let me know.

msak007,
Thanks, that answered several of my questions. I do need some help though. I read the wiki you linked to, and if I'm understanding it properly, it seems to include the commands to blacklist the driver I previously installed using fwcutter. Is that correct? If so, I'm not sure how to proceed after that. Did I miss the instructions on setting up ndiswrapper in the wiki, or do I need to use one of the other articles about ndiswrapper (is there one specific to this wireless card)? 

Thanks again,
-Mighty

---

### Post by bodycoach2 on 2006-07-24
I'm not sure if you live in the states or not, but here in USA, we have poor connection speeds, even wired. If you do a wired speed test, you'll see what I mean:

[http://www.internetfrog.com/mypc/speedtest/](http://www.internetfrog.com/mypc/speedtest/)

There are many other free speed tests online, but at best, a 10 Mbps download and 5 Mbps is what you're going to get. Wireless G is important for inhouse business wireless networking, where shared resources are important. If you're using wireless to get online, 802.11b is really all that is needed.

Wireless G does extend the range, and WiMax and 802.11n are even better, but only for range. Internet speeds won't be any better wired or 802.11b. 

Now, you might have one of those super, $100,000 a month bandwidth lines, and I could be wrong. 

The only real reason to use 802.11g is range, and even then it's not much better than b.

---

### Post by msak007 on 2006-07-24
There are lots of threads and resources discussing ndiswrapper, but I'll sum up the steps I took to get my wireless card working on a brand new install (my install comments are commented out with #). In the case of the driver, <driver name.inf> is the driver for your specific card:

1. # Install ndiswrapper-utils 
```
sudo apt-get install ndiswrapper-utils
```

2. # Blacklist built-in bcm43xx driver 
```
sudo echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

3. # Remove the bcm43xx module (if it's already loaded)
```
sudo rmmod bcm43xx
```

4. # Install driver 
```
sudo ndiswrapper -i <driver name.inf>
```

5. # Find out if the driver installed correclty. If it did, you should see a prompt telling you that the driver and the hardware are present.
```
ndiswrapper -l
```

6. # Load ndiswrapper module
```
sudo modprobe ndiswrapper
```

7. # Add ndiswrapper module to startup
```
sudo ndiswrapper -m
```

8. # Create module dependencies
```
depmod -a
```

9. Restart machine - restart is necessary, simply restarting networking won't suffice

You've already installed Network Manager so at this point when you log back in, your wireless card should be working. I've never used Ubuntu w/ Network Manager (I use Kubuntu w/ knetworkmanager), but I assume it should be the same procedure - right-click on the System Tray icon, choose the network you want to connect to, and enter your WEP / WPA key (if applicable). 

P.S. bodycoach2's response does hold true for the limit on Internet speeds, but for home networks where it's not feasible to run a cable and you must use wireless, the speed and range can make a difference when transferring files within the LAN. I'm in this situation, thus my need for g vs. b. If you do not transfer files and are only looking for the speed to get online, stick with the original method.

---

### Post by bodycoach2 on 2006-07-25
> **msak007 said:**
> 

P.S. bodycoach2's response does hold true for the limit on Internet speeds, but for home networks where it's not feasible to run a cable and you must use wireless, the speed and range can make a difference when transferring files within the LAN. I'm in this situation, thus my need for g vs. b. If you do not transfer files and are only looking for the speed to get online, stick with the original method.

Msak007- Do you think a better antenna setup, or even a rangebooster might be a viable alternative to the headaches with trying to get G working right? I guess it's a 'money vs time' thing. 

Also, if you're trying to hook off your neighbors connection, a better range is absolutely necessary.

---

### Post by msak007 on 2006-07-25
> **bodycoach2 said:**
> Msak007- Do you think a better antenna setup, or even a rangebooster might be a viable alternative to the headaches with trying to get G working right? I guess it's a 'money vs time' thing. 

Also, if you're trying to hook off your neighbors connection, a better range is absolutely necessary.

I've never really had a problem getting g working, so I can't vouch for how well "range boosters" or add-on antennas work - I've never had to use them (and they're expensive too, at least the one Linksys sells for their routers). 

As far as picking up a neighbor's connection, I don't advocate that either :). A lesson in security never hurts anybody (hehe), but it's up to you what you decide to do if a neighbor's unprotected network is within range. I've always paid for my internet so have had no reason to jump onto a neighbor's network (not for the Internet connection anyway :D). I do know some people that have an arrangement with their neighbors where they split the cost of the Internet bill and can connect to their network, so if that's the case then yea range would be a big factor there too.

---

### Post by Mighty_Ferguson on 2006-07-25
msak007,
Thanks VERY much for your help thus far. I can now connect at 802.11g speeds using ndiswrapper. 

I must have done something wrong though, because each time I reboot, network-manager doesn't remember my local wireless settings, and when I try to configure them, I'm prompted to enter my default keyring password. Am I correct in my assumption that network manager forgetting the settings is related to the default keyring? I realize you use wifi-radar instead of network-manager, but I'm guessing they may both utilize the default keyring in the same way.

Thanks again, 
-Mighty

---

### Post by msak007 on 2006-07-25
I'm glad you got it working, getting wireless was definitely one of the hardest things to do when I started using Ubuntu. It's much easier now with the inclusion of Network Manager. 

Now as far as Network Manager not remembering settings, unfortunately I've discovered that's one of the disadvantages of using it. I don't use wifi-radar  (that was awaldram ), I never really tried it although I suppose I should to see how it fares compared to knetworkmanager in that respect. I don't know how Gnome's keyring works, but in KDE there's a "wallet manager" that I assume has the same basic functionality. The only way I could get knetworkmanager to remember my wireless preferences (preferred networks, WEP / WPA keys, etc.) was to create a wallet with a blank password and set that to launch at startup. That way it starts up right away without prompting for a password. The first time I launch knetworkmanager, it requests access to kwalletmanager, and once I grant it access (I choose "Always"), it stores all that info in there so it's always accessible at boot up and and connects automatically when I log in. It's probably not the most secure way to store my wireless settings, but I'm willing to risk that for ease of use especially with the wireless connection. I know it doesn't help you much in Ubuntu, but I did find [this]("http://www.ubuntuforums.org/showthread.php?t=218459") thread which I believe answers your question. Sorry I couldn't help you out here, maybe someone who uses Ubuntu and is more knowledgeable in that area can jump in and help out.

---

