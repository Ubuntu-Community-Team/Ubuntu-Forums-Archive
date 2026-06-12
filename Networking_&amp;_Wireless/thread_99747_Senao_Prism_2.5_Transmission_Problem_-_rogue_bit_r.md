---
title: "Senao Prism 2.5 Transmission Problem - rogue bit rate"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by wleung on 2005-12-06
Dear Reader,

                 I'm currently doing a little bit of research and attempting to measure the range of transmission with different bit rates. Using ubuntu breezy, being relatively easy to install, i've used:

apt-get install hostap-utils, hostapd

to get the Senao NL-2511CD PLUS EXT2 card automatically configured to use the hostap drivers.
Link to website of card here: [http://www.senao.com/english/product/product_wireless01_outdoor_1.asp?pgtl=Wireless&tp1id=02&tp2id=07&proid=000033](http://www.senao.com/english/product/product_wireless01_outdoor_1.asp?pgtl=Wireless&tp1id=02&tp2id=07&proid=000033)

I've checked with lsmod. And the orinoco drivers have been replaced by hostap.
                  I've been attempting to force the card to try and transmit at either of the 1Mbps, 2Mbps, 5.5Mbps rates that the cards support, however the bloody thing sneakily changes to 11Mbps and transmits at highest rates, and then when finished switches back to my predefined bit-rate.

                  I'm using the Ad-Hoc mode via:

iwconfig eth2 mode Ad-Hoc

I've used:
iwconfig eth2 rate 1M         // as well as 2M and 5.5M
iwpriv eth2 oper_rates 1     // as well as 2 and 4

iwconfig reports that the bit rate has changed, but when using iperf or bing to send data, using iwconfig in parallel - it can be seen that the card gets changed to 11Mbps before transmission, and when finished, changes back to the setting I set it onto. Making my attempts to control Transmission rate useless.

             When trying to set the 'fixed' command in iwconfig, the iwconfig package just screws up:

iwconfig eth2 mode fixed

             after running the above - the iwconfig gets changed in someway and complains of mixmatched compiler versions. And I have to reboot to recover.

Can anyone provide an explanation as to what I am doing wrong?
Replies would be greatly appreciated.

Cheers,
Wilson

---

### Post by wleung on 2005-12-06
Ohh, in addition a hypothesis...

Is it another process that linux/ubuntu is running that is causing the bit rate to change prior to sending of data?

I'm not at the computer used in tests at the moment, but I am *wishing* that by monitoring what processes are using the CPU to see if there is another user level process changing the bit-rate.

Cheers,
Wilson

---

