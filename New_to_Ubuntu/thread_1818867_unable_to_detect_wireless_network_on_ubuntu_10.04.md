---
title: "unable to detect wireless network on ubuntu 10.04"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by neouser on 2011-08-05
Hello,

I just installed ubuntu 10.04 on my dell mini 9 and now my computer doesn`t detect wireless networks. 

It is like a vague dejavu: the same happened when I installed an earlier ubuntu version a few years ago (only last time I had wired internet). Unfortunately I don`t have a wired internet connection, so it would be good to find a solution by using the internet on another computer. 

From what I understood on the web, for many it helps to re-install "bcmwl" packages. So far I downloaded "bcmwl-kernel-source" and "bcmwl-modaliases" on a flash-drive (usb-stick) and tried to run these files on my computer. I received a message stating that these packages are already available, and tried to re-instal them. After restarting it was still not working. 

When checking the hardware drivers on my computer I receive an error message "*Downloading package indexes failed, please check your network status. Most drivers will not be available*". In fact, no drivers are found. 

As far as I know the dell mini 9 has a Broadcom WLAN 802.11b/g. I didn't find a driver which I could try to download. 

Would be great to receive some help

Thanks in advance!

---

### Post by bodhi.zazen on 2011-08-05
You will need to work through this guide:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

You will likely need to use a wired connection until you get your wireless working.

---

### Post by computerandu on 2011-08-05
What is the output of sudo rfkill list all?

---

### Post by neouser on 2011-08-05
Thank you for the quick reaction!

Since it won't be that easy for me to find a wired connection soon, I would be happy to hear if you or someone else knows another solution by downloading a package or driver with another computer.

---

### Post by neouser on 2011-08-05
> **computerandu said:**
> What is the output of sudo rfkill list all?

Unfortunately I don't know how I can find this information.

---

### Post by bodhi.zazen on 2011-08-05
> **neouser said:**
> Thank you for the quick reaction!

Since it won't be that easy for me to find a wired connection soon, I would be happy to hear if you or someone else knows another solution by downloading a package or driver with another computer.

Hard to give you any advice before you are able to give us some more technical information outlined in the wiki page you gave us.

Open a terminal and enter the relevant commands and show us the output.

If the kernel did not recognize your wireless card, you are not going to fix it without internet access.

---

### Post by neouser on 2011-08-05
Following your link ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lshw](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lshw)) the interface shows the following information: 



**-network DISABLED*
  *       description: Wireless interface*
  *       physical id: 1*
  *       logical name: wlan0*
  *       serial: 00:1d:19:fd:12:de*
  *       capabilities: ethernet physical wireless*
  *       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg*

**
If I understand correctly, there is a driver but it does not show "bus info".

---

### Post by bodhi.zazen on 2011-08-05
Looks like your wireless card is working, what do you mean by you can not detect wireless networks ? What does network manager show you ?

---

### Post by neouser on 2011-08-05
> **computerandu said:**
> What is the output of sudo rfkill list all?


rfkill list:

 *1: compal-wifi: Wireless LAN*
  *         Soft blocked: no*
  *         Hard blocked: no*
  *2: compal-bluetooth: Bluetooth*
  *         Soft blocked: no*
  *         Hard blocked: no*
  *3: phy0: Wireless LAN*
  *         Soft blocked: no*
  *         Hard blocked: no*
  *4: hci0: Bluetooth*
  *         Soft blocked: no*
  *         Hard blocked: no*

---

### Post by bodhi.zazen on 2011-08-05
Keep following the wiki ...

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)

All the commands and procedures are outlined on that page ^^

---

### Post by neouser on 2011-08-05
In case someone can do something with this info:

iwconfig

 *[FONT=Arial]lo        no wireless extensions.[/FONT]*
*[FONT=Arial]  [/FONT]*  *[FONT=Arial] [/FONT]*
*[FONT=Arial]  [/FONT]**[FONT=Arial] [/FONT]*
*[FONT=Arial]  [/FONT]**[FONT=Arial]eth0      no wireless extensions.[/FONT]*
*[FONT=Arial]  [/FONT]*  *[FONT=Arial] [/FONT]*
*[FONT=Arial]  [/FONT]**[FONT=Arial] [/FONT]*
*[FONT=Arial]  [/FONT]**[FONT=Arial]wlan0     IEEE 802.11bg  ESSID:off/any  [/FONT]*
*[FONT=Arial]  [/FONT]*  *[FONT=Arial]          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   [/FONT]*
*[FONT=Arial]  [/FONT]*  *[FONT=Arial]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]*
*[FONT=Arial]  [/FONT]*  *[FONT=Arial]          Power Management:off[/FONT]*
[I]
[FONT=Arial][/FONT][/I]
[FONT=Arial]*pan0     no wireless extensions*
[/FONT]
[FONT=Arial]  [/FONT]  [FONT=Arial]          
[/FONT]


To get back to your earlier question.
With "no network detection" I mean that my computer does not identify an existing wireless network. My network manager does not list any wireless networks.


It seems that I will have to give up for now and find a wired connection in order to do more trials.
[FONT=Arial][/FONT][FONT=&quot][/FONT]

---

### Post by bodhi.zazen on 2011-08-05
Your wireless card is working, not sure why you are not seeing any wireless networks.

Can you post the output of

```
sudo iwlist wlan0 scan
```

By the way , these commands are explained in the page I gave you.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#iwconfig](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#iwconfig)

---

### Post by neouser on 2011-08-05
It said 

*wlan0 Interface doesn't support scanning: Network is down*

---

### Post by bodhi.zazen on 2011-08-05
Now you will need to identify your hardware and install the proper driver. It may or may not work, but will certainly need an internet connection.

show the output to

```
sudo lshw -C network
```

---

### Post by neouser on 2011-08-05
Thanks again!

I will need to try and find a wired connection this weekend.

---

### Post by neouser on 2011-08-06
Hello again,

I managed to solve the problem!

Today I was able to get a wired internet connection. In package manager I tried to start checking the available not installed "bcmwl" packages. There was a "bcmwl-kernel-source" which I selected. Additional packages were automatically suggested. I installed everything, restarted and everything is fine. Wireless networks are detected again.

I guess for this issue you** need wired connection**. To manually download packages on another computer and transfer these on your problematic computer is too complicated.

Thanks again for all the inputs!

---

