---
title: "Secure server wi-fi hotspot without wpa-supplicant, is it possible?"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2008-08-08
Hello there! I'm talking about my Ubuntu server with WI-FI PCI card ('wireless-mode master' in my /etc/network/interfaces on server). So Server is my Ubuntu server PC with WI-FI access point. Client is a WI-Fi equipped notebook. Everything's fine when I connect without a passphrase so my problem is encryption only. A few questions:

1. Is that possible to make a secure WI-FI access point without wpa-supplicant on server?

2. How on earth does the 'wireless-key' parameter in /etc/network/interfaces work? I tried to supply a password in ASCII and I failed connecting from client, I tried to convert it in HEX and I failed again. 

3. What type of encryption WI-FI server offers by default? Can I change it or I have to use wpa-supplicant for it?

4. What does the 'iwlist <interface name> key' says when I scan a network from my client? I see a HEX string but it's different from the string that I supply in 'wireless-key' string.

5. Is 'wpa-passphrase' compatible with the 'wireless-key' parameter?

Thank you for your help!

---

### Post by dca on 2008-08-08
I don't quite understand... If you have an access point that only has WEP encryption available (because it may be an older model), then I would think it offers some sort of MAC address filtering that would only allow MAC addressess you add to the list access to that WiFi network.

---

### Post by PryGuy on 2008-08-08
Look, I set up a secure access point on my Ubuntu server with WI-FI PCI card ('wireless-mode master' in my /etc/network/interfaces on server). So Ubuntu server PC is my access point. Everything's fine when I connect without a passphrase so my problem is encryption only. Corrected the previous post.

---

### Post by dca on 2008-08-08
If the card is an older WiFi NIC, it may not offer WPA encryption, only WEP.  Some of the older cards that manufacturers still support sometimes offer a firmware upgrade to enable the WPA support.

---

### Post by PryGuy on 2008-08-08
Got what you meant finally... :oops: I've got an atheros based card. Well, anyway, the question remains, is that necessary to use 'wpa-supplicant' on server to go secure?

---

### Post by dca on 2008-08-08
...don't know if this will help or hurt but this article kind of explains using a PC as a WiFi access point...
 
[http://www.linux.com/articles/55617](http://www.linux.com/articles/55617)

---

### Post by PryGuy on 2008-08-08
it uses 'wpa-supplicant' also... Thanks anyway...

---

### Post by easyhorpak on 2008-08-17
1. Is that possible to make a secure WI-FI access point without wpa-supplicant on server?

yes, it is.


2. How on earth does the 'wireless-key' parameter in /etc/network/interfaces work? I tried to supply a password in ASCII and I failed connecting from client, I tried to convert it in HEX and I failed again.

no wireless key on server . it 's authen options.



3. What type of encryption WI-FI server offers by default? Can I change it or I have to use wpa-supplicant for it?

no . it 's webpage authen


4. What does the 'iwlist <interface name> key' says when I scan a network from my client? I see a HEX string but it's different from the string that I supply in 'wireless-key' string.



5. Is 'wpa-passphrase' compatible with the 'wireless-key' parameter?

---

### Post by PryGuy on 2008-08-18
> **easyhorpak said:**
> 2. How on earth does the 'wireless-key' parameter in /etc/network/interfaces work? I tried to supply a password in ASCII and I failed connecting from client, I tried to convert it in HEX and I failed again.

no wireless key on server . it 's authen options.You mean?
> **easyhorpak said:**
> 3. What type of encryption WI-FI server offers by default? Can I change it or I have to use wpa-supplicant for it?

no . it 's webpage authenWeb page authentication???!!!

---

### Post by lisati on 2008-08-18
There's a tutorial on setting up wireless security at [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Reading through the messages in this thread, I suspect the contributors so far might have been talking at "crossed purposes".

Here's my two cents worth, offered in the hope of helping everyone make sure they are talking about the same thing: Many routers use a browser based method of allowing the user to configure them. The password required to access the configuration "web page" is quite separate from the WEP or WPA passphrase and has nothing to do with wpa-supplicant. The exact details will differ according to the make and model.

---

