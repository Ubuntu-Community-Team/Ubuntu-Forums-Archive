---
title: "Unable to Connect to Wireless Network"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by Mickey Zee on 2007-11-15
Hello all.  I am a complete newbie to Ubuntu and Linux.  I just installed v7.10 with a brand new Edimax EW7318 USB wireless adapter.  I bought this adapter specifically because it is supposed to run under Linux.  

When I go to the Network Manager, my wireless network SSID is detected (as well as my neighbor's 8-[) and the signal is strong.  I am using WEP security on the router (the only option available) and I am using the correct passphrase.  I also tried typing in the 26 hex digit key and neither works.

I ran _iwlist_ and came up with the following:

mike@mike-D410:~$ sudo iwlist wlan0 scanning
[sudo] password for mike:
wlan0     Scan completed :
          Cell 01 - Address: 22:A6:81:51:62:BF
                    ESSID:"Bay16St"
                    Mode:Ad-Hoc
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-26 dBm  
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000801cc767b

Can anyone explain to me how to get this working?  I love Ubuntu otherwise, but this is a show stopper for me, as I must have wireless access.

Thanks to all.

---

### Post by Triptol on 2007-11-15
You should be able to use the networkmanager applet in gnome to enter the key. Make sure you select the right kind of key (40 hex, 26 hex... etc.)

---

### Post by Mickey Zee on 2007-11-15
> **Triptol said:**
> You should be able to use the networkmanager applet in gnome to enter the key. Make sure you select the right kind of key (40 hex, 26 hex... etc.)

Did that....no luck.  I tried both the WEP 128-bit Passphrase and WEP 64/128-bit Hex options.

Thanks.....anything else to try?

---

### Post by edwardTheGreat on 2007-11-15
networkmanager applet should have a list of your connections.

If you select wireless and open the properties, 
then disable roaming mode, this will enable the options to enter all the settings into the networkmanager, 
enter the ESSID and the passphrase/hex key and go from there... then if it doesn't work straight away restart the computer or your networking

hope that helps...

EDIT: I posted this message just after you replied that you tried it from Triptol's message... sorry it didn't help... :oops:

---

### Post by Mickey Zee on 2007-11-15
> **edwardTheGreat said:**
> networkmanager applet should have a list of your connections.

If you select wireless and open the properties, 
then disable roaming mode, this will enable the options to enter all the settings into the networkmanager, 
enter the ESSID and the passphrase/hex key and go from there... then if it doesn't work straight away restart the computer or your networking

hope that helps...

EDIT: I posted this message just after you replied that you tried it from Triptol's message... sorry it didn't help... :oops:

Edward, I tried that, too......several times.

(sigh)

---

