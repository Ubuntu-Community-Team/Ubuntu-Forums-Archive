---
title: "wireless trouble"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by davbeck on 2007-01-26
I am having trouble with my wireless. Before I start describeing the problem let me say that it has worked before. I have had to reformat my harddrive a few times and every time I have the same problem with the same symptoms and it takes me forever to fix. Someone guided me through fixing it but I need to know what I am doing. I have been using Ubuntu for about six months and am limited in my knowledge but am excited to learn more technical stuff.

I have an IBM thinkpad a21m and a wireless bus card. the wireless card says compusa on it but in all the technical data and even the driver refers to it as realtek. I have tried other wireless cards with even less luck but I have gotten this to work somehow. the router is a Linksys and the network is set up using windows computers. WEP encryption is enabled.

on my card only the activity light blinks and not the link light. It does not appear in the network connection list at the top-left of the screen. It does however appear in the Network manager. It claims to not be configured yet when I click on it and enable it, it doesn't have any available wireless networks. I know that a windows pc can get a pretty good signal from here.

---

### Post by slybob on 2007-01-26
Can you please run iwconfig and post the result here?

Cheers

Slyb

---

### Post by davbeck on 2007-01-26
here you go

> david@IBM-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.447 GHz  
          Access Point: Not-Associated   Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@IBM-laptop:~$ 

---

### Post by slybob on 2007-01-26
Grand. I take it you have tested for the presence of your wireless network where you are.

 iwconfig wlan0 essid any
to use any ssid it can find 

then open up the device in network-manager

You should hopefully have the available wireless networks listed there..

---

### Post by davbeck on 2007-01-26
O.K. so you said to run command "iwconfig wlan0 essid any". when I did this I got
> david@IBM-laptop:~$ iwconfig wlan0 essid any
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
david@IBM-laptop:~$

and the same symptoms

---

### Post by davbeck on 2007-01-26
OK I saw a wiki that helped me. I now have my wireless working for everything except wep encription as long as I disable it it works but not with it

---

### Post by slybob on 2007-01-26
Remember if you want to change system setting you have to be a super user.

sudo iwconfig wlan0 essid any

sorry, should have told you this.

---

### Post by can1cel on 2007-01-26
> **davbeck said:**
> OK I saw a wiki that helped me. I now have my wireless working for everything except wep encription as long as I disable it it works but not with it
tell where you found the solution i have the exact problem with my wpc54g 1.2.

---

### Post by Thebear on 2007-01-26
Yes davbeck, 
   please post the solution, I have tried a number of Howto's with my setup which is a wmp54g linksys with an rt61 chipset. 

It all sets up and everything looks right but it will not connect and my system freezes a lot when it is set up. 

The bear

---

### Post by davbeck on 2007-01-26
the solution I found was on the wiki [here]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#preview")

basically I typed the ssid into the network manager but based on what I have tried I think that typing this command

sudo iwconfig wlan0 essid any
where wlan0 is your wireless network card

will work better especially if you plan to take a laptop to other places.

if you are using wep encryption type the command

sudo iwconfig wlan0 key FFFFFFFFFF
where FFFFFFFFFF is the key

alternatively you could type it into the network manager but I have less luck with this.

the last step is to simply select wlan0 in the network list.

---

