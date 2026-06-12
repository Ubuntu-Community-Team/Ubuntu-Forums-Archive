---
title: "Wireless card keeps disconnecting and then reconnecting"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by GregoryMA on 2007-08-08
My wireless connection keeps disconnecting and then immediately reconnects.  I am using a netgear wg511t nic.  Here is iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"default"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:46:A5:01:5A   
          Bit Rate:5 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=16/94  Signal level=-77 dBm  Noise level=-93 dBm
          Rx invalid nwid:154  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by sfarber53 on 2007-08-08
Are you running any sort of encryption?  Have you tried running only with MAC ACL enabled and MAC addresses?

- Steve

---

### Post by GregoryMA on 2007-08-09
I am pretty sure I am not using encryption.  I am far from a wireless expert though and I don't know though.  How do I check these three things?

---

### Post by buntunub on 2007-08-09
run in terminal 

$iwlist scan

That will show you all the networks that your wireless card sees, including your own, and the encryptions they are running. What you need to know when connecting to an access point is a) is it encrypted (WEP, WPA, etc), and b) what do I need to have handy to get into it (encryption keys, passwords). If you are trying to get into WPA, you can generate the key with 

$wpa_passphrase essid password

Where essid is the essid of the router, and password is the encrypted passphrase that its running. You must have both of those. Then just copy and paste in the string that command generated. After you do that the first time, your keyring should then activate and store it for you. Each time you reboot or boot back in, its going to ask you for your keyring password to access that router again, because the router will request the encryption key from the keyring manager. On the same session, it should not ask for keyring passwords again if you lose your connection and reconnect again.

---

### Post by GregoryMA on 2007-08-12
Here is iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:13:46:A5:01:5A
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/94  Signal level=-74 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

I don't think it is a problem with encryption because I have just started having troubles with this but nothing to do with my networking has changed in a while.  Also after start up it works reasonably well but then performance degrades with time.

---

