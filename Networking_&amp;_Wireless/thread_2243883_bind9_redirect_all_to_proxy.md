---
title: "bind9 redirect all to proxy"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by jj4 on 2014-09-11
I have an internal dns running unbound forwarding DNS queries via a proxy server.
I want to add  ablanket all redirect in unbound but it doesn;t seem possible.
Is this possible in bind9?

My current conf:

local-zone: "co.uk." transparent
# local-zone: "fcod.llnwd.net." transparent
local-zone: "bbc.co.uk." redirect
local-data: "bbc.co.uk. 600 IN A 109.xx.xxx.xxx"
local-zone: "bbc.com." redirect
local-data: "bbc.com. 600 IN A 109.xx.xxx.xxx"
local-zone: "zattoo.com." redirect
local-data: "zattoo.com. 600 IN A 109.xx.xxx.xxx"
local-zone: "lovefilm.com." redirect
local-data: "lovefilm.com. 600 IN A 109.xx.xxx.xxx"
local-zone: "uktv.co.uk." redirect
local-data: "uktv.co.uk. 600 IN A 109.xx.xxx.xxx"
local-zone: "williamhill.com." redirect
local-data: "williamhill.com. 600 IN A 109.xx.xxx.xxx"
local-zone: "eurosport.com." redirect
local-data: "eurosport.com. 600 IN A 109.xx.xxx.xxx"
local-zone: "netflix.com." redirect

---

