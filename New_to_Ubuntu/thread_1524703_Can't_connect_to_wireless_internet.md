---
title: "Can't connect to wireless internet"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-05
My wireless suddenly stopped working last night.  Ubuntu 10.04 on a Dell Mini 10v netbook.  It can see the network, asks for password but can't connect.  I've rebooted, reset the router AND modem.  Nothing.

---

### Post by jtarin on 2010-07-05
Post results from terminal command ```
ifconfig -a
```

---

### Post by TriBlox6432 on 2010-07-05
```

michael@mCarey-NetBook:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:e8:aa:0e:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:24:2c:a0:d6:13  
          inet6 addr: fe80::224:2cff:fea0:d613/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

michael@mCarey-NetBook:~$ 

```

---

### Post by jtarin on 2010-07-05
Now try this command and post
```
route -n
```

Run this command and post any results
```
sudo /etc/init.d/networking restart
```
Try your network after the last.

---

### Post by TriBlox6432 on 2010-07-06
Alright.  I'll hopefully try that tomorrow.  My home wireless internet got shut down so I'm at the library now, but didn't think to bring my netbook.  :p

---

### Post by thunderbird985 on 2010-07-06
I have the same problem jtarin.  Except my home wireless network is steady.  I'll run those commands and post the results...if possible.  I have to switch OS's.

---

### Post by carlexpc on 2010-07-06
What networking tools does your pc use to manage your network connectivity? Are you using the default Network Manager?

---

### Post by thunderbird985 on 2010-07-06
I am using NetworkManager Applet 0.8, the one that installed standard with 10.04

I just tried what jtarin said. No luck :(

---

### Post by carlexpc on 2010-07-06
> **thunderbird985 said:**
> I am using NetworkManager Applet 0.8, the one that installed standard with 10.04

I just tried what jtarin said. No luck :(


Open your Network Manager and go to the Wireless tab, try to delete all the wireless networks ("Auto <ssid>") on the list and restart your network service.

---

### Post by thunderbird985 on 2010-07-07
> **carlexpc said:**
> Open your Network Manager and go to the Wireless tab, try to delete all the wireless networks ("Auto <ssid>") on the list and restart your network service.

How do  I restart the network service? The command that jtarin listed?


Edit:  I deleted all of them, reconfigured network interfaces, and it still doesnt work. Could be the driver?

---

### Post by TriBlox6432 on 2010-07-08
Well, I'm at the library now, and didn't run ANY additional commands, but it's working.  It connected to the public wifi and I'm currently reading an article on lifehacker so I assume it's all good now.  Thanks for the advice, though unneeded. :D

---

### Post by TriBlox6432 on 2010-07-08
One more quick problem, when I hit the shutdown button (physically on my netbook) it automatically shuts down.  It used to be where it would pop up a menu where I could chose between shutdown, suspend, hibernate, etc.  Is it possible to get this again, so I wont lose my work if I accidentally hit the button?

---

### Post by irv on 2010-07-08
> **TriBlox6432 said:**
> Well, I'm at the library now, and didn't run ANY additional commands, but it's working.  It connected to the public wifi and I'm currently reading an article on lifehacker so I assume it's all good now.  Thanks for the advice, though unneeded. :D

If you get home and you don't have wireless then it could be you wireless at home is not working? If it doesn't make a connection  then click on the network icon in the panel and see if your home network is listed. If not then it is not seeing your network and you need to check your setting in your router.

---

### Post by TriBlox6432 on 2010-07-08
My internet at home was actually cut off from not paying the bill.  But I posted this while we still had service, and the desktop connected via ethernet still worked.  So as long as it works at the library and starbucks, I'm happy.  :D

---

