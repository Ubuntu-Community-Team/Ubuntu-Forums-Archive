---
title: "Echo public IP string for conky?"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by schema2 on 2014-10-11
I am trying to modify a conkyrc to include public ip. i've tried a few things, things I've found on the net. I am just copy/pasting because I don't understant conky format verywell. I really cant seem to get any kind of string working to echo back my external ip in my conky network monitor. the best i've been able to do so far is to get conky to echo back html code for an entire 'whats my ip' web page, lol. I'm sure this is easy. Could someone please help? Here is the snippet in question;

#----------------------------------------------------------------------------------------------------------------------------------------
#                        Network
#----------------------------------------------------------------------------------------------------------------------------------------
${color 0ABFFF}${voffset 2}${hr 1}
${color 0ABFFF}${voffset 5}Hostname: $color$alignr$nodename
${color 0ABFFF}wlan0: $color$alignr${addr wlan0}
${color 0ABFFF}Current: $color${alignr}${execi 10 /sbin/iwconfig wlan0|grep Rate|cut -d"M" -f1|cut -b20-24} Mbits/sec
${color 0ABFFF}eth0: $color$alignr${addr eth0}

${color #0ABFFF}Down: $color${downspeed wlan0} k/s ${alignr}${color #0ABFFF}Up:$color ${upspeed wlan0} k/s
${downspeedgraph wlan0 30,120 000000 0ABFFF} ${alignr}${upspeedgraph wlan0 30,120 000000 0ABFFF}$color
${color #0ABFFF}Total:$color ${totaldown wlan0} ${alignr}${color #0ABFFF}Total:$color ${totalup wlan0}

---

### Post by CantankRus on 2014-10-12
```
#----------------------------------------------------------------------------------------------------------------------------------------
# Network
#----------------------------------------------------------------------------------------------------------------------------------------
${color 0ABFFF}${voffset 2}${hr 1}
${color 0ABFFF}${voffset 5}Hostname: $color$alignr$nodename
${color 0ABFFF}wlan0: $color$alignr${addr wlan0}
${color 0ABFFF}Current: $color${alignr}${execi 10 /sbin/iwconfig wlan0|grep Rate|cut -d"M" -f1|cut -b20-24} Mbits/sec
${color 0ABFFF}eth0: $color$alignr${addr eth0}
[COLOR="#FF0000"]**${color 0ABFFF}Public IP: ${color}${alignr}${execi 3600 wget -q -O - http://icanhazip.com}**[/COLOR]

${color #0ABFFF}Down: $color${downspeed wlan0} k/s ${alignr}${color #0ABFFF}Up:$color ${upspeed wlan0} k/s
${downspeedgraph wlan0 30,120 000000 0ABFFF} ${alignr}${upspeedgraph wlan0 30,120 000000 0ABFFF}$color
${color #0ABFFF}Total:$color ${totaldown wlan0} ${alignr}${color #0ABFFF}Total:$color ${totalup wlan0}
```
[COLOR="#FF0000"]**Added line**[/COLOR]

If you see something like this in conky...
```
${execi 3600 **wget -q -O - http://icanhazip.com**}
``` 
it means... exec interval **command** 

The command part you can test in terminal
eg
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] [COLOR="#FF8C00"]wget -q -O - http://icanhazip.com[/COLOR]
124.148.238.30
```

---

