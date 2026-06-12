---
title: "Strange dial-up problem"
date: 2005-03-30
forum: Networking &amp; Wireless
---

### Post by renoir98 on 2005-03-30
Hi all,
i'm having a strange problem with my 56k connection.
I use an external (serial) 56k hamlet modem and it happens
that the connection is correctly done but it remains inactive for
about 2 minutes.
Then it starts working fine.
I cannot find where the problem resides :-( 
Maybe someone could point me in the right direction.
I've configured the connection using "pppconfig" 
and use "pon" and "poff" to start/stop the connection.
Thanks in advance,renoir98.

////////////////////////////

I can now provide the log taken from
/var/log/messages

```
Apr  1 09:54:49 localhost pppd[4846]: pppd 2.4.2 started by username, uid 1000
Apr  1 09:54:50 localhost chat[4847]: abort on (BUSY)
Apr  1 09:54:50 localhost chat[4847]: abort on (NO CARRIER)
Apr  1 09:54:50 localhost chat[4847]: abort on (VOICE)
Apr  1 09:54:50 localhost chat[4847]: abort on (NO DIALTONE)
Apr  1 09:54:50 localhost chat[4847]: abort on (NO DIAL TONE)
Apr  1 09:54:50 localhost chat[4847]: abort on (NO ANSWER)
Apr  1 09:54:50 localhost chat[4847]: abort on (DELAYED)
Apr  1 09:54:50 localhost chat[4847]: send (AT&FX3S91=14^M)
Apr  1 09:54:50 localhost chat[4847]: expect (OK)
Apr  1 09:54:50 localhost chat[4847]: AT&FX3S91=14^M^M
Apr  1 09:54:50 localhost chat[4847]: OK
Apr  1 09:54:50 localhost chat[4847]:  -- got it
Apr  1 09:54:50 localhost chat[4847]: send (ATDT7001010732^M)
Apr  1 09:54:50 localhost chat[4847]: expect (CONNECT)
Apr  1 09:54:50 localhost chat[4847]: ^M
Apr  1 09:55:22 localhost chat[4847]: ATDT7001010732^M^M
Apr  1 09:55:22 localhost chat[4847]: CONNECT
Apr  1 09:55:22 localhost chat[4847]:  -- got it
Apr  1 09:55:22 localhost chat[4847]: send (\d)
Apr  1 09:55:23 localhost pppd[4846]: Serial connection established.
Apr  1 09:55:23 localhost pppd[4846]: Using interface ppp0
Apr  1 09:55:23 localhost pppd[4846]: Connect: ppp0 <--> /dev/ttyS0
Apr  1 09:55:39 localhost pppd[4846]: PAP authentication succeeded
Apr  1 09:55:40 localhost pppd[4846]: local  IP address 62.94.38.139
Apr  1 09:55:40 localhost pppd[4846]: remote IP address 62.94.58.21
Apr  1 09:55:40 localhost pppd[4846]: primary   DNS address 62.94.8.246
Apr  1 09:55:40 localhost pppd[4846]: secondary DNS address 62.94.8.245
Apr  1 09:58:09 localhost pppd[4846]: No response to 4 echo-requests
Apr  1 09:58:09 localhost pppd[4846]: Serial link appears to be disconnected.
Apr  1 09:58:15 localhost pppd[4846]: Connection terminated.
Apr  1 09:58:15 localhost pppd[4846]: Connect time 2.8 minutes.
Apr  1 09:58:15 localhost pppd[4846]: Sent 6553 bytes, received 25196 bytes.
Apr  1 09:58:16 localhost pppd[4846]: Exit.
 
``` 

Sometimes the last lines output these errors
```
Apr  1 09:54:22 localhost pppd[4771]: LCP: timeout sending Config-Requests
Apr  1 09:54:22 localhost pppd[4771]: Connection terminated.
Apr  1 09:54:22 localhost pppd[4771]: Receive serial link is not 8-bit clean:
Apr  1 09:54:22 localhost pppd[4771]: Problem: all had bit 7 set to 0
Apr  1 09:54:23 localhost pppd[4771]: Exit.
 
``` 

Thanks again for your replies.

---

