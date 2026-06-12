---
title: "How to activate a script on network up"
date: 2016-06-14
forum: Networking &amp; Wireless
---

### Post by jamarsh123 on 2016-06-14
I want a script that mounts shares when connected to WiFi. To that end, I found this excellent article on the subject called: OnNetworkConnectionRunScript

[https://wiki.ubuntu.com/OnNetworkConnectionRunScript]("https://wiki.ubuntu.com/OnNetworkConnectionRunScript") 

I followed the instructions and placed my script in the following location: /etc/network/if-up.d/ . There is also mention of editing the following configuration file:  /etc/network/interfaces . It's not clear to me what info needs to be entered into this file.  Whatever I've tried so far, the script is not activated when I connect to a WiFi. I'm sure this is a simple glitch.

Here is the output of iwconfig:
```

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:"ICM83605"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: FC:8F:C4:08:E7:3E   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

Anyone have some thoughts on how to get this working?

---

