---
title: "ADSL Modem D-link DSL 200 generation III"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by matteonwb on 2007-03-04
Someone can help me to install this modem?

---

### Post by matteonwb on 2007-03-08
Someone can help me?

---

### Post by zvacet on 2007-03-08
system>network setting>highlight your modem>properties>select type of connection>in upper left chek box>close
go>DNS>delete default and put your name servers>close
```
sudo pppoeconf
```

---

### Post by matteonwb on 2007-03-09
Tks for answer but I have usb modem... What I have to do?

---

### Post by dstath on 2008-01-04
I was able to install a D-Link 200 Generation III USB modem with Ubuntu gutsy
after spending several hours (or days?). The solution is simple.

The steps I followed are:

1.  download and install the driver from 
[http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php)

2. use the settings found in the eciadsl page
[http://eciadsl.flashtux.org/modems.php?modem=86](http://eciadsl.flashtux.org/modems.php?modem=86)

3. the trick is to note that LLC_SNAP_RFC1483_BRIDGED_ETH_NO_FCS
is not a mode to be selected for any provider. Rather it is 
provider depended. For my provider, aliceadsl in Italy, the 
setting that worked is VCM_RFC2364. One way to set this
is by trial and error as there are not many modes to test.

NB. 
a) gs7470_synch20.bin works fine. Initially I though that this was
the problem so i tested all the other .bin files and also built twice 
a new .bin file by sniffing my port in Win. I was not able to connect
because i always used LLC_SNAP_RFC1483_BRIDGED_ETH_NO_FCS
which as I realize now does not work with my provider.

b) for the record the values that I used to succesfully connect to 
AliceAdsl provided in Italy are the following:

Vid1/Pid1:	0915 / 8104
Vid2/Pid2:	0915 / 8104
Country:	italy
Provider(s):   AliceAdsl
VPI.VCI:	8,35
Synch .bin:	gs7470_synch20.bin
Chipset:	GS7470
Synch alt:	0
Pppoeci alt:	0
PPP mode:      VCM_RFC2364

---

