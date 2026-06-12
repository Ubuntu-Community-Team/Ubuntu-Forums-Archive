---
title: "Can't find any network using intel wireless 3945"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by ahlt on 2007-09-02
I've read tons of threads here on the forum related to the Intel pro wireless 3945agb device, but I just can't find the solution for my problem.

My card is recognized, but when I try to search for networks I get:
```
iwlist ehh1 scan
eth1     No scan results
```

And I have several networks in my area, most of them using wpa, but I have wpasupplicant installed.

Does anyone know how I can solve this problem?

---

### Post by Zorael on 2007-09-02
Does typing the following in a terminal render it able to detect again?
```
$ sudo modprobe -r ipw3945
$ sudo modprobe ipw3945
```

And do mind, you have to run 'iwlist eth1 scan' with sudo to make it scan anew, else it will just output the results of the last scan.


If so, you're in the same boat I am. It works effortlessly for some, and just awful for us others.


[http://ubuntuforums.org/showthread.php?t=533331](http://ubuntuforums.org/showthread.php?t=533331)
[http://ubuntuforums.org/showthread.php?p=3297574](http://ubuntuforums.org/showthread.php?p=3297574)

[https://bugs.launchpad.net/ipw3945/+bug/134515](https://bugs.launchpad.net/ipw3945/+bug/134515)

---

### Post by ahlt on 2007-09-02
No changes :/

Could there be something wrong with my setup? This is what iwconfig gives me:
```
iwconfig
lo	no wireless extensions.

eth0	no wireless extensions.

eth1	unassociated  ESSID:off/any
	Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
	Bit Rate: 0 kb/s   Tx-Power:16 dBm
	Retry limit:15   RTS thr:off   Fragment thr:off
	Encryption key:off
	Power Management:off
	Link Quality:0  Signal level:0  Noise level:0
	Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0  Invalid misc:13  Missed beacon: 0

```

---

### Post by Zorael on 2007-09-02
I also get "Frequency=nan kHz", which I read somewhere means 'not a number' and equals something wrong.

But I can force it back into shape by either rebooting, or stopping and then starting the ipw3945 module. Once it "works", I only have one connection attempt before I have to reboot or stop/start again, as I explained in those threads (and in that launchpad bug). So if it fails to connect: stop/start. If it connects but the connection dies (which happens more often than it should): stop/start.

If stopping and starting does nothing to help, I haven't the slightest idea what could be wrong. I suppose you've already made sure your kill switch isn't toggled, if you have one?

---

### Post by ahlt on 2007-09-02
I remember reading that you could check if the switch was turned on/off trough the terminal, not sure of the command? And I did that a couple of weeks ago, and the switch was turned on.

And I can't find any physical switch on the laptop, which is a Zepto Znote 6014W...

---

### Post by Ultra Magnus on 2007-09-02
I have exactly this problem - Everywhere else I can pick up any wireless network - but I can't even see the one at home. What router do you use? Mine is a D-Link DSL-G604T - I can't think what could be wrong with my wireless card could it be something to do with the router?

---

### Post by ahlt on 2007-09-03
Mine is a D-link Di-624.

But what could be wrong with the router then? I currently connect trough it wireless with my other laptop, which runs Windows XP...

---

### Post by Ultra Magnus on 2007-09-03
Hi

I'm not sure, to be honest I'm not really sure what I'm doing anyway. My thread is here, I think we have the same problem

[http://ubuntuforums.org/showthread.php?t=540956](http://ubuntuforums.org/showthread.php?t=540956)

Have you checked whether your router is able to see your Ubuntu computer - Mine can see me but I can't see it for some reason.

---

### Post by ahlt on 2007-09-05
> **Ultra Magnus said:**
> Have you checked whether your router is able to see your Ubuntu computer

How can I check that? I don't see anything related to that on the administrationpanel for my d-link.

---

### Post by kaar3l on 2007-09-05
> **ahlt said:**
> No changes :/

Could there be something wrong with my setup? This is what iwconfig gives me:
```
iwconfig
lo	no wireless extensions.

eth0	no wireless extensions.

eth1	unassociated  ESSID:off/any
	Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
	Bit Rate: 0 kb/s   Tx-Power:16 dBm
	Retry limit:15   RTS thr:off   Fragment thr:off
	Encryption key:off
	Power Management:off
	Link Quality:0  Signal level:0  Noise level:0
	Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0  Invalid misc:13  Missed beacon: 0

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:131   Missed beacon:0

```
For me my 3945 sayas same thing and when i do 
```
iwlist eth1 scan
```
then i can see some networks and connect to them. :)

---

### Post by ahlt on 2007-09-06
Damn, why can't I find any networks then?:/

Gonna try another area tomorrow, bringing the laptop to school, perhaps I can see some networks there, will keep you posted...

---

### Post by ahlt on 2007-09-07
Got some interesting information for you guys. I actually manage to find a network at my school. I didn't have the opportunity to connect, since I don't have the passkey, but anyway, I found a network!:)

Anyway, then it seems that it is the D-link which causes my porblem?

---

### Post by RyanGT on 2007-12-29
I don't know if this is helpful or the same problem, but I solved my issues following this thread:
[http://ubuntuforums.org/showthread.php?t=587576](http://ubuntuforums.org/showthread.php?t=587576)

Basically, I get better results with the generic kernel than with the 386 kernel.  It seems like there is a difference in the driver between the two.

HTH,

Ryan

---

### Post by natehall on 2007-12-30
This link might help : [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

Make sure you have the iwl3945 module installed. (I think modprobe is the command you need for that.) I tried this fix without iwl3945 installed and lost all my wireless access!

---

