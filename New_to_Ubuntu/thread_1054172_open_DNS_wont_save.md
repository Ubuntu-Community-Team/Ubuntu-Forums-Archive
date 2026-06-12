---
title: "open DNS wont save"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by bu2971x on 2009-01-29
I want to try open DNS and I add both addresses and restart but they dont save. I am usually on the WildBlue satellite DNS and its still there.
How do you get it to save?  and when I do get it to save how do you select
one of my choice for a session??   thanks

---

### Post by schwascore on 2009-01-31
You didn't mention how you were attempting to do this, so I'm going to suggest the following, which works for me:

Click on System --> Preferences --> Network Configuration
Select the tab that corresponds to your active network connection (Wired, Wireless, etc.)
Click on the actual network connection that is shown in the main window.
Click on "Edit"
Click on the IPv4 Settings tab
In the "Method" pull-down menu, select "Automatic (DHCP) addresses only"

You can now enter OpenDNS's server IP addresses in the DNS Servers text box.  Separate the two IPs with a comma.

Click on "OK" and everything should work just fine.

---

