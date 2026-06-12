---
title: "Forward TCP Port to Serial RS232"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by ralyon on 2008-06-09
I'm looking for a way to forward a TCP port (IP:1234) to a serial port (ttys0). I have a linux pc with a 9 pin serial port which I would like to connect to using [TCPCom]("http://www.taltech.com/products/tcpcom.html") on windows creating a virtual com port which provides a pass through to the serial port on the linux box?

Does anyone know of a way to do this? I'm hoping there is a simple solution I'm just not seeming to be able to put my finger on it.

Thanks for your help,
ralyon

---

### Post by TheLocalGraveDigger on 2008-06-09
i think you need to setup a TCP/IP suite on the serial connection to do that.if anyone knows how to do that please help us.

---

### Post by sockmonkee on 2008-10-15
if I understand you correctly you want to connect a serial port (say /dev/ttyS0 ) to a tcp port?

This can be done quite easily with socat, I think the command should look something like:

socat STDIO:/dev/ttyS0,nonblock,raw,echo=0 TCP-LISTEN:1234

which would connect the serial port to tcp port 1234

---

### Post by ralyon on 2008-10-15
Thanks for the info. I hope to be able to use it someday, but unfortunately I lost that job so I won't have a chance to test it.

ralyon

---

