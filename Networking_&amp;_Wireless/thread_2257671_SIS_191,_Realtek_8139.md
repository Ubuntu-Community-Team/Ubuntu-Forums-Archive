---
title: "SIS 191, Realtek 8139"
date: 2014-12-21
forum: Networking &amp; Wireless
---

### Post by Vlad_Andrei on 2014-12-21
I installed Lubuntu 14.10 on my ancient PC which is working quite nicely so far but I have no internet connection.
My on-board card is sis 191, I also tried with a realtek 8139 and no luck.
The onboard card is recognized and shown as ethernet network but it won't connect (also I can't ping), and the realtek is not working at all.

Here are some outputs [lsmod]("http://pastebin.com/KzAfb8Lf"), [ifconfig]("http://pastebin.com/uLsrHnDQ") (atm I'm connected using usb tether on my phone) 

I'm here if you need more outputs, I really need your help, I can't figure this out myself. Any help is greatly appreciated.

---

### Post by mörgæs on 2014-12-21
Hi, welcome to the fora.

The SIS card has been a troublemaker for some time, as can be see here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345374](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345374)

Does the command ```
sudo ifconfig eth0 mtu 1492
``` help?

---

### Post by Vlad_Andrei on 2014-12-21
Hello, thank you for the fast reply. 
I believe I tried this command before posting here and no, it didn't help.

---

### Post by Vlad_Andrei on 2014-12-22
Ok, new updates: I found out that if I set an Address,Netmask, Gateway and DNS servers (which I used 8.8.8.8 and 8.8.4.4) it says that is connected but internet won't work.
My guess is that the address and the gateway are wrong but I have no idea how to find them so I can't be sure. If I set it to DHCP it just tries to connect and after ~10 seconds it says disconnected.
It's the sis191 I'm talking about, the rtl8139 is not even recognized, even if I tried to blacklist 8139cp or 8139too.

Any idea how to find my address/gateway? If no one can help me I think I will install windows xp on my external harddrive and do an ipconfig /all , I see no other way around, lol..

---

### Post by praseodym on 2014-12-22
Please run the wireless script from the sticky thread in this forum and upload the respective txt file created

---

### Post by Vlad_Andrei on 2014-12-22
Sorry for not posting it before!
This is the [wireless-info.txt]("http://pastebin.com/r7xxtn5r") and the [script ]("http://pastebin.com/1Z4sK7hi")

---

### Post by praseodym on 2014-12-22
The Realtek device should run with one of the loaded drivers only:
```

echo "blacklist 8130cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and check
```

ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
dmesg | egrep "81|sis"
cat /etc/resolv.conf
route -n
```

---

### Post by Vlad_Andrei on 2014-12-22
Hello, I tried to blacklist that, reboot and the realtek card is still not recognized, only the sis one, idk why.
Here are the outputs of the commands above [http://pastebin.com/E1RaJykr](http://pastebin.com/E1RaJykr) .

---

### Post by praseodym on 2014-12-22
> ```
[    1.808321] 8139too 0000:00:0e.0: Chip not responding, ignoring board
[    1.808488] 8139too: probe of 0000:00:0e.0 failed with error -5
```
Maybe its broken?
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by Vlad_Andrei on 2014-12-22
Thanks, but no luck, the realtek is not being recognized and the sis is not getting the IP adress.

the output of the last command: # PCI device 0x1039:0x0191 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:fc:c8:e1:01", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

---

### Post by praseodym on 2014-12-22
The file /etc/resolv.conf was empty:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Vlad_Andrei on 2014-12-22
I'm sorry, still same results.

---

### Post by praseodym on 2014-12-22
Please check:
```

sudo modprobe -rfv sis190 8139too #unloads both drivers
sudo modprobe -v 8139too #loads Realtek
sudo service network-manager restart
```
If it doesn't work, remove any network in "cable" and "dsl" and reboot.
How do you connect? Router/modem combo, modem or both?

---

### Post by Vlad_Andrei on 2014-12-22
The 1st command returned "rmmod sis190"
The 2nd one insmod /lib/modules/3.16.0-28-generic/kernel/drivers/net/ethernet/realtek/8139too.ko 
and after the restart I had no internet connection and no mac addresses to choose from when I wanted to create a new ethernet connection under "Network Connection" in settings. So I suppose either the card is faulty or the drivers are not working proprely, either way, I think is better if we focus on the sis190 since using it I had the best results and closest I could get to internet (being recognized as an ethernet card, saying is connected to internet but no real connection if I enter ip addresses manually etc). What do you think?
Also, I'm using a router/modem combo.

---

### Post by praseodym on 2014-12-22
Ok, reload the sis:
```

sudo modprobe -rfv 8139too
sudo modprobe -v sis190
```
Did you get Login/PW for PPPoE connection from your ISP? Add it to the router interface while connected via cable. The hardware setup should be

```
splitter->modem->router->cable to PC
```

---

### Post by Vlad_Andrei on 2014-12-24
Thank you a lot for your help, in the end I bought a cheap network card which seems to work OOB unlike the other 2.

---

