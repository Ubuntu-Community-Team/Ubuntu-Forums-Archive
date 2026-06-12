---
title: "WPA with Fiesty Fawn Issues"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2007-05-17
I have been able to get unsecured wireless going, but not able to get WEP or WPA running at home with a Dell Latitude D505 with the Intel 2100 3B Mini PCI using ipw2100 for the driver.  It tries to connect, then it says "Waiting for Network Key", then it stops with no network connection.

This is a clean Fiesty Fawn install and wpasupplicant has already been loaded.

WEP hooks up, works for a few, then disconnects.  Any help greatly appreciated.

Thanks

---

### Post by epee on 2007-05-18
You'll need to supply more info - e.g. what you've got in /etc/network/interfaces and the wpasupplicant conf file, for example. You might also look at the output from 'iwconfig' and 'iwlist scan'.

Without more specifics, no one is able to help you. Just look at the vast number of threads here - information is always the key.

Also, by reading through many relevant threads, you'll be surprised that you might even find the answer yourself!

---

### Post by matthewboh on 2007-05-18
I was able to fix this after a lot of playing around - I did a clean install and commented out all of the entries in /etc/network/interfaces EXCEPT for the lo lines BEFORE I tried Network Manager.  I then started Network Manager, let it do it's stuff and everything worked.  If I waited to comment these lines after I first tried Network Manager, it would never work.  Is there a way to suggest to the Ubuntu folks to set up the install so that these lines are commented out?

---

### Post by stuker on 2007-05-20
hi

i am also having an issue connecting to my wireless router since changing the encryption protocol to WPA(tsk) from WEP.  All was OK in WEP BTW.  The driver seems to be working  and below is the output from iwconfing and iwlist

root@lappy:/etc/network# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"stuker"  Nickname:"stuker"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:7369-6E65-6164-6479-6C00-0000-00   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@lappy:/etc/network# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:B7:8B:73
                    ESSID:"stuker"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-28 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 24ms ago

---

### Post by stuker on 2007-05-20
i think i have sorted this out now using wpa supplicant but i am wondering where i add the wpa supplicant command line so that it is always used by the network card?  i.e so that i dont have to run it manually from the command line

---

### Post by matthewboh on 2007-05-20
I was able to connect to WEP, but unable to change a named/found network from WEP to WPA.  However, with the clean install and the updates to /etc/network/interfaces file BEFORE I tried to connect worked effortlessly.  Maybe you can just uninstall then re-install NetworkManager?

---

### Post by stuker on 2007-05-20
well its working with wpa supplicant bur i need to add some lines to the /etc/network/interfaces file.  just trying to determine what these lines are for fiesty

---

### Post by matthewboh on 2007-05-24
Sorry - got sidetracked for a few days.  Anyway, here's the content of my /etc/network/interfaces file.  Like I said, if I commented out everything before running NetworkManager - it works great.  Hope this helps.

```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

---

