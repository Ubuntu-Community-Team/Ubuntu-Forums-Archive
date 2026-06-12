---
title: "Wireless Connection Trouble"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by Jabyvogux on 2011-03-18
Hello, let me preface this by stating that I am an _absolute beginner_.

I downloaded Ubuntu 10.10 onto my Dell Vostro 1500 laptop two days ago and finally have time to try and get connected to my wireless Internet but, alas, it is not working. I right clicked the Network Manager icon and its said that I am in need of a firmware upgrade. I am not sure what wireless card I have. I attempted to use the code in my terminal that was suggested in the sticky thread "suggestions on how to get your support questions answered as quickly as possible" but I did not get any information out of that. I downloaded Ubuntu via Wubi and still have the original operating system (windows xp) on the computer.

My questions are these:
How can I figure out what wireless card I have?
How do I perform the firmware upgrade?
Are there any additional steps beyond upgrading that I will need to do before attepting to connect to the wireless network (assuming no other problems at this time)?

I did attempt a search on the forums but the information I found I never quite understood everything that the relevant threads posted. If you know of a thread that already answered these questions please link and I'll try going off that thread.

Thanks in advance!

---

### Post by 5149.5 on 2011-03-18
Enter iwconfig in the terminal and paste the output in a post.

---

### Post by Jabyvogux on 2011-03-18
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by Jabyvogux on 2011-03-18
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by 5149.5 on 2011-03-18
OK. Enter lspci and look down towards the bottom for information identifying your wireless card and post and paste that.

---

### Post by Jabyvogux on 2011-03-18
Nothing on there that specifically said wireless. These are the only thing that looked internet related:

```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```or

```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```I can post the full results if neither are what you need.

---

### Post by 5149.5 on 2011-03-18
Now you know what kind of card you have and can start looking for a driver:            Broadcom Corporation BCM4311

---

### Post by wep940 on 2011-03-18
If you can, temporarily run and hard-wire between your PC and the router, then open a terminal window and do:
 
sudo apt-get update
 
When that finishes, open up system/administration/other drivers (or some such name - I'm on Windows right now) and see if there is a driver listed there for your wireless - if so, enable it.
 
Disconnect the hard-wire cable.
 
Right-click on the network manager icon and see if "Enable Wireless" is checked - if not, check it so it is enabled.
 
Left-click on the network manager icon and see if wireless networks show now.

---

### Post by 5149.5 on 2011-03-18
I found a package you can install that will contain a driver for your card: bcmwl-kernel-source.

---

### Post by Jabyvogux on 2011-03-18
Ok. I googled that and got this website:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
I'm fairly certain that this is where I need to be. What I'm not sure of is if I need the 32 or 64 bit driver. How would I figure that out?

---

### Post by 5149.5 on 2011-03-18
If you have access to a wired connection, WEP940's method should work fine.

---

### Post by wep940 on 2011-03-18
If you just downloaded "normal" Ubuntu, it is 32-bit.  You would have specifically had to "ask" for the 64-bit at the download.  If at all possible, try what I suggested for hard-wire first - things have changed a lot in terms of driver support and there are restricted drivers available now for that series of Broadcom cards (43xx).  As a result, there are a LOT of outdated threads on the net for installing a driver for this series.  You really shouldn't even need the kernel source module.  If you hard-wire and do the update, you should get a B43 or SSA driver show in the additional drivers that you can use.

---

### Post by Jabyvogux on 2011-03-19
Sorry did not notice all of the replies in between and after my last reply. should have hit refresh first I suppose. I tried entering 'sudo apt-get update' into the terminal and it asked me for the password. I assume its referring to the password I've been using for everything else. When i try to enter the password, no characters appear on the terminal. I've hit enter and it just keeps asking for a password, without letting me type any characters. Needless to say I find this odd.

---

### Post by 5149.5 on 2011-03-19
You won't see anything echoed on the terminal when you are inputting your sudo password.

---

### Post by Jabyvogux on 2011-03-19
I thought that originally but when my password failed twice I thought something might be wrong. I must have just typed it wrong twice however because I just tried it again and typed both slowly and deliberately and it worked. Finished following wep940's suggestion and everything worked smashingly. I'm posting this now via my wireless network connection. Thank you both very much. If I could share some of my jello cups with you two, I would.

---

### Post by wep940 on 2011-03-19
Glad it worked for you!

---

