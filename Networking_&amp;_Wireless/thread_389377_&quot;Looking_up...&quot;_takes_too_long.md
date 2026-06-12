---
title: "&quot;Looking up...&quot; takes too long"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by ouff on 2007-03-20
I have an odd problem.  I'm running Edgy on a laptop with an Intel wireless card.  I use network manager to connect to WPA protected wireless networks.  Regardless of the network I connect to, it takes a very long time for Firefox to get past the "Looking up [website]..." message.  There is a similar delay with other internet applications.  Once it gets past this stage, the page downloads reasonably fast, though not as fast as I would expect.  When I reboot in Windows on the same computer and connect to the same network, there is no delay and downloads are faster.

I suspect there is something wrong with the way Ubuntu's DNS lookup settings, but I'm not a networking or Linux expert, and am not sure how to proceed.

Any thoughts?

---

### Post by Mr. C. on 2007-03-20
Most likely your router is providing itself as a DNS server.

You can confirm by looking at the file /etc/resolv.conf in a terminal window, that it currently contains the IP address of your router.

Configure it to supply your ISPs DNS servers instead.  If you cannot do that, configure Ubuntu to use your ISPs DNS servers directly, in System->Administration->Networking on the DNS tabs.

MrC

---

### Post by wieman01 on 2007-03-21
You need to disable IPV6 globally (there are thread concerning this problem) and also disable it in Firefox (if you are using it). Search for a corresponding threats in here and you'll know what I mean. That will boost your system.

---

### Post by ouff on 2007-03-21
K, so I checked that, and you were right.  My router was my DNS lookup address.  I switched to OpenDNS and it worked fine.  However, when I restarted, it went back to my router's ip address.  Also, if I don't want it to use Open DNS all the time, how do I set up the computer to bypass the router's ip address and get the DNS ip's from the ISP?  This happens on every network I join (four different ones so far) and Windows handles it fine, so I imagine there's a way.  I just don't know enough to take your previous advice.

Thanks

---

### Post by wieman01 on 2007-03-21
> **ouff said:**
> K, so I checked that, and you were right.  My router was my DNS lookup address.  I switched to OpenDNS and it worked fine.  However, when I restarted, it went back to my router's ip address.  Also, if I don't want it to use Open DNS all the time, how do I set up the computer to bypass the router's ip address and get the DNS ip's from the ISP?  This happens on every network I join (four different ones so far) and Windows handles it fine, so I imagine there's a way.  I just don't know enough to take your previous advice.

Thanks
Check out IPV6. I think this will make a difference.

---

### Post by wieman01 on 2007-03-21
_Check this out:_

[http://ubuntuforums.org/showthread.php?t=6841]("http://ubuntuforums.org/showthread.php?t=6841")

---

### Post by Mr. C. on 2007-03-21
You will get much better results by configuring your router with your ISPs DNS server, and if possible, turning off your router's caching-DNS service (it may not have an option to disable).

There are a number of factors that can be causing the issue; it will occur only with DHCP enabled and your client obtains its information via DHCP.

One or more of these remedies might be required to resolve the problem:

1) your router might need its firmware updated
2) your router might allow you to disable its local caching DNS server
3) ensure your router is configured with your ISPs DNS servers.  If your router gets this information dynamically, it should show you the 1 or 2 DNS servers it obtained.  Check the router.
4) Be sure you've entered your ISPs DNS information in the DNS tab of System->Administration->Networking

Alternatively, you may configure your IP information to be static.  Change Network Manager's IP information from DHCP to Static, and supply the correct information.  Be sure to fill out the DNS tab.

Let me know if you need more info.  If so, also provide your router make, model, version, and firmware version.

MrC

---

### Post by stchman on 2007-03-21
> **ouff said:**
> I have an odd problem.  I'm running Edgy on a laptop with an Intel wireless card.  I use network manager to connect to WPA protected wireless networks.  Regardless of the network I connect to, it takes a very long time for Firefox to get past the "Looking up [website]..." message.  There is a similar delay with other internet applications.  Once it gets past this stage, the page downloads reasonably fast, though not as fast as I would expect.  When I reboot in Windows on the same computer and connect to the same network, there is no delay and downloads are faster.

I suspect there is something wrong with the way Ubuntu's DNS lookup settings, but I'm not a networking or Linux expert, and am not sure how to proceed.

Any thoughts?

I did not think Edgy supported either WEP or WPA.  I know that Feisty will OOB.  How do you get Edgy to support WEP or WPA?

Thanks

---

### Post by marvlowe on 2007-03-21
I having the exact same problem with Firefox taking a long time to look up websites. I would like to try the solution mentioned for IPV6 but how does one  go about disabling IPV6 globally?

---

### Post by Mr. C. on 2007-03-21
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by marvlowe on 2007-03-21
Thanks forat the help, disabling IPV6 worked for me. Firefox Browser speed is now great.

---

### Post by Mr. C. on 2007-03-21
You're welcome.  Enjoy the system!

MrC

---

