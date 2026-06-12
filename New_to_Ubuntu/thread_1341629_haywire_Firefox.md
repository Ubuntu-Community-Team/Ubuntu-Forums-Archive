---
title: "haywire Firefox"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by rm06 on 2009-11-29
Since I have upgraded to 9.10 my Firefox seems to have gone haywire. The main problem I've noticed is when clicking on a bookmark in the bookmarks toolbar, it does not go to that site even though the address bar is the correct address. This doesn't happen with any regularity that I've been able to discern as of yet but it is getting annoying. Lots of 404 errors as well on site such as Google which I know aren't down and I'm able to confirm that via other computers.

I tried to download Debian Lenny for about a week thinking their servers were down until I tried it from my Windows partition without a problem and again confirmed that I was unable to get there from Firefox (although I did use Firefox in Windows).

I have even completely re-installed 9.10 as a matter of coincidence and am still experiencing the same problems. Is this a known problem? I cannot find any reported bugs related to this issue.

---

### Post by cariboo on 2009-12-03
You more than likely have a dns problem. Right click the Network-Manager icon in the top panel and select Edit Connection, then select the network interface usually eth0 and click the edit button. Next select the IPv4 tab and from the method drop down and select Automatic (DHCP) addresses only. Then enter either the DNS server address from:
[list]
[*]Opendns  208.67.222.222, 208.67.220.220
[*]Google   8.8.8.8, 8.8.8.4
[/list]

Click Apply, anter your password when asked, and you should be good to go.

---

