---
title: "Excellent wireless solution (tested with intel pro3945)"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by unoodles on 2008-02-20
Ok I have an inspiron 1420 from dell with ubuntu preloaded.

When i would first connect to a wireless network (just clicking the nm-applet and connecting) everything worked fine. But after the second time it would just not work.

This was not too much of a problem, as I could just do a manual configure and use dhcp. But this would fail alot and give no internet access. It would create a virtual interface called eth1:avahi.

So i finally found a way past it. If you have any of these problems you should give it a shot.

1. Open System->Administration->Network (or use the nm-applet)
2. Click on your wireless interface then hit properties.
3. Uncheck roaming if it is checked, then select your network from the drop-down list.
4. (optional) Enter your password.
5. Now select static ip address and type an address, At the public wifi spot i use i set mine to 192.168.208.xxx though sometimes i use 192.168.0.xxx. heck, it may not matter what you enter!
6. (optional) Start up firestarter.
7. now the magic. type:
 sudo route add -net 169.254.0.0 netmask 255.255.0.0 dev eth1 metric 99
8. more magic type:
 sudo route add default dev eth1 metric 99
9. now you should have a perfect working connection.
10. if not click on the DNS tab in network settings and set your DNS (if you dont know try 192.168.0.1)

As mentioned in the title I have tried this only with a intel pro 3945 card, but I could work with others.

---

