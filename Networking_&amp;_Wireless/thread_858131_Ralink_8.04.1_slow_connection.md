---
title: "Ralink 8.04.1 slow connection"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by wigren on 2008-07-13
I've updated an older laptop to Hardy, and I'm having a wireless issue. With 7.10 my RaLink RT2500 wireless card worked fine. But after the upgrade I can get a top transfer speed of only 33 kB/s. It doesn't matter how close I am to either access point I've tried it on. Also, it doesn't matter if I'm transferring a file over the network, downloading a file from the Internet or just surfing. I'm back on Gutsy now (wireless is at correct speed), but I can do a quick upgrade if need be. Thank you.

---

### Post by ZeroXtreme on 2008-07-19
try: sudo iwconfig wlan0 rate 54M

---

### Post by cybrsaylr on 2008-07-19
> **ZeroXtreme said:**
> try: sudo iwconfig wlan0 rate 54M

Tried the above and got this:

Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; No such device.
tt@tt-laptop:~$ 

Pages take longer to load now that I got wireless running on my laptop.
When hardwired my laptop was faster. I was hoping that would speed things up but just got that error message instead.

---

### Post by ibutho on 2008-07-19
Check what network interfaces you have by running
```
ifconfig -a
```
If you find the one that corresponds to your ralink card, then run the iwconfig command, replacing wlan0 with the actual ralink interface name.

---

### Post by merdenoms on 2008-08-01
I have the exact the same problem. I have a Ralink wireless adapter (using rt73usb driver by default) but it downloads maximum 50kb/s..its full speed is 110kb/s in windows xp and vista. Somehow it works full speed in other distros (like Arch Linux, Pardus etc.) What should i do? Does Ndiswrapper works? To install windows drivers with ndiswrapper how can i remove the kernel drivers on ubuntu?

P.S: This is my iwconfig output..everything looks OK

```
dusk@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ZyXEL"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:CF:9F:97:B8   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=73/100  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by mabbee on 2008-09-07
I'm having similar problems. I am using the rt73usb driver with an 802.11b/g internal card in my laptop. In Ubuntu 8.04 it seems to be restricted to just operating in b mode. I only noticed this beacuse on upgrading to 8.04 my netork speed dropped , and BBC iPlayer is now unusable. If I switch my router to 'just G' mode, I am not able to link up -- I am only able to get a connection to B or B/G networks. This seems to suggest that the card is only operating in B mode.

My iwconfig output looks fine: the mode is set to Managed and the rate to 54M, but its just so slow!

I also have problems with Ubuntu 7.10 -- although here the card operates blindingly fast, I get occasional loss of network (and even, sometimes, complete disappearance of the wireless interface) that can only be fixed with a reboot.

Worryingly, the problems do not seem to be resolved in the Aplha4 of Ubuntu 8.10 (which uses a 2.6.27 kernel)

Anyone any ideas? What about using the ralink drivers?

---

