---
title: "Random Network Shutdowns"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by idtt2s on 2007-07-06
I have a 3Com card that would normally use the 3c59x driver. My network shuts down randomly and I cannot seem to bring the network back up through "/etc/init.d/networking restart" or through direct usage of dhclient. Those are the only two ideas I can think of, even though they are basically the same. 

I don't know what to include but this is my dmesg after a shutdown.

[22549.409102] NETDEV WATCHDOG: eth0: transmit timed out
[22549.409111] eth0: transmit timed out, tx_status 00 status e000.
[22549.409119] diagnostics: net 0cc0 media 8802 dma 00a00021 fifo 8800
[22549.409125] Flags; bus-master 1, dirty 1762849(1) current 1762865(1)
[22549.409129] Transmit list 1db432a0 vs. ddb432a0.
[22549.409133] 0: @ddb43200 length 8000004a status 8000004a
[22549.409136] 1: @ddb432a0 length 8000004a status 0000004a
[22549.409139] 2: @ddb43340 length 8000004a status 0000004a
[22549.409141] 3: @ddb433e0 length 8000004a status 0000004a
[22549.409144] 4: @ddb43480 length 8000004a status 0000004a
[22549.409146] 5: @ddb43520 length 8000004a status 0000004a
[22549.409149] 6: @ddb435c0 length 8000004a status 0000004a
[22549.409151] 7: @ddb43660 length 8000004a status 0000004a
[22549.409154] 8: @ddb43700 length 80000084 status 00000084
[22549.409157] 9: @ddb437a0 length 8000004a status 0000004a
[22549.409159] 10: @ddb43840 length 8000004a status 0000004a
[22549.409162] 11: @ddb438e0 length 8000004a status 0000004a
[22549.409164] 12: @ddb43980 length 8000004a status 0000004a
[22549.409167] 13: @ddb43a20 length 8000004a status 0000004a
[22549.409170] 14: @ddb43ac0 length 8000004a status 0000004a
[22549.409172] 15: @ddb43b60 length 8000004a status 8000004a
[22549.409177] eth0: Resetting the Tx ring pointer.
[22550.656043] eth1: no link during initialization.
[22550.656597] ADDRCONF(NETDEV_UP): eth1: link is not ready
[22559.390902] NETDEV WATCHDOG: eth0: transmit timed out
[22559.390911] eth0: transmit timed out, tx_status 00 status e000.
[22559.390919] diagnostics: net 0cc0 media 8802 dma 00a00021 fifo 8800
[22559.390925] Flags; bus-master 1, dirty 1762849(1) current 1762865(1)
[22559.390929] Transmit list 1db432a0 vs. ddb432a0.
[22559.390933] 0: @ddb43200 length 8000004a status 8000004a
[22559.390936] 1: @ddb432a0 length 8000004a status 0000004a
[22559.390939] 2: @ddb43340 length 8000004a status 0000004a
[22559.390941] 3: @ddb433e0 length 8000004a status 0000004a
[22559.390944] 4: @ddb43480 length 8000004a status 0000004a
[22559.390946] 5: @ddb43520 length 8000004a status 0000004a
[22559.390949] 6: @ddb435c0 length 8000004a status 0000004a
[22559.390951] 7: @ddb43660 length 8000004a status 0000004a
[22559.390954] 8: @ddb43700 length 80000084 status 00000084
[22559.390956] 9: @ddb437a0 length 8000004a status 0000004a
[22559.390959] 10: @ddb43840 length 8000004a status 0000004a
[22559.390962] 11: @ddb438e0 length 8000004a status 0000004a
[22559.390964] 12: @ddb43980 length 8000004a status 0000004a
[22559.390967] 13: @ddb43a20 length 8000004a status 0000004a
[22559.390969] 14: @ddb43ac0 length 8000004a status 0000004a
[22559.390972] 15: @ddb43b60 length 8000004a status 8000004a
[22559.390976] eth0: Resetting the Tx ring pointer.

---

### Post by idtt2s on 2007-07-08
Too soon for a bump? Sorry, but this is really bugging me.

---

