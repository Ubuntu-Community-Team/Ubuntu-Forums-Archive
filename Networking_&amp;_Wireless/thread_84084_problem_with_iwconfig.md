---
title: "problem with iwconfig"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by espanhol on 2005-10-30
Hi there

i am trying to configure my network and when i:
```
sudo iwconfig essid "SMC" mode Managed key s:blablabla
```

i get an error like this:

```
Error for wireless request "Set Encode" (8B2A) :
SET failed on device wlan0 ; Invalid argument
```

anyone can helpme out here?

---

### Post by spd106 on 2005-10-31
[QUOTE=espanhol]Hi there

i am trying to configure my network and when i:
```
sudo iwconfig essid "SMC" mode Managed key s:blablabla
```

i get an error like this:

```
Error for wireless request "Set Encode" (8B2A) :
SET failed on device wlan0 ; Invalid argument
```

anyone can helpme out here?[/QUOTE]

You should pass the interface name as an argument to iwconfig ie
**sudo iwconfig wlan0 essid "SMC" mode Managed key s:blablabla**

It might be easier to use the network manager gui tool. I find it works quite well. 

If you're stuck to the console then try editing the /etc/network/interfaces file and using **ifup**.

---

### Post by fred93 on 2008-02-02
When I type:
```
iwconfig ath0 mode Master
```

I get a similar error saying:
```
Error for wireless request "Set Mode" (8B06):
     SET failed on device ath0 ; Invalid argument.
```

Why would I get that error even though I have specified the interface?

Also, I am running Ubuntu Server 7.04 so a GUI is out of the question.

---

