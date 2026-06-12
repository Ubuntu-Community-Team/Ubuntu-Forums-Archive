---
title: "SSH Tunnel and DNS requests"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by proxyofsocks on 2010-08-18
I've successfully set up an SSH tunnel to my home computer. I connect to the SSH server and use the network preferences to apply system wide proxy settings. When I use Wireshark to capture the stream it appears the tunnel is active but the DNS requests are not routed through the tunnel. I have used FF about:config page to change the DNS proxy settings but I don't think it worked.

If that's the case will all DNS requests from other applications be viewable on the LAN? Is there any solution to this?

Thanks

---

### Post by Brandon Williams on 2010-08-18
Which setting did you change in firefox for DNS? I assume that it's network.proxy.socks_remote_dns. If that is set and if your ssh tunnel is providing a SOCKS proxy with -D, then I would expect to see all DNS requests from firefox to be resolved via the tunnel, while all other DNS requests will be resolved directly. Please be more specific about what is giving you the indication that this is not the case.

I use an ssh tunnel to connect to my office network, and I know that the DNS requests are being handled via the tunnel because they can't be resolved without it. I don't use the system settings to define the proxy though. I use the foxyproxy extension, because it allows me to only resolve hostnames via the tunnel when the resulting request will be handled via the tunnel. It could be that there's a problem associated with using the system settings that I'm unaware of.

---

