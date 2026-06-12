---
title: "Linksys Not Recognized"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by j0sh3rs on 2005-05-27
I'm new to linux, and I'm using Kubuntu, first time ever.

I'm currently plugged into my Linksys 802.11b Wireless router because I cannot get my linksys WMP55AG card to work.  As far as I know, the entire thing just isn't being recognized.  It says my router is out of range, when it's right above my desktop.

I do have a 128-bit encryption key, and have not attempted to disable it yet do to the other members in my household who use the network, and the area I live in.

Any suggestions as to how I can get this to work?  I've got someone who's a little more versed in linux than I am, but unfortunately he cannot figure it out either.

Thanks for the help,

-The Ultimate Linux n00b

Edit: I know the card itself is being recognized, as it's listed as ath0, but it won't connect to my "linksys" ESSID.

---

### Post by f.prisson on 2005-05-28
Please post the output of ```
iwconfig
``` for seeing what's already configured. What steps did you take for configuration until right now?

---

### Post by j0sh3rs on 2005-05-28
[QUOTE=f.prisson]Please post the output of ```
iwconfig
``` for seeing what's already configured. What steps did you take for configuration until right now?[/QUOTE]
 lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



Well, I first tried to use the auto config that the OS installer should've done, but to no avail.  Then I tried to manually enter the essid and key, and assign it to the ath0 port, but that still didn't work.  I'm trying to get onto Linksys' site to download the A+G Drivers.

---

### Post by f.prisson on 2005-05-28
Try this commands:```
iwconfig ath0 key xxxxxxxxxxxxxxxxxxxxxxxxxx
``` ```
iwconfig ath0 essid <essid>
``` ```
ifconfig ath0 <IP> up
``` ```
route add default gw <IP AP>
``` If your accesspoint isn't too far away or there are other problems (like MAC adress filtering or something like that) you should have a connection now.

---

### Post by j0sh3rs on 2005-05-29
I get the following messages when I attempt to enter those commands into the console...

j0sh3rs@atari1:~$ iwconfig ath0 key **********************
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device aht0 ; Operation not permitted.
j0sh3rs@atari1:~$ iwconfig ath0 essid linksys
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; Operation not permitted.
j0sh3rs@atari1:~$ ifconfig ath0 192.168.254.106 up
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
j0sh3rs@atari1:~$ route add default gw 192.168.254.100
SIOCADDRT: Operation not permitted

---

### Post by f.prisson on 2005-05-31
You have to do the commands as root or with sudo.

---

