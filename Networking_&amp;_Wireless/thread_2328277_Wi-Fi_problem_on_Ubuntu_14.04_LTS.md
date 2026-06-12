---
title: "Wi-Fi problem on Ubuntu 14.04 LTS"
date: 2016-06-19
forum: Networking &amp; Wireless
---

### Post by ozymandias2 on 2016-06-19
Hi everyone, it's my first post here and I need your help.
Months ago I installed Ubuntu 14.04 on my Lenovo laptop, since that time my wi-fi connection isn't working well. I can't solve this problem so I ask you help. Wi-fi connection is very slow and sometimes it desappear. How can I fix it?

---

### Post by howefield on 2016-06-19
Thread moved to the "*Networking & Wireless*" forum.

Read this thread "*[Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") *" whilst you wait.

---

### Post by sam_baker2 on 2016-06-20
I also have a Lenovo laptop Thinkpad running 14.04
When I was using 12.04 I did not have any problems, but when I went to 14.04, I started getting intermittent 
disconnects.
I finally put an external ASUS Realtek dongle on it and now have no problems with it.
I think on my computer it was a problem with the Realtek network driver.
You may want to consider getting a dongle adapter and try it.
I also tried to change to different frequencies in my router, I changed the protocol
from B/G mixed to G only, nothing worked, but you may want to try doing this first.

---

### Post by Rick St. George on 2016-06-21
Ozyman - you are obviously getting a connection.  check this out (it worked for me).
For some reason "Routes" gets Checked by default, after an update ... which ignores the routes!
This may be what is happening to you, and others, who show an IP Address ... meaning you're connected but nothing connects.

1. Disable Wireless in Network Mgr.

2. Open Network Mgr / EDIT, Selected WiFi connection / EDIT / IPv4 Settings ... 
    Selected Automatic (DHCP) 

3. Next Additional DNS servers: add a DNS server, select from here;
        [http://pcsupport.about.com/od/tipstricks/a/free-public-dns-servers.htm](http://pcsupport.about.com/od/tipstricks/a/free-public-dns-servers.htm)
   
4. Checked "Require IPv4 addressing for this connection ..."

5. then Click the "Routes" button, UNCHECK "ignore automatically obtained routes",
   also make sure "use this connection only for resources.." is UNCHECKED.

6. Select IPv6 Tab / Ignore IPv6 (for security reasons), then Save & Close

7. Choose "Enable Wireless" in Network Mgr.

---

