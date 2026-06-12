---
title: "Wired internet loses connection every 24 hours"
date: 2020-10-07
forum: Networking &amp; Wireless
---

### Post by Phasmus on 2020-10-07
I recently updated my office PC from 19.10 to 20.04. It went smoothly except now the system drops its internet connection at about the same time every day. I'm telecommuting so I'm locked out once it goes offline. Someone on site found that unplugging and re-plugging the ethernet cable fixes it so we figured resetting the network would also work. I set up a service to ping a local system once a minute and do this when the ping fails: 

```
nmcli networking off; nmcli networking on
```

That works to get it back online when the drop happens so I'm not getting locked out every day. But I'd rather get to the root of the problem and I'm not sure where to start. We're guessing it's an issue with dhcp/the 24 hour ip address reservation timeout but I don't know how to test that or address it if it is the case. I don't see anything in /var/log/syslog that seems like it might be the cause (just other services complaining they can't get online). Any ideas how to proceed? I'm happy to provide logs or other info but I'm not sure what would be useful.

---

### Post by TheFu on 2020-10-07
Just set a static IP on the system. Keep the dhcp stuff out of it.  Try that for a few days.
That's the first test.

---

