---
title: "Recieve broadcast packets but not tcp packets"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by sumedhk on 2006-09-13
I connect to the net using ethernet. It was running fine couple of days back but now i cannot ping my gateway. The status of the connection says connected but i cannot ping anyone. Note it says that in windows, in ubuntu it says destination host unreachable.

I installed ethereal and observed that i can recieve broadcast packets like osp, arp, stp etc but not a single tcp packet.

the technician from my isp came to my place today, he tested the cable in a cable tester which displayed that out of the 8 wires inside a lan cable, wires
2 - 8 wires were good but wire 1 was not. He said that he will have to change the ethernet cable which would take atleast 5 - 10 days.

Now i know that out of 8 wires only 4 wires are used in an ethernet lan. What i want to know is that can i swap the wire which is damaged with a wire which is not used. Will this work. Do we need all the 8 wires working properly for an ethernet lan to work


PC - Straight Cable- - Switch

Pin 1 TX+ -------------- Pin 1 RX+
Pin 2 TX- -------------- Pin 2 RX-
Pin 3 RX+ ------------- Pin 3 TX+
Pin 6 RX- ------------- Pin 6 TX-

---

### Post by tbonius on 2006-09-13
I dont know why it would take 5 days to switch out an ethernet cable whene you can simply run down to Radio Shack or CompUSA or wherever.. and buy one yourself.  Make sure and check if it is a crossover cable.. and if youre not entirely sure.. just buy one of each.

T

---

