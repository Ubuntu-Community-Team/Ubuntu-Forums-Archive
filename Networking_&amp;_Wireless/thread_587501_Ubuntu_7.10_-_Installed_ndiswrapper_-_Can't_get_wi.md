---
title: "Ubuntu 7.10 - Installed ndiswrapper - Can't get wireless card working"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by kingleer on 2007-10-22
Hey, 

I just finished installing ubuntu 7.10 on my laptop (I love it thus far). I'm a linux noob, but this isn't the first time I've used ubuntu, and I've been using it as my main OS for two years. So I tried to get my wireless card working, which is the first thing I do on every install. I installed ndiswrapper using the synaptic package manager and the install dvd. 

Next, I tried installing the windows driver for my wireless card using ndiswrapper. This isn't the first time I have done this, and I was able to do it in ubuntu 7.04 and before with no problem. 

So, I take the driver I've always used and try installing it. 



Attempt to install driver



sudo ndiswrapper -i ~/PRISMA00.inf



this will try to install the driver from my home directory.



 Check installed driver



sudo ndiswrapper -l


gives 

prisma00  :  driver installed
              device (1260:3886) present (alternate driver: prism54) 


Next, Loading ndiswrapper



sudo modprobe ndiswrapper


Than I go to check if my wireless card is picking up anything 

iwconfig 

gives

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      NOT READY!  ESSID:"kinglear"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Any idea on what I'm doing wrong/ can someone help me out? Thanks in advance.

---

### Post by kevdog on 2007-10-22
First make sure that you have removed the prism54 driver

sudo modprobe -r prism54

Then I would reload the ndiswrapper module
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

Then you physically need to bring the interface up

sudo ifup eth0

Then see what you get with 
sudo iwlist scan

If you want to make sure that the prism54 module is not loaded at boot everytime
echo "blacklist prism54" | sudo tee -a /etc/modules

---

### Post by kingleer on 2007-10-22
Thanks. 

Okay, I did as you said and blacklisted prism54. I think my wireless card itself is now up and running. 

see below 

kinglear@ubuntukinglear:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:4B:6B:71
                    ESSID:"Jung Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 02 - Address: 00:12:17:1A:5C:FA
                    ESSID:"kinglear"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1

kinglear@ubuntukinglear:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0





The network I'm trying to connect to is kinglear by the way. 

However, I'm unable to connect to the network itself even though I can detect it. 


I go to manual configuration for networking, in the network setting box I go to wireless connection,

Under ESSID, my network is visible. 

After turning my laptop on and off, I get 


kinglear@ubuntukinglear:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      NOT READY!  ESSID:"kinglear"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kinglear@ubuntukinglear:~$

---

### Post by kingleer on 2007-10-23
Figured out what was wrong. 

I added 

modprobe -r prism54
modprobe -r ndiswrapper
modprobe ndiswrapper
 
to /etc/rc.local. 

Everything works fine now thanks.

---

### Post by kevdog on 2007-10-23
I guess you could add those to rc.local, but I dont know if its necessary.  Did you add ndiswrapper to /etc/modules???

---

