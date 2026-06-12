---
title: "Wireless problems with Dell 1300 and Dapper Drake"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by n2htt.mike on 2006-09-28
Hi,
I am trying to the built in wireless card on a Dell 1300 to work with ndiswrapper in Dapper Drake. I have been through all of the wiki I can find, and several installs, and here is where I am:
1. I can get the latest ndiswrapper (v1.8) loaded, and it successfully loads the Dell drivers for the card. ndiswrapper reports seeing both the hardware and the driver.
2. The wireless hardware is showing up named eth1. ndiswrapper is setting up the driver as wlan0. Network setup does not see the wlan0 interface.
3. I tried either changing the name of the port (eth1) or changing the way ndiswrapper sets up its port (wlan0), but cannot find documentation that works to accomplish either.
BTW, hardwire ethernet connection works fine.
Any direction on this would be most welcome.
Thanks
Mike

---

### Post by n2htt.mike on 2006-09-28
Replying to my own message...

I found an answer that works!

See this post under how-to:

Re: HOWTO: Broadcom 4318 Wireless Cards

Mike

---

