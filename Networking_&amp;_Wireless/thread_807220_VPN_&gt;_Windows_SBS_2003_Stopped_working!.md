---
title: "VPN &gt; Windows SBS 2003 Stopped working!"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by slavnist on 2008-05-25
I have a home network with Ubuntu 8.04 configured to connect to a remote office via VPN tunneling. I set it up and it connected first time. I then was able to login to the server using Terminal Service Client (TSC). Wow.. Feeling pleased with myself I demonstrated the setup to a friend (fatal).
I showed him how I was able to control the server and even run Explorer to surf the web. Then I showed him how I could even log into the office router via explorer. It was the I noticed that the ADSL speed of the office router was very slow and thinking it could benefit from a reboot !!](*,) Typical MS solution.[-X Anyway. the result was breaking the tunnel and the TSC without logging out (silly me, as my IP address is in the router I should have logged into the router directly and rebooted it without leaving a session open).

The router rebooted and the server is still running and I can log into the server from home but only via a Windows XP machine. My Ubuntu VPN now fails every time. I suspect the the server thinks that I am still logged in and refuses another session from the same gateway.

If anyone is still following me and knows anything about Windows tunneling and active sessions I am sure the fault is there as Ubuntu seems to be rock solid. What do I need to kill instead of rebooting the server? and How?

---

