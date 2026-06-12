---
title: "Wifi works 20 seconds after startup, then not :("
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by r4wMUnt34q on 2008-06-16
Hello guys,

I have troubles with getting my wifi to work. I followed this guide (which worked for a lot of people):
[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html), but when I start Ubuntu, it recongnizes the wireless connection, I select the encryption type, give the password, and for maybe 20 seconds everything works, I can browse the web and so on, but after that the connection is I dunno why lost and wlan0 gives "No results" when I type "sudo iwlist scanning" to the terminal, first it does give the info about the network, but then nothing :(. Everything is fine with the Wifi in my Win XP installation and was fine in Gutsy, please help :(

P.S.: I did a fresh installation of Hardy after formatting my Linux partition, if it helps...

---

### Post by r4wMUnt34q on 2008-07-03
Bump :(

---

### Post by Bubba64 on 2008-07-03
Are using the wifi from add remove or the network manager. Are you if using the network manager running it with roam to connect to another available network, but not a personal one that should have a standard output.

---

### Post by r4wMUnt34q on 2008-07-03
I use the default network manager. I run it with roam mode, but it asked for a password in the beginning I think and it havent asked since then. When I tried to set it up manually (no roaming mode) it didnt work, I used the same configuration as in Gutsy though.

Edit: As I said, sudo iwlist scanning gives no results after those 20 seconds. Can my router possibly reject the connection after such time ?

---

### Post by Bubba64 on 2008-07-03
> **r4wMUnt34q said:**
> I use the default network manager. I run it with roam mode, but it asked for a password in the beginning I think and it havent asked since then. When I tried to set it up manually (no roaming mode) it didnt work, I used the same configuration as in Gutsy though.

On my laptop if I have to change the manual then re input the password I have to do a reboot to get it to work, but as long as I don't mess with the settings it runs on every startup. So try setting it to manual with all the correct settings input the pass word make sure it is detecting your network close that window and let it do the voodoo that it does then close the network manager do a reboot and see if it works.

---

### Post by r4wMUnt34q on 2008-07-03
I can try that when I get home, though I probably tried something like that, thanks for your replies Bubba64

---

### Post by Bubba64 on 2008-07-03
> **r4wMUnt34q said:**
> I can try that when I get home, though I probably tried something like that, thanks for your replies Bubba64

If that works you can save that setting on the network manager main gui so if you go other places you can save the setting there as well if you are taking your laptop to work or where ever. The main thing is making sure you are using the right wep or wpa setting and the correct setting at the dhcp or I think ip settings. If your getting it to work with roam it should work fine in manual if your getting a clear signal. Good Luck

---

### Post by r4wMUnt34q on 2008-07-03
I tried all the possible combinations of wep, wpa and so on, but I will try to look at the IP settings and play with it a little. I think I did set the thing up correctly if it is able to connect and I am able to update my PC. I checked the settings in Windows, its a WEP encryption and the it is ASCII because HEXADECIMAL doesnt allow l in the passphrase and the password contains a l. In Gutsy I used dhcp, but I remember it working with a static address, but Im not sure, thanks again :)

---

