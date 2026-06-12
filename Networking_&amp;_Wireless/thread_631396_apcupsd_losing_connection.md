---
title: "apcupsd losing connection"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by jsylvia007 on 2007-12-04
Hi All!

I'm hoping someone else has run into this issue before.  I have installed apcupsd on a machine to act as the "server".  This machine is directly connected to the UPS.  There are 5 "slave" machines that read it's values to determine whether or not they should power down.

The issue is that all the client machines seem to be losing connection to the apcupsd daemon resulting in a multitude of emails being sent out because of loss / regain of the connection.

Last night all 5 machines lost connection to the backup machine 15 times a piece...  this resulted in 5 * 2 * 15, or 150, email messages.  I should also mention that I have a blackberry, so it was buzzing non-stop for almost 4 hours... from 2am to 6am...

The backup machine is NOT rebooting, and as far as I can tell is running normally, and no other services are affected.  Is there ANYTHING that might be causing this?  I can't find a single thing in any of the logs.

System Info:

All Systems are Ubuntu 7.10
All Systems are apcupsd 3.14.1-3

HELP!

---

