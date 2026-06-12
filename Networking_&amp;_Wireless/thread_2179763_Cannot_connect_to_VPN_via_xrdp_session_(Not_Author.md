---
title: "Cannot connect to VPN via xrdp session (Not Authorized to control networking)"
date: 2013-10-09
forum: Networking &amp; Wireless
---

### Post by mike68 on 2013-10-09
I have 12.04 LTS installed on a server which I'm setting up to be a home media server. I currently have a monitor connected to the server but I want to be able to do all administration on the box using my win7 laptop.

I've installed xrdp and can now connect using remote desktop. I connect using the same user I log in directly who is an administrator.

This setup is generally working OK except for 2 issues:

1) If I try to connect to my VPN (clicking the network top right, VPN connections) it works fine if I am actually using the box, but if I remote desktop in, I get the following error.
VPN Connection Failed Not authorized to control networking. This appears as a popup error that disappears after a couple of seconds.

2) When I connect using xrdp I get a different desktop session to that which I have on the actual box. This causes me a problem with firefox as I can't run it in both sessions. Is there a way to connect to the same session I have on the actual box or get around this problem some other way?

I am a relative newbie to both Ubuntu and Linux in general.

I suspect that for some reason, I have a different set of permissions when remoting in via xrdp rather than a direct connection. I need to have full permissions.

Thanks,

Mike

---

