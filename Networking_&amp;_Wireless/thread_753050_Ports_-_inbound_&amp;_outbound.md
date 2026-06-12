---
title: "Ports - inbound &amp; outbound"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Bruce M. on 2008-04-12
How can I figure out which ports are used for inbound traffic and which are used for outbound traffic?

Here's the thing; my conky NEVER reports **Inbound** traffic, even when I'm downloading something.
Outbound seems to work and total works, but I'm not sure that outbound is accurate.

When I open FF and come here I see Outbound numbers go up and Total go up, but I would thing I should be seeing Inbound and Total figures there.

Even my Down & Up seem to be messed up.

Here is what I'm using to get the information.
```

${color orange}IP:${alignc}${color white}${addr eth0}$color
${color cyan}Down: ${color white}${downspeed eth0}k/s ${alignr}${color cyan}Up: ${color white}${upspeed eth0}k/s $color
${color cyan}Total: ${color white}${totaldown eth0} ${alignr}${color cyan}Total: ${color white}${totalup eth0} $color
${color cyan}Inbound: ${color white}${tcp_portmon 1 32767 count}          ${color cyan}Outbound: ${color white}${tcp_portmon 32768 61000 count}${alignr}${color cyan}Total: ${color white}${tcp_portmon 1 65535 count} $color
${color orange}Connections: ${color white}${tcp_portmon 32768 61000 count} ${alignr} ${color orange}Service/Port $color${color white}

```

Thanks
Bruce

---

