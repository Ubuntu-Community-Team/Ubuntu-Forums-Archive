---
title: "IPerf Server 2.0.4-1 Daemon Mode not Listening on Port"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by megakale on 2008-11-03
Hi there, 

I have to run IPerf Server in daemon mode and running netstat shows that iperf is not listening on the respective TCP port.

Envoirnment is Ubuntu 8.10 Server install in Virtual Machine mode with IPerf 2.0.4-1.

IPerf will only work if i run it under interactive terminal mode.

Many thanks for any advise.

MK

---

### Post by genernic on 2008-11-13
bump

I have somewhat the same issue. First of all, running in interactive mode works, but I need daemon mode for running multiple tests and return tests. 
running in daemon mode works somewhat the first test, except the return test from the client, and after the first test, the iperf process eats up my two cpus 100%....not really nice

---

