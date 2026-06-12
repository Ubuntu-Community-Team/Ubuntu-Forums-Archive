---
title: "Got bluetooth connection to dialup networking BUT can't get remote ip adress"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by wakeboarder on 2007-10-23
Setup bluetooth connection to my phone and everything seems fine up to when a remote ip adress should be set

Can someone please help me sort this out?
I can ping the local adress below but not the remote one.
It seems to setup the DNS servers OK though.

This from the log

Oct 24 00:01:38 localhost chat[5994]: ^M
Oct 24 00:01:40 localhost chat[5994]: ATD*99***1#^M^M
Oct 24 00:01:40 localhost chat[5994]: CONNECT
Oct 24 00:01:40 localhost chat[5994]:  -- got it 
Oct 24 00:01:40 localhost chat[5994]: send (^M)
Oct 24 00:01:40 localhost pppd[5991]: Serial connection established.
Oct 24 00:01:40 localhost pppd[5991]: Using interface ppp0
Oct 24 00:01:40 localhost pppd[5991]: Connect: ppp0 <--> /dev/rfcomm0
Oct 24 00:01:41 localhost pppd[5991]: Remote message: Congratulations!
Oct 24 00:01:41 localhost pppd[5991]: PAP authentication succeeded
Oct 24 00:01:42 localhost pppd[5991]: Could not determine remote IP address: defaulting to 10.64.64.64
Oct 24 00:01:42 localhost pppd[5991]: local  IP address 10.145.34.153
Oct 24 00:01:42 localhost pppd[5991]: remote IP address 10.64.64.64
Oct 24 00:01:42 localhost pppd[5991]: primary   DNS address 10.0.0.1
Oct 24 00:01:42 localhost pppd[5991]: secondary DNS address 10.0.0.2
Oct 24 00:02:20 localhost pppd[5991]: Terminating on signal 15
Oct 24 00:02:20 localhost pppd[5991]: Connect time 0.7 minutes.
Oct 24 00:02:20 localhost pppd[5991]: Sent 336 bytes, received 0 bytes.
Oct 24 00:02:21 localhost pppd[5991]: Connection terminated.
Oct 24 00:02:21 localhost pppd[5991]: Exit.

:confused:

---

### Post by wakeboarder on 2007-10-24
Actually I've found sort of a workaround

If I enter the following in the ppp provider for example **/etc/ppp/peers/provider**
**replacedefaultroute**

**it works!**

But it messes things up when the connection is terminated and there are other active network interfaces.
This might no be a big issue when traveling since I wouldn't have any other interfaces than the ppp one.
At home I have both wireless and wired, although I mostly use the wireless.
ACTUALLY it only mess things up when bouncing the interface many many times i.e. when trying to get this working.
**With normal use everything seems to be just fine!**

Still, being curious and all I would like know why I don't get a remote ip. Is this just that my Internet provider has this particular configuration?
;)

---

