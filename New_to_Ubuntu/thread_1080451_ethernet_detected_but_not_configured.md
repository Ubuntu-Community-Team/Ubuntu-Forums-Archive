---
title: "ethernet detected but not configured"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by abhishekg on 2009-02-25
hii i am a newbie .having problem in connecting to internet ...
precisely problem is :
after reading from Help on how to configure ethernet i have pasted

auto eth0
iface eth0 inet dhcp

in /etc/network/interfaces 
tried also 
sudo ifconfig eth0 up followd by dhclient 
but LED for LAN in adsl doesn't glow hence i remain disconnected initially ,hoever after 15-20 min eth0 automatically gets configure LED starts glowing and connection establishes .the same story repeats every time i boot up...

i have searched forums,no one seems to suffer from this stupid problem ,so at last i had to post it ..

any help /advice is highly appreciated 

thanks

---

### Post by carml on 2009-02-25
What kind of connection you use? If you have an ADSL modem from your provider,maybe a look at System->Help & support can help you.
If so,see the instructions at the section Internet -> Modem ADSL.
Otherwise you'll have to know exactly the parameters used by your provider.

---

