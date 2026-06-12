---
title: "Internet over Bluetooth via cell phone, hangs during high traffic loads"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by russnash37 on 2007-10-23
I've been using a bluetooth dongle attached to my Ubuntu 7.04 Server to access the internet via my cell phone successfully for some time now.  However, I have been plagued with one problem.

The whole setup works great, except when I start using higher traffic applications such as heavier web pages and Second Life.  It varies from occurrence to occurrence, but typically within ten minutes of logging into, for example, second life the modem drops the call.  More often, this will happen within a minute or two.  The disconnects do also happen during much lighter traffic loads, for example, just using an SSH session and perhaps browsing the odd webpage, however, these hangups are fewer and much further between.

The cell phone is an LG VX8300 connecting via Verizon's NationalAccess / BroadbandAccess service (EVDO).

Here is a typical log snippet:

> 
Oct 23 00:04:04 ds9 pppd[1045]: Starting link
Oct 23 00:04:07 ds9 chat[1075]: abort on (NO CARRIER)
Oct 23 00:04:07 ds9 chat[1075]: abort on (ERROR)
Oct 23 00:04:07 ds9 chat[1075]: abort on (NO DIALTONE)
Oct 23 00:04:07 ds9 chat[1075]: abort on (BUSY)
Oct 23 00:04:07 ds9 chat[1075]: abort on (NO ANSWER)
Oct 23 00:04:07 ds9 chat[1075]: send (ATZ^M)
Oct 23 00:04:07 ds9 chat[1075]: expect (OK)
Oct 23 00:04:07 ds9 chat[1075]: ATZ^M^M
Oct 23 00:04:07 ds9 chat[1075]: OK
Oct 23 00:04:07 ds9 chat[1075]:  -- got it 
Oct 23 00:04:07 ds9 chat[1075]: send (ATDT#777^M)
Oct 23 00:04:07 ds9 chat[1075]: expect (CONNECT)
Oct 23 00:04:07 ds9 chat[1075]: ^M
Oct 23 00:04:09 ds9 chat[1075]: ATDT#777^M^M
Oct 23 00:04:09 ds9 chat[1075]: CONNECT
Oct 23 00:04:09 ds9 chat[1075]:  -- got it 
Oct 23 00:04:09 ds9 chat[1075]: send (\d)
Oct 23 00:04:10 ds9 pppd[1045]: Serial connection established.
Oct 23 00:04:10 ds9 pppd[1045]: Connect: ppp0 <--> /dev/rfcomm0
Oct 23 00:04:22 ds9 pppd[1045]: Local IP address changed to 70.211.4.62
Oct 23 00:04:23 ds9 pppd[1045]: Open UDP 70.211.4.62:123 -> 128.118.25.3:123 
Oct 23 00:07:13 ds9 pppd[1045]: LCP terminated by peer
Oct 23 00:07:13 ds9 pppd[1045]: Connect time 2.9 minutes.
Oct 23 00:07:13 ds9 pppd[1045]: Sent 596 bytes, received 76 bytes.
Oct 23 00:07:13 ds9 pppd[1045]: Hangup (SIGHUP)
Oct 23 00:07:13 ds9 pppd[1045]: Modem hangup
Oct 23 00:07:13 ds9 pppd[1045]: Connection terminated.


I've done a lot of research and googling to try and find a resolution for this issue, my best guess so far is that it's a flow control problem of some kind.

My configuration files:

/etc/bluetooth/rfcomm.conf

> 
rfcomm0 {
        bind yes;
        device 00:12:56:4B:6E:85;
        channel 8;
        comment "Bluetooth PPP Connection";
}


/etc/chatscripts/verizon

> 
# abortstring
ABORT 'NO CARRIER' ABORT 'ERROR' ABORT 'NO DIALTONE' ABORT 'BUSY' ABORT 'NO ANSW
ER'
# modeminit
'' ATZ
# ispnumber
OK-AT-OKL3 ATDT#777
# ispconnect
CONNECT \d\c


/etc/ppp/peers/verizon

> 
hide-password
/dev/rfcomm0
connect "/usr/sbin/chat -v -f /etc/chatscripts/verizon"
noauth
defaultroute
usepeerdns
connect-delay 10000
user "123-456-7890@vzw3g.com"    <-- Edited out my cell phone number for my own sanity
demand
lock
lcp-echo-failure 4
lcp-echo-interval 65535

115200


I have tried making changes to the above file, such as specifying 'xonxoff' and 'crtscts' to no effect.  It is my understanding that hardware flow control (crtscts) is the default anyhow.

Any help anyone can offer with this problem would be gratefully received.  I had considered that their may be further diagnostics I could use on the serial link?

Thanks again!

Russ.

---

### Post by Mach1US on 2007-10-26
What is happening with your serial connection it uses one of protocols needed for ISDN which was default connection type for dial in connections.
It uses Link Control Protocol ( LCP ) which waits for the peer side to exchange LCP messagages but unfortunately it is not supported by  cell providers .
The work around is to disable it on your side .
To do so type :
```
sudo gedit /etc/ppp/peers/wvdial
```
then add following lines to the file:
```
lcp-echo-failure 0
lcp-echo-interval 0
```

If you have any questions feel free post your questions on my how-to :
[http://ubuntuforums.org/showthread.php?t=343989&highlight=motorola+evdo](http://ubuntuforums.org/showthread.php?t=343989&highlight=motorola+evdo)

---

### Post by russnash37 on 2007-10-26
Thanks for your response, Mach1US, I'll give this a try and post back the results in a few hours!

Thanks again!

Russ.

---

### Post by russnash37 on 2007-10-26
Unfortunately, these changes don't seem to have fixed the issue.  The answer must lay elsewhere :(

Thanks for the help though!

Russ.

---

