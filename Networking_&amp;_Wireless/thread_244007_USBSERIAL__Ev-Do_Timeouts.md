---
title: "USBSERIAL / Ev-Do Timeouts?"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by Major_Imbu on 2006-08-25
Thanks to the many postings on this topic I was able to quickly get my Xubuntu (Drake) system up and running with my PCMCIA Sprint Ev-Do card.  I get similar throughput with like signal to my MacOS or WinXP setup, so that's great.

What isn't working so hot it are unexpectedly dropped connections after a few minutes (but seemingly random) that don't really feel like timeouts (since I'm sending packets continuously and have artificially high timeout values).  Each time I can successfully reconnect by running:

sudo /etc/wvdial sprint

Apart from "PPP daemon has died"..."(exit code 15) I'm not seeing much else by way of error condition.

I've seen postings about patching the usbserial.c module patch but it doesn't seem quite right for this kernel.  Anyone else having the same issue and have a concrete fix? ](*,)   Thanks.  :-)

Cheers!

---

### Post by Major_Imbu on 2006-08-26
A few more details:

Sprint Novatel Merlin S620 32-bit PC-CARD
(Ev-Do coverage in Los Angeles area market)

/etc/ppp/peers/sprint:
#the USB serial device of the EV-DO PCMCIA card (Sprint Novatel s620)
ttyUSB0
#login info
230400 # speed
#debug
defaultroute # use the cellular network for default route
usepeerdns # use the DNS servers from remote network
nodetach # keep pppd in the foreground
crtscts # hardware flow control
lock # lock the serial port
lcp-echo-failure 4
lcp-echo-interval 65535
noauth # don't expect the modem authenticate itself
connect "/usr/sbin/chat -v -f /etc/ppp/peers/sprint-connect"
disconnect "/usr/sbin/chat -v -f /etc/ppp/peers/sprint-disconnect"

* I only recently added the lcp with arguments and have tried bit rate 115200b/s

---

### Post by Major_Imbu on 2006-08-26
Since my last posting it seems to have stabilized (it's been connected overnight).  The only difference at this point is that I've simplified and gone with this (as suggested from another forum - biggest thing is removing LCP and possibly HW flow control everywhere I think):

/etc/ppp/peers/sprint:

connect '/usr/sbin/chat -v -t3 -f /etc/ppp/sprint-chat'
debug
/dev/ttyUSB0
230400
defaultroute
usepeerdns

/etc/ppp/sprint-chat:
"'AT'"
'OK''ATDT#777'

Hope this helps anyone else with the same isse.

Now, for a graphical signal strength indicator...  :-)

Cheers!

---

