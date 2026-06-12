---
title: "Serial port"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2009-01-24
Hi
I'm trying to use minicom to communicate with a GPRS Modem on serial port 2.  I installed minicom, but just can't communicate with GPRS Modem.

Am I using good software ?
How can I start minicom and specify to work on com-2 ? (found nothing in CTRL-A-Z)
What is ssty for ?
How can I see if GPRS Modem is alive on com-2 ?

Thanks

---

### Post by Pierrot Lafouine on 2009-01-24
up

---

### Post by Pierrot Lafouine on 2009-01-25
Hi
I'm trying to use minicom to communicate with a GPRS Modem on serial port 2. I installed minicom, but just can't communicate with GPRS Modem.

Am I using good software ?
How can I start minicom and specify to work on com-2 ? (found nothing in CTRL-A-Z)
What is ssty for ?
How can I see if GPRS Modem is alive on com-2 ?

Thanks

---

### Post by ModelM on 2009-01-25
First of all, com-1 in Linux is /dev/ttyS0, com-2 is /dev/ttyS1.

Second, you might install cutecom & have a look at that. It might suit your needs better than minicom.

---

### Post by The Cog on 2009-01-25
You may also want to look at gtkterm.

Note that /dev/ttyS1 has a capital S.

---

### Post by Pierrot Lafouine on 2009-01-25
Tanks all, but in fact I need to interface COM-2 with command line application.
My final target is to run a Python script that will access GPRS Modem on COM-2.

Any idea on how I can configure minicom (or other application) to use COM-2
?

Thanks

---

### Post by ModelM on 2009-01-25
Try

sudo minicom -s

to configure minicom initially. After that

minicom

should bring it up working as you wish.

---

### Post by The Cog on 2009-01-25
Yup. run **minicom -s** to get the configuration screen up (or start minicom and type **Ctrl-A O** then use the arrow keys and enter to go to the serial port setup. **COM2** should be device **/dev/ttyS1**. It may help to turn all flow control off to start with. I tried minicom on intrepid only this afternoon. It works fine.

---

### Post by Pierrot Lafouine on 2009-01-25
minicom freeze when started with 9600 N81 controls OFF
... 
hummmmmm, any other serial com application (command line) ?

Thanks

---

### Post by Pierrot Lafouine on 2009-01-25
After more test, look to me modem is dead
Thanks

---

### Post by The Cog on 2009-01-26
Minicom doesn't freeze for me. I tested it by shorting pins 2 and 3 (transmit and receive) of the connector together (using a kitchen knife - I was at the kitchen table). When I short the pins together, I can see my typing appear on the screen. This only works if you turn hardware flow control off.

---

