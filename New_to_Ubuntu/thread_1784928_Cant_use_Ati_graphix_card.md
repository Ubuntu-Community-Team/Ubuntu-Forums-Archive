---
title: "Cant use Ati graphix card"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by reelo2228 on 2011-06-17
Hey again! so i tried to install ubuntu properly (not WUBI) on my desktop and after installation, i get nothing after the login screen, did a few error check then found out that its my Ati card. I took it out and ubuntu loged in normally (but no unity)i tried to download the driver for Ati card (RX300 SE). But when i tired to run it in the terminal it gives me this error

"ERROR: ./default_policy.sh does not support version
defaut:v2:1686:lib::none:2.6.38-8-generic; make sure that the version is being correctly set by --iscurrentdistro"

any work around to this?:(

---

### Post by reelo2228 on 2011-06-17
Bumping for desperate help

---

### Post by clhsharky on 2011-06-17
reelo2228

> "ERROR: ./default_policy.sh does not support version
defaut:v2:1686:lib::none:2.6.38-8-generic; make sure that the version is being correctly set by --iscurrentdistro"

any work around to this?
No

Open-source radeon driver will be the correct driver for your legacy Ati  (RX300 SE)card.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
> If you've previously installed the ATI binary/proprietary driver (a.k.a Catalyst/fglrx), you need to make sure it's fully purged before trying to use the open-source ati/radeon driver. See this page
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Sharky

---

### Post by wildmanne39 on 2011-06-17
> **reelo2228 said:**
> Hey again! so i tried to install ubuntu properly (not WUBI) on my desktop and after installation, i get nothing after the login screen, did a few error check then found out that its my Ati card. I took it out and ubuntu loged in normally (but no unity)i tried to download the driver for Ati card (RX300 SE). But when i tired to run it in the terminal it gives me this error

"ERROR: ./default_policy.sh does not support version
defaut:v2:1686:lib::none:2.6.38-8-generic; make sure that the version is being correctly set by --iscurrentdistro"

any work around to this?:(HI, I think you need to remove that driver, I am going to give you a link for the driver for you card.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

---

### Post by reelo2228 on 2011-06-18
the driver i downloaded from ati didnt really install i think, coz of the error, it showed in the terminal that the temp install files were removed( a roll back i think).
do i still need to uninstall it? ( whts the difference between uninstall and purge?

---

### Post by reelo2228 on 2011-06-18
Hey! sory for the slow feedback, i managed to install the open source drivers and the radeon card worked, the desktop was able to be displayed. but i cant open the catalyst control center.. i guess its half way progress xD

---

### Post by wildmanne39 on 2011-06-18
> **reelo2228 said:**
> the driver i downloaded from ati didnt really install i think, coz of the error, it showed in the terminal that the temp install files were removed( a roll back i think).
do i still need to uninstall it? ( whts the difference between uninstall and purge?
Hi, purge will remove all the package including the configuration file. Follow the directions on the link I gave you and it will tell you to remove the other driver I believe but do what it says, if it says something different then I do.

---

