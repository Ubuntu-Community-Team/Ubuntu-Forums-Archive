---
title: "Vpn + ufw"
date: 2017-07-27
forum: Networking &amp; Wireless
---

### Post by mrfort on 2017-07-27
I have spent several days searching the internet and reading forum posts about how to make UFW work correctly with OpenVPN and PPtP. I have edited the /etc/default/ufw and the /etc/ufw/before.rules according to what I read. I have opened over a dozen ports (all were listed in the forum posts). NOTHING I have done has worked. It seems to me that such a popular linux distro used by many businesses would have an easy way to set up OpenVPN and PPtP. Especially in the GUFW gui. That should be in the list of "Preconfigured". One click solution. It should make any changes necessary. I am able to connect to and use my VPN but NOT with UFW active. This is a security issue. Is there ANYONE out there that can configure UFW CORRECTLY for VPN? I am tired of spending time trying hundreds of different suggestions in the forums. Hopefully a REAL expert on these things will answer this post.

---

### Post by TheFu on 2017-07-27
If you care at all about security, don't use PPTP.  It has been hacked for over a decade and really easy to hack since 2012. [https://www.schneier.com/blog/archives/2012/08/breaking_micros.html](https://www.schneier.com/blog/archives/2012/08/breaking_micros.html)

If you use openvpn (+ L2TP or IPSec), only 1 port needs to be opened.

For firewall stuff that isn't working the way I expect, I find drawing a diagram helpful.  That way I'm reminded to open the WAN port, forward to the STATIC IP on the server running the service.  If you don't effectively have 

If you use PPTP, then I cannot help. Sorry.  A quick search says a trivial setup (from ufw/gufw) might not be workable with pptp.

[https://wiki.ubuntu.com/UncomplicatedFirewall#Available_Versions_in_supported_versions_of_Ubuntu](https://wiki.ubuntu.com/UncomplicatedFirewall#Available_Versions_in_supported_versions_of_Ubuntu) might help. Maybe not, but it appears highly dependent on the specific release running.

---

