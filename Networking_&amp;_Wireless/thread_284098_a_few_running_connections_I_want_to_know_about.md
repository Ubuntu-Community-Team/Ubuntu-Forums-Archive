---
title: "a few running connections I want to know about ?"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by neewby on 2006-10-25
Hi ,

 Could someone tell me what services are running on these specific ports locally ? 
                   

                 LOCAL ADDRESS      ///       FOREIGN ADDRESS


tcp               localhost:60372    ///     *:*                     LISTEN
tcp              localhost:49406    ///    *:*                     LISTEN
tcp              localhost:49406    ///     localhost:57450        ESTBLISH
tcp               localhost:57450    ///     localhost:49406        ESTBLISH
udp               *:bootpc           ///      *:*
udp               *:bootpc           ///     *:*

its weird , how local address 49406 > 57450 > 57450 > 49406 ?
seeing BootP Client does this mean I have a static IP ?

---

### Post by matthewstory on 2006-10-25
most likely what you're seeing are services that use the local loopback device (lo) to talk to the machine.  This is just how a lot of linux servers work, they talk to the machine they are running on over the local loopback device.

---

