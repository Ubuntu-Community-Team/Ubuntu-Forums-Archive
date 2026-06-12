---
title: "wvdial and /etc/ppp options that helped me"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by mfdc1969 on 2007-10-15
As a noob I have spent many hours pouring through these forums and those of LinuxQuestions.org gleaning bits of useful info to enable my modem and dial-up connection. I am located in Victoria, BC Canada and my primary internet access is via ADSL with the ISP Telus  but I rely on dial-up when travelling.  I present the options I discovered in the hopes they may help others:

From reading the forums I decided to add to my wvdial.conf file:

```
sudo gedit /etc/wvdial.conf
```

these two options:
```

Carrier Check = no
Stupid Mode = yes
```

From the Ubuntu DialupModemHowto: Configure Connection to Internet Service Provider (see the bottom of the page) [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) where you will see:

4. [Alternative Way 1 (using wvdialconf & wvdial)]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9")

I edited options for pppd:

```
sudo gedit /etc/ppp/options
```

and found these three options helpful:

1. Comment out lcp-echo-intervals 30
2. Comment out lcp-echo-failure4
3. Add these few lines at the bottom:

```
# Added by me after reading this web page
# https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9
# If you connect successfully but your Internet applications do not function
# (eg. web pages do not load in Firefox), you might need to add 
# replacedefaultroute as a new line in the pppd option file.
replacedefaultroute

```

These 5 changes helped me to connect and I am grateful to all of you who post and reply - your participation in our community makes Ubuntu a success! 

Thank you everybody!

---

