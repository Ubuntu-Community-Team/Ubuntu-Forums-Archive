---
title: "Can I Make My WiFi And Network Cards Look LIke Routers?"
date: 2016-03-21
forum: Networking &amp; Wireless
---

### Post by grace3 on 2016-03-21
Hello,

I'm wondering if it will be possible to make my wifi and network cards look like routers to my ISP?

Here's what I have in mind:

I'm  wondering if it would be possible to make my network cards look like  routers and then create a virtual server in local host or apache that  connects to these "routers" with my pc ultimately connecting to this  server through local host. In fact, why not an entire virtual network.  with servers and pcs all talking to each other, with random realistic  ping times; and my pc randomly connecting to any number these of random  virtual servers, as a gateway to the Internet. This may in fact be what the TOR  network does; but why not have this in an app on my pc and connect to  TOR as well?

Of course the purpose of this app would be anonymity  and security. Perhaps, I could write or commission such an app and make  it available for free on source forge. I think I want to call it  "Network Heaven."
Kind of like a sim city of networking and encrypted vpns that you can actually connect to, all inside of your pc. This is a game I'd like to see!

I'm a dreamer I know; but I think this might be technically possible.

Any useful insights appreciated.

---

### Post by SeijiSensei on 2016-03-21
I doubt you can replace most proprietary cable or DSL modems with a Linux box, but you can certainly build a router and place it behind the ISP's device.  There's no way any of this would be somehow "hidden" from the ISP since all the outbound traffic would eventually be sent out the ISP's router.

I use [OpenVPN]("http://openvpn.net/static.html") to create an encrypted tunnel between a machine on my local network configured as a router and the servers I rent from [Linode]("http://www.linode.com/").  I could forward all my outbound traffic through the tunnel, but once it leaves the remote server it is still visible to anyone who wants to snoop.  Personally I think some people seem to devote a lot of effort to "protecting" themselves from surveillance in the mistaken belief that someone actually cares what they are doing.

---

### Post by slickymaster on 2016-03-21
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by grace3 on 2016-04-06
> **SeijiSensei said:**
> I use [OpenVPN]("http://openvpn.net/static.html") to create an encrypted tunnel between a machine on my local network configured as a router and the servers I rent from [Linode]("http://www.linode.com/").  I could forward all my outbound traffic through the tunnel, but once it leaves the remote server it is still visible to anyone who wants to snoop.  Personally I think some people seem to devote a lot of effort to "protecting" themselves from surveillance in the mistaken belief that someone actually cares what they are doing.

Can you explain how to set this up? I would like to do this for myself.

BTW, the hotel I'm staying in uses London Trust Media [https://londontrustmedia.com/](https://londontrustmedia.com/) . This service has far less latency than either TOR or HMA. Alternatively, I've used Zenmate and Tunnel Bear. I'd love to get an opinion about LTM.

Thanks, Grace

---

### Post by QIII on 2016-04-06
Please do not ask for help via PM.

Any solution or explanation is then lost to the community.  The Forums do not exist simply so that individuals can get help - which of course they do.  But our purpose here is to provide solutions and advice for the entire community.

To that end, all support should be delivered in the open forums.

---

### Post by grace3 on 2016-04-06
> **QIII said:**
> Please do not ask for help via PM.

Any solution or explanation is then lost to the community.  The Forums do not exist simply so that individuals can get help - which of course they do.  But our purpose here is to provide solutions and advice for the entire community.

To that end, all support should be delivered in the open forums.

Wow, this kind of close and immediate surveillance is just nuts!!! Forget this NSA Distro.........

---

