---
title: "Allowing incoming ftp in firewall"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by whiteB on 2006-08-07
Hi, I have done Natting with Ip-tables. Now, I just want to establish an ftp connection
to a remote server with Public IP.When I tried to do ftp, I was able to
connect to the remote server. But after authentication in the remote server,Connection showing as ,going to passive mode and Freezing.
Any body can help me ,what modifications should i do in the firewall
to allow incoming ftp from my client pc's.
crackerB is offline

---

### Post by noof on 2006-08-07
What ip is the server giving you? Using an ftp client behind nat should work without any modifications if you're using passive mode. It sounds like the remote server gives you a bogous ip though.

---

