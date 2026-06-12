---
title: "Configure Proxy-Settings in Terminal?"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Che.SSL on 2008-07-13
Hi :)
how do I set up system-wide proxy-settings through the terminal? I'm looking for the command(s)...
I have tried export http_proxy='http://192.168.0.100:8080', but Firefox, Epiphany & Co won't use the actual proxy.
Thanks.

---

### Post by axel1973 on 2009-03-26
its so sad that there is no knowledge or no will of the peoples to help for such a long time... SAD!

im looking for the same information. i found several docs for a possibly solution. but i was not able to find any doc/manual/man page on ubuntu or debian lenny 5.0 that describes HOW to and WHERE to correctly enter that http_proxy enviroment variable.

i found docs telling me it should go into /etc/profile, others say /etc/bash.bashrc . so whats right? whats wrong?

there seems also to be a difference between linux console AND linux gui (X enviroment, gnome kde etc). i some cases the variable is available and correct within the console/text enviroment but it didnt made it into the GUI enviroment. this is still not clear to me.

---

### Post by BkkBonanza on 2009-03-26
This page has info about how to do this,

[http://wazem.blogspot.com/2008/01/how-to-change-gnome-proxy-settings-on.html](http://wazem.blogspot.com/2008/01/how-to-change-gnome-proxy-settings-on.html)

Keep in mind that if you change the environment within a console window with "export" it only affects that console and any programs inherited from it. So doing so has no way to affect the system globally.

If you add an export command to /etc/profile then it will be picked up by any consoles opened after. But whether a program uses envirnoment variables or not is completely dependent on what the programmer chose to do.

---

### Post by BkkBonanza on 2009-03-26
I was just playing around with gconftool to see how it interacts with Firefox.
The info given on the page I noted above is a little off. 
You actually need to also change the use_http_proxy value too or FF will not respond.

So this will set mode to manual,

gconftool --set /system/proxy/mode --type string manual
gconftool --set /system/http_proxy/use_http_proxy --type bool true

and this will set it back,

gconftool --set /system/proxy/mode --type string none
gconftool --set /system/http_proxy/use_http_proxy --type bool false

And actually if you are toggling between manual and direct I think you can just do one command and set the boolean accordingly.

gconftool --set /system/http_proxy/use_http_proxy --type bool false

Not all programs use the gnome settings though. 
Thunderbird does not. Shame.

---

