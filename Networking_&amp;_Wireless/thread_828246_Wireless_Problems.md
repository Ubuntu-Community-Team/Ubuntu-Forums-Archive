---
title: "Wireless Problems"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by Amalgamayne on 2008-06-13
Hello:

I just put Hardy onto my new Dell XPS 1530, and the wireless will only turn on about every third time I boot up my computer.  This is quite frustrating!  When the wireless is "off" Hardy notices (through lspci) that I have a wireless card, but whenever I try any of the commands (ifconfig, iwconfig), nothing works!

I have an intel wireless 3945 card.  Any suggestions would be extremely helpful.

Thanks!

---

### Post by chili555 on 2008-06-13
What does:```
sudo iwlist wlan0
```tell us? Is there any encryption in place on your router or access point?

When you say it "turns on," do you mean it connects? Or what?

---

### Post by malath on 2008-06-13
Hi.
i got the same problem, dell inspiron 630m. I installed the virtualbox-ose-module and after rebooting no wireless was found, knowing that i was using it normally before. i removed the total linux from the system and reinstall it again and teh same thing still no wire less.
 up on iwconfig it says:
lo        no wireless extensions.

eth0      no wireless extensions.
and up on 
root@malath-laptop:~# iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

---

### Post by Amalgamayne on 2008-06-13
> **chili555 said:**
> What does:```
sudo iwlist wlan0
```tell us? Is there any encryption in place on your router or access point?

When you say it "turns on," do you mean it connects? Or what?

My terminal says this is an unrecognized command.

---

### Post by chili555 on 2008-06-13
Sorry. I made a mistake. It should be:```
sudo iwlist wlan0 scan
```I apologize.

---

### Post by Amalgamayne on 2008-06-13
Here's the output:

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:12:6D:5F
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=77/100  Signal level=-57 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000012713eff024


I believe I get this since the wireless is working.  It has been working today, so if I reboot and try this command, will this get Ubuntu to enable wifi?

Thanks

---

### Post by malath on 2008-06-13
up on the command it tells 
malath@malath-laptop:~$ sudo iwlist wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

There is no encryption on the router. i was able to access the wirless before, but now i think ubuntu cannot see the wirelss broadband card.

can you help please.

---

### Post by alchemist0 on 2008-06-13
.....hmmm.....Same problem here! used

```
sudo iwlist wlan0 scan

```

but the output was:
```
wlan0     Interface doesn't support scanning.

```

now what???](*,)](*,)](*,)

---

### Post by prj44 on 2008-06-13
Same problems, but with another twist.

My router is WPA2 Personal enabled.  So I make the appropriate setup in Network Settings, exit, and then re-enter Network Setings.  The settings have been changed back to WPA Personal!  Sounds like the correct information wasn't properly recorded, which would certainly complicate the task of connecting to my router.

This is done on a Centrino Laptop, which works flawlessly with the router in XP.  Is this a bug???

---

### Post by malath on 2008-06-14
I have rebooted the system and pressed ESC to enter menu
I have choosen to boot to generic kernal NOT the recovery mode
and it worked.

---

### Post by namraw on 2008-06-14
i have the same problem i dunno if this helps but i ran the command:
```
dmesg
``` 
and found the following lines:
```

[  174.173460] zd1211rw 2-3:1.0: firmware version 4725
[  174.213448] zd1211rw 2-3:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
[  175.215356] zd1211rw 2-3:1.0: error ioread32(CR_REG1): -110

```

i know thats my driver as i did some research on it wen i thought wireless wasn't "out of the box"

hope that can help

ps

```
sudo iwlist eth1 scan
```
returns:
```
eth1     No Scan Results
```

---

### Post by chili555 on 2008-06-14
> **alchemist0 said:**
> .....hmmm.....Same problem here! used

```
sudo iwlist wlan0 scan

```

but the output was:
```
wlan0     Interface doesn't support scanning.

```

now what???](*,)](*,)](*,)Perhaps your wireless interface is not wlan0? Please do:```
iwconfig
```Substitute the interface that shows data. On my laptop, it's eth1.

@everybody-

You have a variety of problems, none as far as I can see, like the original poster: > the wireless will only turn on about every third time I boot up my computerPlease start a new thread and tell us what your specific problem is. At a minimum, please post a coherent description of your symptoms, what you have tried so far and ***sudo** lshw -C network*. Network Manager does *not* allow two IP addresses on two interfaces at once, so detach your wire before you try anything with your wireless.

I like to answer posts here, but I automatically skip these:> So. my wrless wnt werk. pls help. ty

---

