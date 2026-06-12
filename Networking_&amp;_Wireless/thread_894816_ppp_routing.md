---
title: "ppp routing"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by mack_psu on 2008-08-19
I am having trouble setting up a ppp route.

here is my situation...

i have set up a ppp connection between two linux pc's with these addresses, and i want to bridge two lan's across the ppp connection.

linux box A: eth0:192.168.0.10, ppp0:192.168.1.2

connect to 

linux box B: eth0:192.168.5.22, ppp0:192.168.2.1

attached to linux box A via ethernet crossover cable is a windows pc with ethernet address 192.168.0.11.

similarly, attached to linux box B via ethernet crossover cable is another windows pc with ethernet address 192.168.5.51.

complete picture
win(*.*.0.11) <--ethernet--> (*.*.0.10)eth linux ppp(*.*.1.2) <--serial-->ppp(*.*.2.1) linux eth(*.*.5.22) <-> win(*.*.5.51)

essentially i want to ping from one windows pc to another...
192.168.0.11 <---> 192.168.5.51.

the ppp command line i use is the following...

linux box A:
pppd nocrtscts lock local nodeflate persist maxfail 0 192.168.1.2: /dev/ttyS0 115200 &

linux box B: 
pppd nocrtscts lock local nodeflate persist maxfail 0 192.168.2.1: /dev/ttyS0 115200 &

also on windows box A, the eth address is 192.168.0.11 with gateway of 192.168.0.10 (linux box A)

and on windows box B, the eth address is 192.168.5.51 with gateway of 192.168.5.22 (linux box A)

i can get the windows pc attached to linux box A to ping its ppp address (192.168.1.2) and eth address (192.168.0.10)

but i cannot get it to ping the other ppp address (192.168.2.1)

i think i either have a ppp loop or need to add some static routes to the routing tables, but am not sure what to do...

thanks in advance for help.

---

