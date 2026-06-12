---
title: "Connecting to the internet on UBUNTU"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by doublez08 on 2008-11-07
I just installed Ubuntu on my hard drive. I have a dual boot: Vista and Ubuntu. I have a wireless network set up in my home. 

When I switch to Ubuntu OS, it can't find the network. Can anyone walk me thru step by step so I can connect to the internet using UBUNTU? 

It also asks for a BSSID and MAC address. I have the MAC address, but not the BSSID, I don't know where to find it. 

If anyone can help me, I would appreciate it. 

Thanks.

---

### Post by doublez08 on 2008-11-07
I attempt to make a new wireless connection, and it asks for the following:

SSID
MODE
BSSID
MAC Address
MTU

I have the MAC address, but where do I find the other ones? 

Is it possible that I can't connect to the internet with UBUNTU? 

Again, I am a NOOB, and just installed UBUNTU as a dual boot with VISTA. 

Please help me, I would like to have this up and running. 

Thanks

---

### Post by MewRS on 2008-11-07
It's probably the same issue that we are trying to solve here: [http://ubuntuforums.org/showthread.php?t=973420](http://ubuntuforums.org/showthread.php?t=973420)

---

### Post by sved on 2008-11-08
I am through the stuff you are talking bout. let me try if i can be of any help to you guys.

- to connect to the wireless network, assuming that the wireless card and its driver are installed successfully, all that we need to do is create a profile for wireless access.

creating profile for wireless access:
1. click on system -> preferences -> network configuration.
 this will bring up the 'network connections' window.
2. click on wireless tab
3. click on add
 this will bring up the 'editing wireless connection' window.
4. with the defaults on, all that i did to get connected to my wireless router/modem is enter an valid SSID of your wireless ruoter.

it worked even without entering the other values. assuming that there is no password required to connect to the wireless network.

if you have a password protected your wireless network then you will have to click on wireless security tab and 

1. select security type from the drop down. should be the same as mentioned on the wireless router.
2. enter the password that you have mentioned on the wireless router for clients to join the wireless network. 

However later i have also entered the other values viz:
1. BSSID : I am not sure what this is, but i entered the MAC address of the LAN port on the wireless router.
2. MAC ADDRESS: this is the MAC address of your wireless card on the laptop or desktop.

Well I am not sure with what should be the values of hte BSSID and MAC ADDRESS. However the values that i tried did not affect/disrupt my wireless connection.

you may place the mouse pointer in the blank space against the BSSID and MAC ADDRESS, then it will show you the description.

---

