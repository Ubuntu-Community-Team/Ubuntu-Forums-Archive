---
title: "traceroute an E-mail??"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by Red-Shield on 2008-09-08
hello there can any one tell me if there is a way to do something close to like a **traceroute** or **host** check on an email address or trace its source i know it comes through the server but before the server is there a way to find the real IP address of the sender ??

---

### Post by HalPomeranz on 2008-09-09
The string of "Received:" headers in the email message is supposed to tell you the path that the email took to get to you.  Unfortunately, it's easy for a malicious user to forge these headers and lie about the path the email took.  So in general, no there is no way to figure out how the email got to you, other than knowing the IP address of the machine that's trying to send the email in to your mail server.

---

### Post by Red-Shield on 2008-09-09
well thanks for your help i do appreciate the response

---

