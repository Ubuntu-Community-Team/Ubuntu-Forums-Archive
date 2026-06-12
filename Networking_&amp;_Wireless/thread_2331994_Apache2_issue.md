---
title: "Apache2 issue?"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by ignitiongtown on 2016-07-27
I'm running a python script on my server every once in awhile the script seems to bind a port and I have to switch it. I tried lsof -i :myport | grep "python" | cut -d " " -f2 | xargs kill -9 both with -f2 and -f3. This did nothing python still gives the error errno98 address already in use.

But this command did work fuser -k 5004/tcp, the issues is I think since it kills the process that opened that port it's killing apache maybe. I think this because nmap only shows ssh open port nothing else.

If I remember open with iptables restart the service for Apache2 and networking I still get nothing. I sometimes also get a forbidden error from Apache2 instead of a cannot connect message with I get from the site if I go to the port but the Web app hasn't started.

Ubuntu 16.04 server

---

