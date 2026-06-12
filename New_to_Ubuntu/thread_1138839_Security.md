---
title: "Security"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by theozzlives on 2009-04-26
How do I secure my network so that one computer can access the internet but not my network, I'm using Samba?

---

### Post by Saghaulor on 2009-04-26
I'm not expert, but it's worth a try.

I believe you could statically specify an ip that is on a separate subnetwork, but that uses the same gateway ip, hence its using the internet, but not accessible to your network.

Additionally, a way that I'm sure that works, you could set up your network behind a router, then specify a DMZ, then statically assign any foreign computer to the DMZ, so that it is in front of your firewall but not accessible to your network behind the firewall.

---

### Post by H4F on 2009-04-26
I don't think you have to be varied about. samba does not share your internet . do you get internet from cable or from modem ? is your modem configured to make ppp connection ? or you pc makes ppp connection ?

---

