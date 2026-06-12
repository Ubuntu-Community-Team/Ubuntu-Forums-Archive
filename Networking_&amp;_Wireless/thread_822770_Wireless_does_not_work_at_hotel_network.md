---
title: "Wireless does not work at hotel network"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by HHB002 on 2008-06-08
I am fairly new to Linux and Ubuntu. 
I have made a fresh install og Hardy Heron when it came out. It has been updated regularly at the latest on june 3rd as I have not been able to connect since that date.
At home I connect to a linksys router without any problems.

For now I am on a hotel in Norway where I have to be for some time. They have an unencrypted network where you are getting a username and a password.

I can not log on to the network in fact I do not even get the log in box. The network manager is able to connect to the network but neither firefox nor the update manager can acces the internet.

I have a pcmcia Belkin wireless G notebook card model F5D7010
It is in my 5 year old Medion computer.

As said it has been working flawlessly at home with WPA2 encryption.

The IWCONFIG looks as follows.
lo       no wireless extensions
eth0     no wireless extensions
wmaster0 no wireless extensions
wlan0 IEEE 802.11g ESSID:"bhgjest"
      Mode:Managed Frequency:2.412 GHz 
      Access point: 00:13:49:33:DB:6E
      Bit rate=1 Mb/s Tx-Power=27 dBm
      Retry min limit:7 RTS thr:off Fragment thr=2346 B
      Link Quality=59/100 Signal level=-58 dBm
      Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
      Tx excessiveretries:0 Invalid misc:0 Missed beacon:0

The IFCONFIG looks as follows.
wlan0 inet addr:192.168.17.206
      bcast:192.168.17.255
      mask:255.255.255.0
      up broadcast running multicast mtu:1500 metric:1
      RX packets:866
      TX packets:156
      The rest of the figures for tx and rx are 0
      txqueuelen:1000
      rx bytes:62962 tx bytes:11700

I have disbled IPV6
In network settings DNS servers are 213.184.200.1 and 213.184.200.2 listed.

The reason I have cut a corner at ifconfig is that I have to write it all on a borrowed (windows) computer situated next to my own.

I cincerely hope that you can help.

Brgds
HH

---

### Post by chili555 on 2008-06-08
I've had this difficulty a few times at hotels. Have you tried entering the IP address of the log-in page directly?

Whe you open Firefox, it tries to go to your home page, [http://www.google.com](http://www.google.com), for example. The hotel's system wants to redirect to a login page to ask for your user name and password, [http://login.hotel.com](http://login.hotel.com), for example. Looking at the address for the login on the borrowed XP machine, can you type the address in directly and get to the login?

---

### Post by HHB002 on 2008-06-09
Hello.
I have tried to put in the ip adress which I have to use in windows: [http://192.168.17.5](http://192.168.17.5) but get the failed to connect screen in firefox. It only has to be done with a new password once a week.
Thanks for the suggestion, anything else?

---

### Post by chili555 on 2008-06-09
Once, and this may have been a lucky coincidence, I was able to get to the hotel log-in page using *lynx,* a text-based web browser. I think it is installed, by default. Please try opening a terminal and do:```
lynx http://192.168.17.5/
```You navigate around lynx with the arrow keys, Tab and Enter. 

Once I completed the log-in process, I could go back to Firefox, instant message, etc.

---

### Post by HHB002 on 2008-06-10
I have now managed to get the Lynx browser, as it was not installed.
I borrowed a wired connection and updated the system to june 9th. Everything worked well at this connection. I installed the browser and went back to the hotel.
And sorry to say but it did not work.

Never the less which adress or IP address I type I get the message: Host server unreachable.

Further suggestions are very much appreciated.

---

### Post by HHB002 on 2008-06-14
Unfortunate it seem like I have to go back to Win XP as I can not get connected and witrhout internet, not much use of linux.
Will make a dual boot box and check if I can log in with windows and then change to Ubuntu and see if it can log in. 

Was just getting used to Linux:(

---

### Post by Payteer on 2008-06-16
This has happened to me a couple of times now as well.  It works perfectly fine at home, but not in any hotspot, can anyone work out why?

---

