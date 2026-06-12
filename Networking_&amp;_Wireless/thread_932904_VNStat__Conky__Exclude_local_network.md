---
title: "VNStat / Conky / Exclude local network"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by BoGs on 2008-09-28
I recently had my internet disabled for going over the monthly isp allowance and am setting up a counter to keep track of my bandwidth.

I have installed vnstat and included the outcome to my conky rc file. Now I run into another issue, and that issue is local network. This computer is on a local network and I transfer photos and documents and such from other computers, Is there any way to exclude that traffic from the calculation to get an accurate amount of what I am actually using.???

any help would be appreciated.

---

### Post by dfmalh on 2009-04-07
Hi, I have only recently started to use Conky and would like to use vnstat to log my monthly isp allowance. I saw some thumbnails and it look very nice. You can then track your total as it is "growing".

I downloaded vnstat, but when I try and add some of the conky.rc code to my conky.rc file it does not work.

Is there a good how to somewhere that someone would like to share please.

Thanks, for all the help.

---

### Post by dfmalh on 2009-04-21
OK, my vnstat is working perfect! 

It switches between and only display: 
[LIST]WLAN, [/LIST]
[LIST]LAN and, [/LIST]
[LIST]No network[/LIST]


Here is the code:
```

NETWORK is ${if_existing /proc/net/route eth1}a WLAN ${else}${if_existing /proc/net/route eth0}a LAN ${endif}${else}unavailable${endif}${hr 2}${if_existing /proc/net/route eth1}
ESSID: ${alignr}${wireless_essid eth1} 
Signal Quality: ${wireless_link_qual eth1}% ${alignr}${wireless_link_bar 8,60 eth1}
WAP MAC: ${alignr}${wireless_ap eth1}
Local IP: ${alignr}${addr eth1}
External IP: ${alignr}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}

${alignc}${upspeedgraph eth1 16,180 582D10 E08000}
${color #FFFFFF}ULS: ${upspeed eth1} kb/s ${alignr}Session Uploads: ${totalup eth1}
${alignc}${color2}${downspeedgraph eth1 16,180 444444 AAAAFF}
${color #FFFFFF}DLS: ${downspeed eth1} kb/s ${alignr}Session Downloads: ${totaldown eth1}

WLAN Summary
${hr 1}
Downloads${goto 150}${color1}Uploads
${color1}Today:$color${goto 60}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $2 $3}'}${goto 150}${color1}Today:$color${goto 210}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $5 $6}'}  
${color1}Week:$color${goto 60}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $3 $4}'}${goto 150}${color1}Week:$color${goto 210}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $6 $7}'} 
${color1}Month:$color${goto 60}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150}${color1}Month:$color${goto 210}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
${endif}${else}
${if_existing /proc/net/route eth0}
LAN IP: ${alignr}${addr eth0}
Default Gateway IP:${alignr}${gw_ip eth0}
${alignc}${upspeedgraph eth0 16,180 582D10 E08000}
${color #FFFFFF}ULS: ${upspeed eth0} kb/s ${alignr}Uploads: ${totalup eth0}
${alignc}${color2}${downspeedgraph eth0 16,180 444444 AAAAFF}
${color #FFFFFF}DLS: ${downspeed eth0} kb/s ${alignr}Downloads: ${totaldown eth0}

LAN Summary
${hr 1}
Downloads${goto 150}${color1}Uploads
${color1}Today:$color${goto 60}${execi 300 vnstat -i eth0 | grep "today" | awk '{print $2 $3}'}${goto 150}${color1}Today:$color${goto 210}${execi 300 vnstat -i eth0 | grep "today" | awk '{print $5 $6}'}  
${color1}Week:$color${goto 60}${execi 300 vnstat -i eth0 -w | grep "current week" | awk '{print $3 $4}'}${goto 150}${color1}Week:$color${goto 210}${execi 300 vnstat -i eth0 -w | grep "current week" | awk '{print $6 $7}'} 
${color1}Month:$color${goto 60}${execi 300 vnstat -i eth0 -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150}${color1}Month:$color${goto 210}${execi 300 vnstat -i eth0 -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
${endif}

```

I hope this will help someone. :D

---

### Post by Blyde on 2009-05-01
Any idea how to clear the VNSTAT database?

---

