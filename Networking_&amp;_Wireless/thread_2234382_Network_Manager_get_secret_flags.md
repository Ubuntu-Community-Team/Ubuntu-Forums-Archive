---
title: "Network Manager get_secret_flags"
date: 2014-07-14
forum: Networking &amp; Wireless
---

### Post by afhx on 2014-07-14
I note that the problem of a  dialog box appearing which asked for a password which blocks access via a dongle to the internet(  No password seems to be succeed  )  was solved for versions 12.4 and perhaps later   versions by  the following:
add 
options ath5k nothwcrypt=1
to
/etc/modprobe.d/ath5k.conf

However, I have version 14.4 and no ath5k_conf file
This is not an ever present problem but occurs from time to time. Various moves  likes deleting and entering a new connection sometimes works,sometimes the problem resolves itself on re-booting. sometimes removing the dongle and re-inserting works. Sometimes nothing works but then the problem resolves itself. It is a problem I had for years.

---

### Post by afhx on 2014-07-15
Perhaps,  I should give a little more detail. I have a TMobile E1750 dongle. Normally everything works fine.  I use a rule given by sola in December 2009  **Huawei E1750 3G USB modem (T-Mobile web'n'walk Stick V ** . Sorry, I don't know how to specify a specific thread. However, occasionally , especially when I  make repeated attempts to connect, a dialog popped up seeking a password, The password on the Connections fails as does the sudo password.  This blocks all connection attempts. This a recurring problem .The relevant line in the system log appears to be this;
get_secret_flags assertion  ' is_secret_prop (setting, secret_name error ') failed
I have ubuntu 14.4

---

### Post by afhx on 2014-07-17
After some digging around the following might be a solution. I have to wait for the problem to recur to be sure
sudo rfkill list all  # list devices

sudo rfkill unblock all  

sudo service network-manager restart

---

### Post by steeldriver on 2014-07-17
If you have an ath5k device and need to set a module parameter at load time, you can just **create **an ath5k.conf file in /etc/modprobe.d/ and put the options ath5k nothwcrypt=1 line in it, it doesn`t matter that the file doesn't exist already

```

echo 'options ath5k nothwcrypt=1' | sudo tee -a /etc/modprobe.d/ath5k.conf

```

In fact, the filename is not important AFAIK - except it should end in .conf

Sorry, I have no idea what get_secret_flags is

---

### Post by afhx on 2014-07-22
Perhaps I should add that the suggested solution I gave earlier ( if it is a solution) is only a temporary solution until the next  boot-up. Somewhere a configuration needs to be altered.

---

