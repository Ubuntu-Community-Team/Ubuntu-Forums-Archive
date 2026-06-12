---
title: "Config Files iptabls bzw. Stop-Skript bei Start-up"
date: 2016-07-24
forum: Networking &amp; Wireless
---

### Post by radiac2 on 2016-07-24
Hallo Zusammen!

Ich habe mich anscheinend versehntlich mittels iptables von meiner VM ausgesperrt und komme mittels SSH nicht mehr darauf. Der Fehler ist noch 100%ig verifziert, aber ich denke es liegt daran. Ich habe jedoch die Möglichkeit das Volume an eine andere VM zu hängen. Jetzt war meine Idee: 

1. Die Config-Dateien "manuell" zu bearbeiten oder
2. Ein Start Skript zu schreiben dass die iptables erst mal flusht.

Weiß jemand von euch wo die Config unter Ubuntu 14.04 standardmäßig liegt bzw. wie ich ein Start-Skript platzieren muss damit es beim start ausgeführt wird?

Danke für eure Hilfe!

MfG

---

### Post by radiac2 on 2016-07-24
iptables -F unter /etc/rc.local brachte den notwendigen erfolg ;-)

---

### Post by howefield on 2016-07-24
Hello radiac2,

Welcome to the forums.

> Write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries, and English is the common language of these forums.

---

