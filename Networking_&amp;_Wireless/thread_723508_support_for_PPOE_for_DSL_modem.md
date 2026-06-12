---
title: "support for PPOE for DSL modem"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by jcobban on 2008-03-13
My only connection to the Internet is through an ethernet attached DSL modem.  So before I can get beyond the small set of tools on the installation CD I need to activate the PPoE connection to my ISP.  I am not given that option, and if I need to download some additional feature from the Internet I cannot do it.  Is this a catch 22?

---

### Post by SpaceTeddy on 2008-03-13
open a terminal, and type
> sudo pppoeconf

that should give you a dialog where you can setup your dsl-modem (if it got deteced). after that, the option to connect via dsl will appear in network manager. 

and yes, this is a catch 22 if you do not know how to setup dsl connections (i really don't like that network manager does not bring a button for that - or that i have not found it yet)

---

