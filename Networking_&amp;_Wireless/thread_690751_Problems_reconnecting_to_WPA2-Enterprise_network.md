---
title: "Problems reconnecting to WPA2-Enterprise network"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by Carceri on 2008-02-07
I have some problems getting the Network Manager to reconnect to my company's WPA2 protected network. More specifically:

We run a WPA2-Enterprise protected wireless network, where clients are issued certificates which they use to log on to the network. The EAP profile is EAP-TLS. I have the following three files:

client.crt
client.key
ca.crt

Which are my certificate, my private key and the certificate of the CA who issued my certificate, as well as the certificate of the RADIUS server we authenticate towards.

When I first click on the network, I am prompted to select the protection used, and enter my information. I select WPA2-Enterprise, EAP-TLS, pick my certificates, enter my certificate CN in the "anonymous identity" field (required by the RADIUS server) and finally type in my password for the private key. I choose to automatically connect to this network, and click the "Connect" button. Everything works fine, and I am now connected to the network.

However...

If I am disconnected for some reason (radio interference, going into standby, rebooting the machine, logging out, etc.) it tries to automatically connect to the network again, but never succeeds. In the log it says that it is getting a new key for the network, but nothing happens.

In the keyring manager, I can see that it has stored the password I used to unlock my private key under the name of the connection, but I have a feeling that it fails to reconnect, because it cannot decrypt my private key (still just a guess though). Reconnecting to WEP or WPA(2)-PSK networks works fine. In that case the keyring manager stores the network password, and apparently uses it to connect to the network again. However, it does not seem to work when the password is not used to access the network directly, but instead to decrypt my private key, which is then used for EAP-TLS authentication.

By the way, using WPA-Enterprise instead of WPA2-Enterprise makes no difference.

The solution is to select "Connect to Other Network", enter the SSID again and reenter all information, select certificates, etc. and then click connect. Then I am connected again. However, I am getting a little tired of going through this procedure every morning when I arrive at the office, or after every reboot.

Any ideas? Have I found a bug, or am I just doing something wrong?

Edit: Forgot to mention that I am running Ubuntu 7.10

---

### Post by Carceri on 2008-02-10
Anyone? Anyone ever tried using EAP-TLS authentication with certificates?

---

### Post by dsbalentine on 2008-02-11
FYI, i've been able to connect to my company's wireless network using wpa2 enterprise with eap-tls and certificates.  

it doesn't work just clicking on the broadcast ssid though with the network manager, you have to use connect to another network, wpa2 enterprise, tls, then use your info (here it's the user id, personal cert and ca and then the password for the cert)

My only problem is using the intel a/b/g chip, iwl4695, the modiule dies after a few hours and i have to reload it, which tends to confuse the network manager a bit.  other than that it associates very quickly and has pretty good speed.  this is in 7.10.  I've been the linux guy here that's made our crap active directory authed network work in linux through several ditros and versions of linux as well as different auth types, so i'd be happy to help with anything i can if you have any questions

---

### Post by Carceri on 2008-02-11
As you can see from my first post, I have no problems getting it to work. I just have to pick certificates again every time I reconnect, and that get's annoying. For WPA-Personal it just saves the password and automatically reconnects the next time. Not so with WPA(2)-Enterprise. Do you have the same problem, and if no, what did you do different :)

---

### Post by mojportal on 2008-02-11
I cannot automatic connect with wpa2-personal. Something reset to wep and change password. Every time when want connect must in network manager change WEP to WPA and enter password. How can fix that?

---

### Post by Carceri on 2008-02-12
Some more information... When I start up the computer and it tries to log on, I get the following in the log:

Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'NetworkName' received. 
Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0/wireless): access point 'NetworkName' is encrypted, but NO valid key exists.  New key neede 
Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'NetworkName'. 
Feb 12 08:59:56 geshenna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 

This repeats several times. When I manually pick my certificates again, everything works:

Feb 12 09:01:04 geshenna NetworkManager: <info>  Activation (wlan0) started... 
Feb 12 09:01:04 geshenna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 09:01:04 geshenna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb 12 09:01:04 geshenna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 09:01:04 geshenna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 09:01:04 geshenna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb 12 09:01:04 geshenna NetworkManager: <info>  Activation (wlan0/wireless): access point 'NetworkName' is encrypted, and a key exists.  No new key needed. 

...and then it logs on.

I have talked to another user, and he has the exact same problem. He did say that it worked in Feisty though, so something seems to be broken since then.

---

