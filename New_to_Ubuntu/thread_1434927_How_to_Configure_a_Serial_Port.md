---
title: "How to Configure a Serial Port"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by ESimard on 2010-03-20
Hi, complete newbie here.  I need to set a serial port, (for some legacy device)perminately to 19,200 baud with hardware flow control.  I see that a program call setserial might do the trick but shied away after reading the complicated install instructions.  Is there some other program or procedure I can use?  I do not need it at boot time so Grub doesn't need to be changed, I think?  Nor will it be used for internet access as it not a modem.  Just after the system is up and the legacy device is connected.

ubuntu 9.10
Thanks in advance
Ernie

---

### Post by relay_man on 2010-03-21
Hi Ernie
To make serial communication a little easier, you might try Gtkterm.
It can be downloaded from the repositories using your package manager.
It is has several good features without being complicated, a clean
graphical interface, and is rather simple to setup and use.
I use it to communicate with some older ham radio equipment, some commercial
radio devices and my oscilloscope.  It works really well for me.

---

### Post by luttermann on 2010-03-21
What kind of device is it? how do you need to communicate with it? I personally use minicom for serial terminals and modems. And cat for reading from a dumb terminal on a UPS, but serial communication is a vast subject...

---

### Post by ESimard on 2010-03-21
Hi, it's a device that enables two way communication with a model railroad.  It's called a LocoBuffer.  I would like to permanently configure a port to its requirements.

I'll try the above mentioned program and see if will work.

Thanks for the help _Ernie

---

### Post by ESimard on 2010-03-21
Hi, I tried Gtkterm and it shows that four ports are available:
/dev/ttyS0, S1, S2, and S4.  But there are only two ports installed on my system?

lspci does indeed show only two ports.  When I attempt to configure the legacy device (Locobuffer) it tells me that no ports are configured.

lspci -vv shows the two ports but after Capabilities: is says <access denied>.  Could this be the problem? If so how do I gain access?  Also it appears that Gtkterm only defines the port while the program is running.  How do I make the port setting permeate?

Still a bit lost
Thanks _Ernie

---

### Post by ESimard on 2010-03-22
Hi again.  I found on the install disk drivers for Linux.  The directions include the use of the "make install" command.  Would this be the same for ubuntu?  That is can I follow the Linux directions the same way?

Thanks Ernie

---

### Post by ESimard on 2010-03-22
Hi, tried the Linux instructions and still the ports are not available/configured.  Has anybody installed the Moschp MCS9865 software.  I'm in a complete loss as to the problem.

Thanks Ernie

---

### Post by janiskracht on 2010-10-11
Hi there,

The 9865 is working well over here with my U.S.Robotics external V.Everything modem..

I downloaded the most recent driver  (I think it was from 2009) I could find at MosChip's site for the 9865 card. [www.moschip.com](www.moschip.com).. the install was pretty easy.  I already had the kernel set with CONFIG_SERIAL_8250 ( it was compiled as as inbuilt (=Y) in .config file of kernel 2.6.28-16-server.)

I used the instructions  in the PDF file, essentially 'make' and 'make install' once I had the files in /root's desktop directory.  

I'd originally installed the internal Conexant modem in my Dell 64bit system, but it seemed to be interfering with my wireless keyboard and mouse, so I really wanted this MosChip port to work :)  I'm a happy user now (grin)

Janis

---

### Post by HermanAB on 2010-10-11
Howdy,

The easiest way to configure a serial port is with Cutecom.  It should be in the repos, otherwise, you can also use minicom, but it is a bit archaic.

---

