---
title: "poor reception using Restricted Wireless Driver"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by linux8654 on 2007-08-03
I installed a wireless card with an Atheros chipset

lspci as:
03:00.0 Ethernet controller: Atheros Communications, Inc. [COLOR="Red"]AR5212[/COLOR] 802.11abg NIC (rev 01)

 I am using the Restricted driver,  Atheros Hardware Access Layer (HAL)

When my computer is 3 feet away from the wireless router, my reception is never greater than 28%,  if I move more than 5 feet from the router I can not establish any connectivity.  After reading through several posts, I believe I need to get a different wireless driver to fix this problem.  I am familiar but not proficient with linux, and am looking for some help finding and installing an appropriate wireless driver.

Thanks for any help,

linux8654

---

### Post by webjames on 2007-08-07
THIS IS NOT AN ANSWER

i have been watching this post for a couple of days now, no answer. i have exactly the same problem, except my signal strength does not change at all even if i put my laptop right next to the router.

lspci gives:
...
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
...

my laptop is a thinkpad t41 with a IBM card inside:[http://www.thinkwiki.org/wiki/IBM_11a/b/g_Wireless_LAN_Mini_PCI_Adapter](http://www.thinkwiki.org/wiki/IBM_11a/b/g_Wireless_LAN_Mini_PCI_Adapter)

if anyone has the same card, but with a working signal strength thing, please post.

many thanks

---

### Post by webjames on 2007-08-07
UPDATE!

I am now using the madwifi OpenHal driver: see screenshot, i'm not sure why it appears in the restricted driver management; the restricted driver has disappeared.

to do what i did: 
```
sudo apt-get install subversion
svn checkout http://svn.madwifi.org/branches/madwifi-old-openhal madwifi
cd madwifi
make
sudo make install
cd openhal
make
sudo make install

```
when asked about removing a module just press 'r' then enter, and then restart. well that worked for me


see [http://madwifi.org/wiki/OpenHAL](http://madwifi.org/wiki/OpenHAL) for more details or the README in the madwifi/openhal dir

as for signal improvements, i think i am getting around the same strength; but i now have a better speed 54mbps, rather than 48mbps.

tell me your experiences...

---

### Post by webjames on 2007-08-07
this may be helpful:

```
james@james-laptop:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:0F:66:C9:49:62
                    ESSID:"DD-WRT"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=50

```

---

### Post by webjames on 2007-08-08
update......

well after testing the openhal i decided to use the old, non-free, madwifi driver, but i installed it myself from the madwifi site. i un-installed the restricted driver first along with the manager. seems to be working now.

i think i'll let openhal mature a bit before i try it again.

as for the signal no improvements, well maybe slight, but the signal now gets better the nearer i get teh the router. to a maximum of 65% when my laptop is within inches. still a bit weird but it's working.

---

### Post by linux8654 on 2007-08-08
I successfully installed the MADWIFI driver, however my poor reception problem remains the same.

---

### Post by webjames on 2007-08-09
the last thing which i want to try,  but cannot is to install windows and see if my reception increases. i think the only way to do this as windows signal strength might be inaccurate. i think if you went right the the edge of your signal range, then tested it on windows and see if you still just about got reception then you'd know if it's a driver issue.

---

### Post by splintercellguy on 2007-08-09
Could the OP's issue simply be that the card reports an inaccurate strength value?

---

### Post by webjames on 2007-08-09
perhaps, mine to, as it should be above 60% when next to the router!

---

### Post by moron on 2007-08-10
Where are you getting this percentage value from?  

The "quality" value shown via "iwlist scan" is *not* a fraction despite looking like one. I believe that it is showing the distance between the noisefloor and the signal strength (level=-72 dBm  versus Noise level=-95 dBm). 

For example:

Quality=23/94

is within normal limits and should allow a decent connection.  If memory serves, 20 is OK, 40 is amazing and I think somewhere around 60 is the theoretical maximum.  

If you are talking about some other tool (network manager?) then the strength percentage is pretty much meaningless since we have no idea how they are calculating it. 

Cheers

---

