---
title: "Running glassfish in port 80"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by khristian on 2008-04-25
I'm running a Glassfish v2 server on a Kubuntu Gutsy machine, and I've been looking for a way to run it on port 80 (default is 8080), but without having to run it as root. Is this possible?

---

### Post by huggy77 on 2008-04-29
do you want apache to front it or do you want to use glassfish's webserver?

---

### Post by khristian on 2008-04-29
> **huggy77 said:**
> do you want apache to front it or do you want to use glassfish's webserver?

I need just glassfish running. Suggestions?

---

### Post by huggy77 on 2008-04-30
i just installed a fresh ubuntu GF install - you have to start in manually via the asadmin command.... it is in the gf bin dir...  i will monkey with it and post a how to... i really want to get apache fronting it - that will be fun

---

### Post by khristian on 2008-04-30
> **huggy77 said:**
> i just installed a fresh ubuntu GF install - you have to start in manually via the asadmin command.... it is in the gf bin dir...  i will monkey with it and post a how to... i really want to get apache fronting it - that will be fun

The server here is working fine, what I wanted to know is if there is a way of making it listen on port 80 (80 and 443) without the need to run it as root.

---

