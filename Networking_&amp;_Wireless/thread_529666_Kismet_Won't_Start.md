---
title: "Kismet Won't Start"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by hutch346 on 2007-08-19
I've been trying to run Kismet but I keep getting this error message:

john@john-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (Atheros): Enabling monitor mode for madwifi_g source interface ath0 channel 6...
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: 'get_mode' does not return integer parameters.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

---

### Post by hutch346 on 2007-08-19
nvm solved it!

---

### Post by msjones on 2007-08-24
hi,

Im having the same problems. can you tell me how you got it solved?

thanks

mj

---

### Post by band-aid on 2007-08-24
post the contents of your kismet configuration file and I'll see if I can figure it out.

---

