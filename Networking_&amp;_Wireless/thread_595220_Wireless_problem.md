---
title: "Wireless problem"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by gatorbowls on 2007-10-28
I Am testing out ubuntu (the newest one)
I have a acer 5050  laptop thats wifi.
It has a  802.11/b/g WIRELESS LAN.
I can't seem to get the wireless to work..

---

### Post by gatorbowls on 2007-10-28
Hmm any solutions anyone?

---

### Post by jml on 2007-10-28
More specific information will be needed in order for someone to help you.  If you have not yet done so, review the five "sticky" threads posted at the top of this sub-forum.  There is a lot of information there that can be of help to you.

When you say you are using the latest version of Ubuntu, just to be clear, you mean version 7.10, Gutsy Gibbeon?

When you say wireless does not work, can you please be more specific?  Is the wireless card detected?  If it is, does it see nearby wireless networks?  If it does, can you connect to unencrypted networks?  Encrypted ones?

Second question, the Acer 5050, according to their web site uses something called an Invilink 802.11 b/g mini-pci wireless card.  I have not been able to determin precisely what chip set it uses.  If your wireless card is not even being detected, then you will need to find out what wireless chip set your card uses.  That information may be included in the documentation that came with your laptop.  If you still have windows installed on your laptop, you can use the hardware utility to find out the specifics of your wireless card.  If you already have Ubuntu up and running, either as a live CD or HD install go into a terminal and type the following commands and post the output here on this forum.

lspci
ifconfig
iwconfig

There will be a lot of output from these commands.  Search for reference to wireless devices.  If you are lucky, one of these commands will allow you to identify what chipset your wireless card uses.  Good luck.

Joe

---

### Post by gatorbowls on 2007-10-28
Yes My wireless is on..and it's by my wireless router...and it's not getting the singal somehow..
My nehobor's have wifi too..and im not picking there's up either..
And yes Im using 7.10

I hope this helps.

---

### Post by gatorbowls on 2007-10-28
And on ubuntu it shows that there is no signals avaible.

---

