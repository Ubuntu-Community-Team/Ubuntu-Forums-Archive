---
title: "Ubuntu College Authentication Problem , LF SecureW2 alternative"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by d13k on 2008-01-26
My college requires authentication for network it's called securew2 which is available for Windows only .Using the basic google search I've found I can connect using wpa supplicant.
I tried numerous times to install it also tried switching to FedoraCORE 8 and OpenSUSE 10.3 but without success .
I've found tutorial that tell me to download wpa supplicant 0.4.9 from site ```
http://hostap.epitest.fi/releases/wpa_supplicant-0.4.9.tar.gz
```
and then unpack it
I used```
 tar -xvzf /etc/wpa_supplicant-0.4.9.tar.gz


```

then

```
cd wpa_supplicant-0.4.9
```

and then 

```
cp defconfig .config
```

and then I had to check if there is "#" in front of these commands located in defconfig

CONFIG_DRIVER_WIRED=y
CONFIG_IEEE8021X_EAPOL=y
CONFIG_EAP_TTLS=y

and then I am required to enter

```
make 
```

and 

```
make install 
```

but I get error

bash: make: command not found


I also tried using ```
ifup eth0
``` and ```
ifup dhcp
``` commands but without success

and I also tried changing my file wpa_supplicant.conf located in /etc/wpa_supplicant/
to

```
ctrl_interface=/var/run/wpa_supplicant

ctrl_interface_group=0

ap_scan=0

network={

key_mgmt=IEEE8021X

eap=TTLS

identify="USER"

password="PASS"

phase1="auth=PAP password=PASS"

phase2="auth=PAP password=PASS"

eapol_flags=0

}
```

If needed I can post screen shots too 
I am linux newbie so consider that when replying :D

I am trying to install this on laptop dell inspiron 6400
and I think I am using broadcom card can't remember exactly the name right now

P.S. I am trying to install this on Ubuntu 7.10

---

### Post by TuxBobble on 2008-02-04
I'm trying to find a way of doing the same thing.  My school's network uses SecureW2 with PAP.  I need to find a way to use it on the school's network if I want to use Ubuntu. If anyone could help, I'd greatly appreciate it.  I'm currently in Windows XP since that's the only way I can get a wireless connection on campus.

---

