---
title: "Help - to set up an ADSL connection"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by joel85 on 2007-02-07
Hi I'm an advanced user in windows, but a newbie to Ubuntu. I recently downloaded and installed the Ubuntu 6.10 Edgy, my conextant accessrunner ADSL modem has been detected by ubuntu and the network light is on (steady-meaning network connection established with modem) but my problem is (please dont think i'm stupid) I dont know how to set up the ADSL connection and input the connection parameters like

VPI
VCI
Handshake Protocol
Encapsulation
Username
Password
Dial Number

please tell me how to do this and to set it up in ubuntu desktop or to make ubuntu connect at start-up....
Please Help!- I'm in a desperste situation

Thank you.....

---

### Post by gradedcheese on 2007-02-07
This might help:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29)

---

### Post by joel85 on 2007-02-07
Hi thanks for the advice gradedcheese, well i tried out wat is given in the link u provided... but wen i run the command ```
wget -c /home/desktop/rp-pppoe-3.8.tar.gz 
``` terminal says unsupported scheme....

any ideas why? please help

many thanks

---

### Post by gradedcheese on 2007-02-07
hmm, looking at the guide I see that the command is actually:

```

wget -c [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)

```

By the way, what that does is: go and download the file at this URL, and put it in my current working directory.  The next command uncompresses it, and so on.  If you want, just right-click the link and Save-As to the Desktop.  Then in the terminal "cd Desktop" and continue from there.  Don't forget to install build-essential as they suggest before you get too far:

sudo apt-get install build-essential

---

### Post by joel85 on 2007-02-07
> **gradedcheese said:**
> hmm, looking at the guide I see that the command is actually:

```

wget -c [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)

```By the way, what that does is: go and download the file at this URL, and put it in my current working directory.  The next command uncompresses it, and so on.  If you want, just right-click the link and Save-As to the Desktop.  Then in the terminal "cd Desktop" and continue from there.  Don't forget to install build-essential as they suggest before you get too far:

sudo apt-get install build-essential

hi, i was sucessful in installing build-essential
but when i was installing rp-ppoe-3.8
on the last step (gksudo gedit /usr/share/applications/RP-PPPoE.desktop)
i encountered the following error message...
```

joel@joel-desktop:~$ gksudo gedit /usr/share/applications/RP-PPPoE.desktop
(gedit:8952): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```
please help me to figure out how to correct this, otherwise i [B]cannot connect to internet....
everytime i'm reebooting to windows to ask help in this forum...

[/B]

---

### Post by gradedcheese on 2007-02-07
Actually that's not an error, you can just continue using gedit.

---

### Post by joel85 on 2007-02-08
thanks alot ill follow it up....

---

