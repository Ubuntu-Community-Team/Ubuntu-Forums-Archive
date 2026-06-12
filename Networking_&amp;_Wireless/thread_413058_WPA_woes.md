---
title: "WPA woes"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by Amarth on 2007-04-18
Hello!

I'm having lots of trouble setting up WPA on Kubuntu Feisty. It worked fine in Dapper (hell, it even worked fine in Gentoo a couple of years ago), but it doesn't work anymore after a fresh Feisty Beta install. I have the card up and running using ndiswrapper (took too much effort, too, but that was my own fault), and I can connect to unencrypted APs: it pretty much automatically connects to my neighbours open AP now - not the desired behaviour.

I have tried KNetworkManager, but it didn't work (just got stuck at 28% all the time). Various sources seem to suggest removing network-manager helped, but it did nothing for me. I have tried the /etc/network/interfaces way described as stickied here, but it didn't work either. I'm out of ideas.

Can someone help me, please? Thank you!

---

### Post by FreakTech on 2007-04-18
what type of hardware are you running?

---

### Post by Amarth on 2007-04-19
A USR MAXg PCI card (Broadcom chipset).
Product page: [http://www.usr.com/products/networking/wireless-product.asp?sku=USR5417](http://www.usr.com/products/networking/wireless-product.asp?sku=USR5417)

It worked before, it that's any help. :)

---

### Post by FreakTech on 2007-04-19
That could be your problem.  Ubuntu and actually almost all linux distros have problems with broadcom NIC's.  Hopefully someone in the community can help.  i haven't had to deal with it.  My Intel card works perfect right out of the box.  Sorry I couldn't help.

---

### Post by kugn on 2007-04-19
I'm not sure whether it would work, but you might want to try this:

1. Since you used ndiswrapper, blacklist the bcm43xx driver.

2. Comment out everything in /etc/network/interfaces except for the loop section.

3. Convert your WPA password to hex by entering

wpa_passphrase your_ssid your_password

the hex passphrase is the long string that begins after "psk="

4. In KNetworkManager, choose "Connect to other Wireless Network", and use the hex passphrase you got for the password field.

good luck

---

### Post by Amarth on 2007-04-19
Nope, that didn't do it.

First of all, obviously, when I commented out all of /etc/network/interfaces, the adapter wasn't found by KNetworkManager. So what I did was a 'sudo ifconfig wlan0 up', and then I tried entering things like you said, but KNetworkManager still stops at 28%.

---

### Post by RavanH on 2007-04-19
Have you given Wicd Manager a try? It did what Feisty's Network Manager couldn't on my machine... Saved Feisty for me, so to speak. Meaning: I would have ditched Feisty if it wasn't for Wicd getting my wifi to connect. And easy too!

See [http://adam.blackhole.cx/wicd/wb/](http://adam.blackhole.cx/wicd/wb/)

---

### Post by Amarth on 2007-04-19
Didn't work either. It stop on 'obtaining IP', and after a while times out with 'not connected'. Looks like a fine program though. :)

It feels like the problem is on a deeper level... Something wrong with wpa_supplicant or wireless-tools or ndiswrapper or whatever other package that might be used in the process.

More ideas? I feel like just dropping the encryption. Pray there aren't too many wizzkids with too much time in the neighborhood. :)

---

