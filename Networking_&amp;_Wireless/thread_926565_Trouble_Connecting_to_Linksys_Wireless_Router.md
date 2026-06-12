---
title: "Trouble Connecting to Linksys Wireless Router"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by ty10 on 2008-09-22
Greetings. I am having trouble connecting to my Linksys BEFW1154 wireless router. I cannot for the life of me connect to my network.

The router works, as demonstrated by my roommates' ability to connect to the network. He's running Ubuntu 8.04, as am I, so I don't believe the problem is inherent in Ubuntu. Additionally, I am able to connect to other wireless networks without any problems. I am able to access the router when connected with an ethernet cable. We have reset the router several times in an effort to figure out what's going wrong here, but always without success.

My computer is a Lenovo Thinkpad T60. My wireless adapter is an Intel PRO/Wireless 3945ABG Network Connection, and it appears to be functioning correctly. 

When I try to log on to my wireless network, I am prompted for the password, which I correctly enter. It then gets hung up "attempting to join the wireless network", occasionally reprompting me to enter the password, but nothing ever happens. The little swirling connecting thing just spins forever. 

Any idea what's going on? Any help will be vastly appreciated.

---

### Post by ty10 on 2008-09-22
Here's what iwconfig shows when I try to connect. Maybe it'll help:


tylo@Mainframe:~$ lspci | grep -i wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
tylo@Mainframe:~$ 
tylo@Mainframe:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"El Grobe"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:F5:1E:59   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Thanks again.

---

### Post by superprash2003 on 2008-09-22
ensure you are entering the correct key type.. wep or wpa .. 64 bit or 128 bit...

---

### Post by ty10 on 2008-09-22
We've reset the router multiple times, set it up with different passwords and password formats, even without any wireless security whatsoever. Didn't seem to help.

---

### Post by Dougie187 on 2008-09-22
You don't have a wireless mac filter or anything else?

---

### Post by ty10 on 2008-09-22
The MAC filter is not enabled. I'm starting to believe that the problem is with my computer.

---

### Post by ty10 on 2008-09-23
Update: Tried reinstalling Ubuntu. Figured maybe I messed something up at some point in the last four months that resulted in my current predicament. No progress. Thanks for all your help thus far, though.

---

### Post by Dougie187 on 2008-09-25
What does this give you?
```
lshw -class network
```

---

