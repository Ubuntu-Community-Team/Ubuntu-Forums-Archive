---
title: "strange problem with ethernet"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by Dr.Joker on 2011-05-11
Hi guys,

I have a very strange and annoying problem. When I try to connect to the Internet with a LAN cable, it doesn't work. I plug the cable in and nothing happens. But here comes the twist: it was working perfectly until yesterday! Without making any changes, yesterday I came to work, plugged in the cable into my laptop, and nothing happens. I first suspected there was something wrong with the cable, but I tried a different cable from a different outlet and nothing happens, and when I boot in to Windows it still connects automatically without any problems. To make things even stranger, I reset the computer a few times, and eventually it connected, but the next time I booted my system again no wired Internet.  I can still connect to wireless, but this kind of thing really bothers me, because I have no clue why this just suddenly stopped working. When I run

```

sudo dhclient -v eth0

```it tries DHCPDISCOVER and finally the output it gives is

```

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```But I don't understand why, and if I log in to windows I get an IP address without any problems, and everything is smooth. Any help in resolving this issue will be greatly appreciated.

---

### Post by taseedorf on 2011-05-12
Hm... try reinstalling the DHCP client....

Make sure that the network device is "up"

---

### Post by Dr.Joker on 2011-05-12
Thanks for your reply. Reinstalling dhclient was one of the first things I tried. After restarting it did connect automatically, but then the next time I restarted it did not. After that I reinstalled both ubuntu-minimal and dhclient, but it didn't help.

---

### Post by Dr.Joker on 2011-05-12
Also, if I boot into recovery mode, and choose failsafeX, it connects automatically to LAN with no problem. Someone please help, this should be a solvable problem!

---

