---
title: "VPN Help Requested"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by Permafrost91 on 2006-08-05
I have searched high and low in this forum without getting anything to work. I need to VPN into my school's network (heard that one before, I'm sure) but my school makes everything easy for Windoze and Apple users only. Here's all the info on VPNing:
[http://it.med.miami.edu/x687.xml](http://it.med.miami.edu/x687.xml)

Now, needless to say I'm running Ubuntu. I have tried vpnc and pptpconfig without any success. The first requires a group password which I don't have and was never given. The latter simply does not connect. So I'm at a loss now. Is there an easier way to connect via VPN to my school's network?

Thanks!

---

### Post by jordilin on 2006-08-05
take a look at this wonderful howto:
[http://www.popey.com/node/62](http://www.popey.com/node/62)

---

### Post by Permafrost91 on 2006-08-05
Thanks for the quick response. Now, I honestly have never worked with VPN before so I don't know anything about it but from what I've gathered here in the forums, the Cisco VPN client can only connect to Cisco VPN servers. I think the school is running MS VPN servers. On top of that, I don't have a .pcf file like the person writing this howto so I don't know what to do about that.

---

### Post by Permafrost91 on 2006-08-06
Ok, I figured out that my school uses pptp. I don't know anything else though (they haven't responded to my inquiry yet). I installed the network-manager-pptp package from linux2go repo (found somewhere else here in the forums) without any success.

---

### Post by mips on 2006-08-06
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)
[http://www.ubuntuforums.org/showthread.php?t=91249](http://www.ubuntuforums.org/showthread.php?t=91249)
[http://www.ubuntuforums.org/showthread.php?t=195416](http://www.ubuntuforums.org/showthread.php?t=195416)
[http://www.ubuntuforums.org/showthread.php?t=164975](http://www.ubuntuforums.org/showthread.php?t=164975)
[http://www.ubuntuforums.org/showthread.php?t=151186](http://www.ubuntuforums.org/showthread.php?t=151186)
[http://www.ubuntuforums.org/showthread.php?t=28396](http://www.ubuntuforums.org/showthread.php?t=28396)
[http://www.ubuntuforums.org/showthread.php?t=71860](http://www.ubuntuforums.org/showthread.php?t=71860)
[http://www.ubuntuforums.org/showthread.php?t=41331](http://www.ubuntuforums.org/showthread.php?t=41331)

---

### Post by christo:: on 2006-08-10
I know exactly what you're going through. I spent ages fighting problems with the Cisco VPN client on ubuntu - in fact I have had problems with it in the past with other distros too, so finally I gave up and started looking for a solution. The answer came in the form of VPNC, which is way better than the Cisco VPN client. I was so happy with the results that I wrote this [linux VPN tutorial]("http://www.spiration.co.uk/post/1293") which clearly describes how to get this working under linux (specifically ubuntu). I hope you find it helpful and I hope people start to forget about the whole Cisco VPN fiasco :):)

christo

---

### Post by Permafrost91 on 2006-08-11
Well, the whole Cisco VPN is nice and all but my network uses PPTP. I knew nothing about VPN before I started upon connecting to my school network and so (erroneously) attempted using vpnc first.

Thanks for all the replies though!

---

