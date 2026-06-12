---
title: "Conky help"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Defiant Rat on 2009-12-29
So, after spending way more time than is healthy, Ive got conky looking how i want. The only thing is the network stuff isnt working and i cant figure out why.
```
${color #5da5d3}Network (${color #e5e5e5}${addr}${color #5da5d3}) ${hr 1}
 ${color #e5e5e5}Down:${color lightgrey} ${downspeed eth0} k/s $alignr${color #e5e5e5} Up:${color lightgrey} ${upspeed eth0} k/s
${color #5da5d3}${downspeedgraph eth0 27,120 000000 ff0900 180} $alignr${color #5da5d3}${upspeedgraph eth0 27,120 000000 ff0900 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

```

Im connected to my wireless network and downloading, yet it shows upload and download as 0.
Screen shots attached, any ideas?

Thanks.

---

### Post by lemmy999 on 2009-12-29
Is your wireless NIC eth0 or something else? You might want to try a quick ifconfig and make sure!

---

### Post by rolnics on 2009-12-29
> **lemmy999 said:**
> Is your wireless NIC eth0 or something else? You might want to try a quick ifconfig and make sure!

I would say something else as eth0 is in the coding. ifconfig is the way to go

---

### Post by Defiant Rat on 2009-12-29
Cheers guys, turns out it was ra0. :D

---

