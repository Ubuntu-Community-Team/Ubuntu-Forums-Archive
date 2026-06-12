---
title: "Ubuntu//Cannot connect to the Internet"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by Geomancer on 2007-02-13
I cannot connect to the internet in Ubuntu. It has detected a dial-up and a wired internet service, but I don't have either. I have a D-Link AirPlus G DWL-G510 Wireless Internet Card, and my router is a D-Link WBR-2310 802.11g Wireless Router. I'm not extremely knowledgeable about wireless networks, but I got my Windows one to work. I don't know why  Ubuntu won't detect it.

---

### Post by Floppyjoe on 2007-02-13
This Url may be of help to you:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Floppyjoe

---

### Post by Geomancer on 2007-02-13
> **Floppyjoe said:**
> This Url may be of help to you:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Floppyjoe

I am confused by this page, do I open a terminal and type ipconfig?

---

### Post by Floppyjoe on 2007-02-13
Open a terminal and type:
```
iwconfig
```

---

### Post by Geomancer on 2007-02-13
This is what I got :

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

You can see that there is no wlan0. I'm getting a little worried here. What should I do?

EDIT: I think I need to install Ndiswrapper... can someone give me instructions on how to do this? Keep in mind I'm running an Ubuntu 6.10 Desktop CD. I haven't installed yet... still getting the feel of Ubuntu.

---

### Post by sumgi on 2007-02-14
Here are a couple links,

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

The first one is a good guide to look through when having wireless trouble, read it through step by step.

The second is pretty much everything else related to Wireless.

---

### Post by Geomancer on 2007-02-14
> **sumgi said:**
> Here are a couple links,

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

The first one is a good guide to look through when having wireless trouble, read it through step by step.

The second is pretty much everything else related to Wireless.

You seem happy to provide links, but no one will actually tell me the steps to get my internet working. I'm sorry, I just am so used to Windows and I really have no idea about terminals and commands and all that jazz. In windows, all you need to do is run the wireless setup program and *bam*. You have a wireless connection. I don't know why this is so hard for me to do on Ubuntu.. I guess I am an utter noob. I wish there was a program like the wireless setup from Windows.

I have typed in iwconfig and ifconfig. I've also done lwhs or whatever it is called. I see my card in lwhs, but what do I actually **do?** I mean, I see it, but seeing it in the terminal means nothing if I can't connect to the internet. I need something to **do.** Is Ubuntu really all about the terminal? Is there an OS that is harder to use than Windows? I never imagined that would happen. Once again, I am really sorry for the rant. Could someone tell me the next step to take, but without just linking to a Wiki about Wi-Fi? Thanks. :(

---

### Post by Floppyjoe on 2007-02-14
I don't know if you can save changes to your configuration when using a live cd. I am not very knowledgeable in that area. But if you can install ndiswrapper and install the needed ndiswrapper drivers using the cd maybe it will work. You need to become familiar with using the terminal to get things done in Linux. It's not as user freindly as the other OS is.

---

### Post by sumgi on 2007-02-14
> **Geomancer said:**
> You seem happy to provide links, but no one will actually tell me the steps to get my internet working. I'm sorry, I just am so used to Windows and I really have no idea about terminals and commands and all that jazz. In windows, all you need to do is run the wireless setup program and *bam*. You have a wireless connection. I don't know why this is so hard for me to do on Ubuntu.. I guess I am an utter noob. I wish there was a program like the wireless setup from Windows.

I have typed in iwconfig and ifconfig. I've also done lwhs or whatever it is called. I see my card in lwhs, but what do I actually **do?** I mean, I see it, but seeing it in the terminal means nothing if I can't connect to the internet. I need something to **do.** Is Ubuntu really all about the terminal? Is there an OS that is harder to use than Windows? I never imagined that would happen. Once again, I am really sorry for the rant. Could someone tell me the next step to take, but without just linking to a Wiki about Wi-Fi? Thanks. :(

Well I can understand your frustration, I just recently installed ubuntu as a dual boot on my laptop on Sunday and it took me about a day to figure out what I was doing wrong. If I had the link above I think I would have been done a lot sooner. 

I think most people give links on how to solve the issue yourself because most people follow the teach a person to fish routine though they would rather just give them a manual. 

Let me ask you, have you configured your wireless under System ..> Administration ..> Networking ? It's kind of like the start menu on Windows except this is on the top of the screen. It will ask you for your password and then it should bring up the Networking interface. If you see a Wireless Connection entry under the Connection tab then you may have a working driver and just need to activate. Select Wireless and click on the Properties button to the right. Check Enable this connection and fill in the appropriate information below such as SSID(Broadcast name of router) and password if there is any encryption. When done click ok and the connection should become active.

If you have done this or this does not activate your connection then please post output from the following.

[LIST]
[*]sudo lshw -businfo
[*]lspci -v
[*]sudo lsmod
[*]sudo iwconfig
[*]sudo ifconfig
[/LIST]

---

