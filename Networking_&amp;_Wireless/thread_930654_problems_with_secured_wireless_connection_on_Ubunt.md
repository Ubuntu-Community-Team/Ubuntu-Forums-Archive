---
title: "problems with secured wireless connection on Ubuntu 7.10 gutsy"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by Barbelo on 2008-09-26
Hi,
 I have a bit of a problem connecting to the secured wireless connection. 
the main problem is that the computer says it is connected. it detects the belkin usb adapter and the connection I have already set up the key using both the network manager and the terminal. I used this 
sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid “ESSID_IN_QUOTES”
sudo iwconfig [interface] key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed -- sudo iwconfig [interface] key open <<<----See note below
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]
and it gave me the answer it should.
BUT when I open firefox it doesnt download any website and it logs in to yahoo messenger, I receive messages but most of the time the other person doesnt receive the messages that i send.
msn doesnt log in. 
the other computers of my housemates have no problem with the connection so it is not problem with the router. 
I have no clue what else i can do. Please HELP!!!
thanks

---

### Post by superprash2003 on 2008-09-26
in your terminal type ping google.com and post output

---

