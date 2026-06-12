---
title: "iked.real error with Kvpnc"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by chabs on 2008-06-02
I am very new with Ubuntu and linux itself therefore bare with me since this might be a very easy solution but I am stuck!  I set up Kvpnc and had it working fine and now I get this error when I launch the application.

info: Gateway hostname (142.176.36.40) resolved to "142.176.36.40".
info: Trying to connect to server "142.176.36.40" (142.176.36.40) with user "dchaba" and IPSec ID "yhzJZAvpn"... 
debug: bindingFailed to bind to 0.0.0.0:500: Address already in use
debug: NameAndPid: 5127/iked.real

The a windows pops up saying 
 
Error - kvpnc

Binding port 500 failed.  Program "iked.real" with PID "5127" is using 
it.  You have to stop it first.

I have looked all over the net and forums about iked.real but have no idea how to stop it.  Any help would be appreciated.

---

### Post by chabs on 2008-06-08
I figured out how to stop the program with this command

sudo killall iked.real

And now Kvpnc is working fine.

---

### Post by OpenThinking on 2011-01-01
> **chabs said:**
> ...
I have looked all over the net and forums about iked.real but have no idea how to stop it.  Any help would be appreciated.

Hi!

Uninstall the Shrew Soft VPN client through Ubuntu program central.

---

### Post by rrsguru on 2012-02-05
Thank you Open Thinking, the uninstallation of Shrew Soft VPN Manager helped to connect KVPNC and also my VPN netwowrk manager

---

