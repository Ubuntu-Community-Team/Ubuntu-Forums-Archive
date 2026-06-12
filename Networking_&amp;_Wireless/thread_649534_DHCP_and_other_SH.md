---
title: "DHCP and other SH"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by unq on 2007-12-25
So, my isp needs a login and password to provide internet to user.
I have an sh script that logins to my isp, and I want automatic login as my computer starts

!The trouble is, that I need to run this script after dhcp client recives the ip address.

I tried to run this script from rc.local but it runs earlier than reciving ip ..

some ideea?


using ubuntu 7.10 desktop

---

### Post by Saahib on 2007-12-25
You can use "Sleep" so that it can wait for few seconds before login.

---

### Post by unq on 2007-12-25
yeah I can but is not a profesional solution :)

---

### Post by unq on 2007-12-25
nobody knows how to start a progrom at the end of reciving IP by dhcp?:confused::confused::confused:

---

### Post by unq on 2008-01-14
the solution:
put the sh script into /etc/init.d
for example my_sh_script
then create sym link to it in /etc/rc2.d with command
ln -s /etc/init.d/my_sh_script /etc/rc2.d/S99my_sh_script (where S mean start and 99 order of loading, and the name of your script at the end.)

now you can order your order of loading.
enjoy :KS

---

