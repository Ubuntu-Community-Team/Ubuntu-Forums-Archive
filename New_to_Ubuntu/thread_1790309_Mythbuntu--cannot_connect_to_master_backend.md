---
title: "Mythbuntu--cannot connect to master backend"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by maryhigginsrice on 2011-06-24
Hi everyone. I installed Mythbuntu on my old machine-Dimension E310--Windows XP. The installation went okay, but everytime I start the front end I receive an error message stating that the master backend cannot connect. I am using the router ip address instead of the default--127.0.0.1. The backend does connect,but I still receive the error messages. I have a Hauppauge 1600, which is recognized, but how do I use it to watch live tv? I made a second partition for my recordings, but how do I get the backend to recgnize the partition. I am also using a router(Belkin) .Any assistance will be appreciated. mary:(

---

### Post by bance on 2011-06-25
Hi Mary,

Here's a [_[COLOR=Red]link[/COLOR]_]("http://parker1.co.uk/mythtv_tips.php") to a good set up guide!

The backends IP should be the same in all of the following files:-


[LIST]
[*]/home/user/.mythtv/mysql.txt
[*]/home/user/.mythtv/config.xml
[*]/home/mythtv/.mythtv/mysql.txt
[*]/home/mythtv/.mythtv/config.xml
[*]/etc/mythtv/mysql.txt
[*]/etc/mythtv/config.xml
[/LIST]
(substitute /user/ for your user name)

Here's a [_[COLOR=Red]link[/COLOR]_]("http://ubuntuforums.org/forumdisplay.php?f=301") to myth-buntu forums

HTH Steve.

---

### Post by tgm4883 on 2011-06-25
So just to confirm, the backend connects but the frontend doesn't. Is the frontend on a separate machine? Did you setup mythtv-setup to use the actual IP rather than 127.0.0.1

---

