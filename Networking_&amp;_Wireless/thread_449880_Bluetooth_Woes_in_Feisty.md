---
title: "Bluetooth Woes in Feisty"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by delphiguy on 2007-05-20
Cheers,

I've posted this on the Absolute Beginner Talk Forum, but I think this is a more
proper forum for my problem.

Im trying to make bluetooth work in Feisty but I seem to have hit a brick wall.
When I try to connect from my CellPhone to my PC, my CellPhone asks for
a PIN, so I type in 1234 which is I think the default but all I got is
"Unable to pair. Try Again?" so I tried 0000 for the PIN and still I get the same error
"Unable to pair. Try Again?".

And when I looked at /etc/bluetooth/hcid.conf it says that passkey is indeed "1234".

And when I try to initiate the connection from the PC, my CellPhone asks for a PIN so I
typed in 1234, but Ubuntu gives me this error "Unable to connect to remote device."
and my CellPhone also gives me this error "Invalid Pin".

Any ideas on how to solve this??

My CellPhone is Samsung SGH-X820.

Thanks.

---

### Post by gregh on 2007-05-21
I have the same issue with a Nokia 6300 if anyone has solved this.

-Greg

---

### Post by taxone81 on 2007-05-21
Same problem with nokia 6680

---

### Post by delphiguy on 2007-05-22
no takers??

---

### Post by yngvestein on 2007-05-22
ditto on SE W810i... Guess it's a pretty common problem...

---

### Post by delphiguy on 2007-05-23
I finally got it working.  I dont know how or why, but maybe just maybe it has something to do
with something I did with synaptic.

I installed everything that has blue or bluez or something that remotely resembles bluetooth
(at least in my mind).

And after a restart of Ubuntu, I got a nice Bluetooth logo in my tray, and bluetooth now works.

---

### Post by Ivo Moelans on 2007-05-23
I have a Treo 650 and a dongle. Both are recognized correctly but I can't get them working. I get the following error message:
** (gnome-obex-server:9928): WARNING **: OBEX server register error: -1

** (gnome-obex-server:9928): WARNING **: Unable to initialize OBEX source

** (gnome-obex-server:9928): WARNING **: Couldn't initialise OBEX listener

Anybody any suggestions?

---

### Post by wigglydiggly on 2007-05-27
> **Ivo Moelans said:**
> I have a Treo 650 and a dongle. Both are recognized correctly but I can't get them working. I get the following error message:
** (gnome-obex-server:9928): WARNING **: OBEX server register error: -1

** (gnome-obex-server:9928): WARNING **: Unable to initialize OBEX source

** (gnome-obex-server:9928): WARNING **: Couldn't initialise OBEX listener

Anybody any suggestions?


I got the same message too.  I believe its because the service is already running.  Do you have bluetooth file sharing already running?  I closed that and than ran gnome-obex-server in terminal and recieved this when trying to scan for services availible on Ubuntu.  Not sure what to do next though.

$ gnome-obex-server
conn_request:   bdaddr 00:09:2D:33:2F:AE
conn_complete:  status 0x00

---

### Post by ssong on 2007-05-29
If memory serves, you need to completely purge your bluetooth packages and re-install them.  Something like 

"aptitude purge [insert bluetooth packagenames]" 

and then reinstall them.  That worked for me.

---

