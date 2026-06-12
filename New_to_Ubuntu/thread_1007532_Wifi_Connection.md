---
title: "Wifi Connection"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by neigun on 2008-12-10
Hi Guys

just when I thought everything was OK my wifi connection appears to be playing up.

Whilst running Ubuntu 8.10 from my dvd drive I could connect to the net and still can. But if I use the installed version I get nowhere:-(

Initially after installing Ubuntu to my hard drive everything was OK. However, after downloading a couple of things from the Ubuntu downloader, like a new version of the Linux kernel, and installing them- the connection became erratic. The indicator states I'm connected but no joy.

Any advice would be welcome.

TTFN Neil

---

### Post by Michael.Godawski on 2008-12-10
First some input please :p
run in terminal and post the output here
```
sudo lshw -C network
iwconfig
```

---

### Post by neigun on 2008-12-10
I've tried the command line and get prompted for my sudo password- which if its the same as my admin password- I can't type it in.

I've tried the num lock etc.

I've no experience of using command lines so please excuse my ignorance!

Neil

---

### Post by capn_hector on 2008-12-10
> **neigun said:**
> I've tried the command line and get prompted for my sudo password- which if its the same as my admin password- I can't type it in.

I've tried the num lock etc.

I've no experience of using command lines so please excuse my ignorance!

Neil

the sudo password is the password for the account your on, sudo is a system where you no longer have to log on as the root user to administrate your system.  just run sudo <commandgoeshere> and when it asks for your password you enter your user password.

---

### Post by Michael.Godawski on 2008-12-10
The password won't be displayed. Just type it in and hit enter.

---

### Post by igknighted on 2008-12-10
Sounds like an issue with the atheros driver not being loaded.  It's a known bug... see the release notes for 8.10 on ubuntu.com, the fix is listed there.

---

### Post by neigun on 2008-12-10
I've tested the network connection using Network Tools and it seems to be working OK. But Firefox wont connect and the Download Manager doesn't;-)

Neil

---

### Post by mjheagle8 on 2008-12-10
can you connect to the internet with any other programs? i.e. another browser, email client, etc?

---

### Post by neigun on 2008-12-13
> **mjheagle8 said:**
> can you connect to the internet with any other programs? i.e. another browser, email client, etc?

Nothing connects to the net, but the indicator on the taskbar shows a live connection as does the green light next to the user name. It's weird as out of the blue Firefox and the download manager connected, after days of not connecting to the net, and then just as mysteriously deconnected!

Neil

---

### Post by mjheagle8 on 2008-12-13
Do you have a firewall that could be blocking your connection to the internet?

---

### Post by neigun on 2008-12-15
> **Michael.Godawski said:**
> First some input please :p
run in terminal and post the output here
```
sudo lshw -C network
iwconfig
```

Tried the command line and received the following:

lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:"virgin"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:D4:89:20   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality=52/100  Signal level:-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions

I think my Netgear dongle is causing the problem combined with a weak signal. Firefox, at least at this stage, appears not be as forgiving as IE8.

Neil

---

