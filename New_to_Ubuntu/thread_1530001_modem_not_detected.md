---
title: "modem not detected"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by sair.aruna on 2010-07-13
Hey i just installed ubuntu 9.04 on my system. but i'm unable to connect to the internet. i use a SmartAX mt882 modem and connect it to the computer using the  ethernet port. my this modem is not being detected. how can i solve this problem?

---

### Post by jerenept on 2010-07-13
This may seem like a silly question, but does your Ethernet port work? Did the modem install any special software on the machine? usually ethernet network equipment is compatible with ubuntu

---

### Post by sair.aruna on 2010-07-13
> but does your Ethernet port work

Well the ethernet port works fine with Windows 7.

 > Did the modem install any special software on the machine

No special software was installed on the machine.

I've had the same problem with another PC.I didn't get the problem fixed then.Since then I've been working with windows. Now I'm thinking of shifting to Ubuntu. I really want to get a solution to this problem this time.

---

### Post by MrOneEyedBoh on 2010-07-13
not to really hijack this but I tried to get my cousins' laptop connect ( hes using ubuntu ) to his wireless and we cant figure it out. In windows ya know how you can search for a hotspot and then click on connect and then type in the WEP key if its needed? Well we cant get that on his laptop.

---

### Post by gandaran on 2010-07-13
> **MrOneEyedBoh said:**
> not to really hijack this but I tried to get my cousins' laptop connect ( hes using ubuntu ) to his wireless and we cant figure it out. In windows ya know how you can search for a hotspot and then click on connect and then type in the WEP key if its needed? Well we cant get that on his laptop.
first you need to know what brand of wireless card and if the driver is installed, try connecting the laptop via ethernet port to internet  and run the software data update command in terminal
```
sudo apt-get update
```
then go to system » administration » hardware drivers, if you see a driver there install it and reboot, the panel network manager should now pick up the wireless network, just fill in the password details like in windows.
if you don't find the driver post back the model and brand of wireless card or paste here the results from this command
```
lspci
```

---

### Post by gandaran on 2010-07-13
> **sair.aruna said:**
> Hey i just installed ubuntu 9.04 on my system. but i'm unable to connect to the internet. i use a SmartAX mt882 modem and connect it to the computer using the  ethernet port. my this modem is not being detected. how can i solve this problem?
one question, which dials out to your internet provider, the modem or you computer?
if it's the modem check if dhcp server is enabled in the modem configuration page, should work just connecting to ethernet port if DHCP is enabled.

---

### Post by alphacrucis2 on 2010-07-13
> **sair.aruna said:**
> Hey i just installed ubuntu 9.04 on my system. but i'm unable to connect to the internet. i use a SmartAX mt882 modem and connect it to the computer using the  ethernet port. my this modem is not being detected. how can i solve this problem?


Applications - Accessories - Terminal. Then these commands:

```
ifconfig
```

```
route -n
```

```
sudo lshw -C Network
```

You can direct the output of these commands to a file. For example:

```
ifconfig > Desktop/ifconfig.txt
```

Then copy the output files from your Ubuntu Desktop to somewhere Windows can access them and post the output in this thread using code tags.

---

