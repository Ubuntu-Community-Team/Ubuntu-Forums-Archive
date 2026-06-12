---
title: "Unable to connect to Secure wireless network from Ubuntu 7.10"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by kittu_81 on 2007-10-29
Hi

I just upgraded from Ubnutu 7.04 to 7.10. I have a Dell 1390 Wireless LAN card.
It was working absolutely fine on 7.04. But after upgrading to 7.10, my wireless drivers are installed.
And my laptop is able to connect to an un secure network. But every time I try to connect to a secure wireless n/w it keeps prompting for Passphrase. I enter it but it cant connect to the network.
I have WEP encryption. Tried to follow steps regarding Wireless encryption on this forum, to no avail :(

Please help..

---

### Post by inyoka on 2007-10-29
I have had some problems with Encrypted Wireless connections, but all have come down to one of the following:
:
**1) Wrong Password stored in default keyring. (or just a wrong password)**
Check your default keyring is not storing an incorrect password from a previous connection attempt and trying to authenticate for you, if it is goto "System>Administration>Keyring Manager" and delete the offending key. It still prompts you to enter the system password to unlock the keyring before logging in, don't confuse this with the Wireless password.
**2) Wrong Type of Encryption**
Double check what encryption your hub is using.  If you have deleted your Default Keyring you should just have to select the network from the drop-down list when clicking on the network icon in your system tray, and enter the password.
**3) Hub has crashed, or password not applied.**
Check the hub/switch hasn't crashed, mine crashes when generating a new key sometimes, make sure its generated the key and make sure you apply the settings.

If you can connect unencrypted, its unlikely to be a driver fault.  Is the unencrypted network the same network? Or are they separate?  Sorry if these seem like simplistic answers/questions, if you have checked all these please post with more information.  There are lots of things that could be going on and it depends on how much you know as to what is more likely.

---

### Post by kittu_81 on 2007-11-01
> **inyoka said:**
> I have had some problems with Encrypted Wireless connections, but all have come down to one of the following:
:
**1) Wrong Password stored in default keyring. (or just a wrong password)**
Check your default keyring is not storing an incorrect password from a previous connection attempt and trying to authenticate for you, if it is goto "System>Administration>Keyring Manager" and delete the offending key. It still prompts you to enter the system password to unlock the keyring before logging in, don't confuse this with the Wireless password.
**2) Wrong Type of Encryption**
Double check what encryption your hub is using.  If you have deleted your Default Keyring you should just have to select the network from the drop-down list when clicking on the network icon in your system tray, and enter the password.
**3) Hub has crashed, or password not applied.**
Check the hub/switch hasn't crashed, mine crashes when generating a new key sometimes, make sure its generated the key and make sure you apply the settings.

If you can connect unencrypted, its unlikely to be a driver fault.  Is the unencrypted network the same network? Or are they separate?  Sorry if these seem like simplistic answers/questions, if you have checked all these please post with more information.  There are lots of things that could be going on and it depends on how much you know as to what is more likely.

Hi
1. My Keyring manager shows 3 keys. login, default and session. What does it mean?
2. I would click on the network from drop down list and then it would prompt for the passphrase which i believe i wud enter correctly. 
3. the hub is perfectly fine. everybody else's wireless is working on it.
i dont know why is this happening.
Any solutions??

---

