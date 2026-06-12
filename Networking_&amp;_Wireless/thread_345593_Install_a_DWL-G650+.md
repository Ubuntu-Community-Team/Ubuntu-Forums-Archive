---
title: "Install a DWL-G650+?"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by coral on 2007-01-24
Hello, i searched all over the place, but i havent found a guide that tells me HOW to install a wireless card (just configure the encryption). So may please someone guide me trough the steps of a PCMIA DWL G650+ Rev: B1

I would certainly appreciate it :D

/Coral

---

### Post by VorDesigns on 2007-01-24
Hi,

Depending on what flavor you have installed, there are different avenues of approach.
Also, what kind of security the wireless access point you are connecting to affects things as well.
I have been trying for a couple of weeks to get Dapper 6.06 to work with my older DWL-G650 card.
In Dapper the card was recognized and some form of MadWiFi is installed that allows communication with the card but I was never able to get the card running through the Networking applet in the System --> Administration menu.
That being said, I was able to register my card with a specific access point and get an IP from the firewall located on the wired segment of my network.
Part of what follows may not be necessary but this is my journey.
First I tried using the Networking applet which recognised my card as ath0
I edited my interfaces for ath0 as follows:  I used sudo gedit /etc/network/interfaces from a command line (terminal window)
auto ath0
iface ath0 inet dhcp
## Added as per other posts but the value of this is unknown
pre-up ifconfig ath0 up
pre-up ifconfig ath0 down
pre-up ifconfig ath0 up
## Added as per other posts
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
## Added by the Network applet but it doesn't work
wireless-key <my_secret_code_was_here_> // put yours in place
## Added as per other posts to identify the access point I want
wireless-ap <MAC_Address_of_my_AP> // put yours in place
## on the channel it uses
wireless-channel 9
## by the name I gave it
wireless-essid my_ap_name // put yours in place
## in the manner it communicates
wireless-mode managed

I still couldn't get connected.

Finally, after I boot, I run the following in a terminal window

## This tells the secret code that should be loaded already
sudo iwconfig ath0 key <my_secret_code_was_here_> // put yours in place
## This tells the authentication mode 1 for open, 2 for Shared key
sudo iwpriv ath0 authmode 2
## Now that the ap and ath0 should be talking, ask for an IP
sudo dhclient ath0

At some point I will figure out how to script this and have the system load it automatically.

Clearly there has to be a better way but I don't know.

---

### Post by VorDesigns on 2007-02-18
I created the script I was talking about
open your favorite edit and add

```
#!/bin/bash
iwconfig ath0 key <your_secret_code_goes_here_>
iwpriv ath0 authmode 2
dhclient ath0
```

Save the file
change the file properties 

sudo chmod 755 <your_file_name>

run the file as sudo.

I tried adding this to my interfaces file but it didn't work no matter what I tried.
It does make getting the card going easier once I have logged in.

---

### Post by Cippa Lippa on 2007-03-16
Hi VorDesigns

I have your same problem with my DWL-G650 that I just bought. How should I modify your script if I just need to connect to open and unprotected wireless networks. I do not have a IP, password, nothing. Just using a downtown-wide open wireless broadband connection we have here in Toronto...

Thanks for replying

Cippa Lippa

---

