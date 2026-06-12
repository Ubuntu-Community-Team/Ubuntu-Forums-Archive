---
title: "Open ports on firewall for SSH"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by btgon on 2007-04-24
I was just curious what ports I should have open and forwarded to my ubuntu box so I can ssh into it from the outside my firewall? It works locally but when i try to go through my external firewall it gives me a "Connection refused ".

Thanks for the help!

---

### Post by sdide on 2007-04-25
sshd is usually set up to listen on requests on port 22, unless you set it up differently that should be what you are looking for.

---

