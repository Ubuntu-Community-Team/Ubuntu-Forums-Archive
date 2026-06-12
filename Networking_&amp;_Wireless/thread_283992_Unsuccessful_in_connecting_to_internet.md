---
title: "Unsuccessful in connecting to internet"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by theta on 2006-10-25
I'm terribly sorry to request help for my first thread but when you understand what is happening, perhapse you can understand. I tried Ubuntu right off the disk for awhile and I like it more than I like any of the Windows operating systems. However, I hadn't used anything other than Windows before (except that of a Mac computer... Eh), and I wasn't sure if I was ready for it or not.
 Well, I decided to install Ubuntu, and since I had so much stuff scattered on my computer (That already had lots of stuff on it when I got it), I decided to wipe my drive for the room needed. Well, needless to say, when I was done installing Ubuntu, the internet didn't work! I sat there for a long time trying to get back on the network, to no avail.
 I've been trying fruitlessly for a week and a half now just trying to get back on the internet, by going through these forums periodically on someone else's computer, messing with things, etc. I'm becoming nervous because there are important things waiting for me on the internet that I can't get to, while at the same time, I'm becoming very frustrated because nothing is working, no matter how close it seems I come. I was about to switch back to Windows when I realised I had no access to any windows CDs... Anywhere. Then I realised I didn't want to go back anyways, since I feel it's still possible to get back on with Ubuntu, seeing as alot of other people with a similar (but apparently not the same) problems got it to work, and so I'm willing to try just about anything.
 I'm not sure what information to put, so any guidance would be very-well taken, but I'll try. My router is an "ewire" and I'm on the SBC Yahoo internet provider. I am not the only computer on the network, and my computer is not the main one. I have a dell pentium four. The internet worked before on Windows XP *and* on Ubuntu when I was running it from the CD while Windows XP was installed. I am very desperately in need, and would love any help given. Thank you.

---

### Post by adwait on 2006-10-25
From what I can gather from your post, your network is connected to the net using SBC Yahoo and you are on that network, not directly connected to the router, right?
If so, check the Network settings to see if they are alright? Have you properly configured Static/Dynamic IP? DNS servers? Also, can you ping the router using
```
ping <router IP address>
```

---

### Post by theta on 2006-10-25
I am pretty sure I have it all set up right. I tried all the settings that Windows XP had showed, and other set-ups. I think it should be DHCP, because that's how it was on Windows, but that gives less information than when I use static IP.
Anyways, when I ping my router's address (or any address for that matter), I get
"connect: network is unreachable"

---

### Post by adwait on 2006-10-25
So the computer cant see the router and hence no internet. Gotta be a problem with your network settings. It was DHCP on windows, so when you configured Ubuntu with a Static IP, did you configure the router accordingly? If not, you either need to change the router to static IP or change the computer to DHCP.

---

### Post by theta on 2006-10-25
I'm not sure how to change the router to Static or the computer to DHCP, but I would love to change the computer to DHCP, if that's an option... Or if worse come to worse, the other, if I simply knew how.

---

### Post by theta on 2006-10-25
Thank you for responding so quickly, adwait, but unfortunately it's very late and I'm exhausted- to the point of almost falling asleep at my keyboard. I have highest hopes for fixing this problem soon though; thank you.

---

### Post by adwait on 2006-10-25
Hehe, its no problem...let's hope I (or anyone else) is able to help you on this :)

For changing the computer to DHCP, I am using Kubuntu so can't really tell you the exact place where you'll find it. But it should be there somewhere in the menus....find Network Settings and in there somewhere you should find it.

---

### Post by theta on 2006-10-25
Well, I Network Settings are under System->Administration->Networking.
 However, I didn't find anything about switching the computer to DHCP. I have four tabs, "Connections," "General," "DNS," and "Hosts."
 Under Connections I have "Ethernet connection," which I can choose either static IP or DHCP connection, and "Modem connection."
 Under general, is two text boxes, "Host name," and "Domain Server." I never actually understood what those two are for. Sorry, yes, I am a pretty unknowledgeable when it comes to some of these in-depth things like networking.
 Under DNS is DNS Servers and Search Domains. I put the DNS under DNS servers, "192.168.1.254"
 Under Hosts is a bunch of different things that I don't really understand, but each value has an IP address and an Alias. There are things such as "ff00::0, ip6-mccastprefix" and "fe00::0, ip6-localnet"

---

### Post by theta on 2006-10-25
Is it supposed to have those strange values? On a side note, some of the commands I've tried that I found on the forums have given me access denied, which is strange. Everything should be set up right, I thought...

---

### Post by theta on 2006-10-25
Whoops, I found out I needed to be doing everything from the root terminal. I'm sorry. Anyways, now I'm getting "No DHCPOFFERs recieved.
No working leases in persistent database - Sleeping."
Oh, and I guess you were referring to setting eth0 to DHCP instead of Static IP, wich I did.

---

### Post by adwait on 2006-10-25
Well, since it says no DHCP Offers recieved, it means that there is no active DHCP server accessible. That either means that the router is not on DHCP, or that there is some physical problem wtih the connection between the router and your computer. If you have access to the settings of the router, check its settings. Also, check the settings of the other computers on the net, whether they are on DHCP, their DNS servers etc. The "strange" values you mentioned are alright. On the other hand, is the DNS address 192.168.1.254 right? Is that the IP of the router?

---

### Post by theta on 2006-10-26
Yes, it is. Though after more looking around, I think it might be the network drivers... Forcedeth or whatever. I looked around for other people with the same router and provider, and one was having problems with forcedeth. It seemed to be running fine, I think, but it seemed like the only reasonable explanation...

---

### Post by navlelo on 2006-10-26
I think I have the same problem as Theta.

I just installed Ubuntu and am a Linux newbie, but quite experienced with Windows. I have fiddled around with different network solutions and is fairly confident about it, but not an expert.

When running Ubuntu from the CD, Internet works fine with its default DHCP setting. After installing Ubuntu (clean system, automatic install, no dual boot) the DHCP settings are exactly the same, but I can't connect to the network. I can't ping the router or my Windows computer, and the Windows computer can't ping the Ubuntu. When booting from the CD again, everything works just fine. I am actually doing that right now.

IMPORTANT EXTRA INFORMATION: I noticed that the Internet connection actually works for a short while. When booting the desktop, the automatic update system says there are updates available, but by the time I click on the install button, the connection is gone. I have also tried to load a web page immidiately after logon, and I can do that for just a few seconds. The automatic setup have also found the right DNS information of my ISP.

I thought there might be some sort of firewall problem with the router. I use static IP adresses on my LAN (DHCP is still on) and changed the network configuration to the same that my previous Windows installation used. There is no change: The network works for a few seconds.

I am very puzzled.

---

### Post by navlelo on 2006-10-26
One more piece of information:
If I unplug and replug the ethernet cable, the computer comes online again for a few seconds, maybe as much as a minute. Surfing the net is possible, but it's ](*,)

---

### Post by navlelo on 2006-10-29
I don't know what caused my problems, but I fixed it by installing updates. The 45 seconds window of internet connection was enough to get the most important updates. 

That was Ubuntu 6.06. I destroyed the window system while trying to install xgl/compiz, and ended up up doing a new and clean install with 6.10. I have no internet problems there. :)

It seems my problem was not the same as Theta's.

---

