---
title: "Getting wifi to work on HP Pavilion dv6000"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by jhall124 on 2008-09-04
I seen this on [http://madwifi.org/ticket/1192#comment:337](http://madwifi.org/ticket/1192#comment:337)

I didn't have to perform step 7. Here's what it took:

1. wget http: / /snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
2. tar -zxvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
3. cd madwifi-hal-0.10.5.6-r3835-20080801
4. sudo make
5. sudo make install
6. System -> Administration -> Hardware Drivers -> Uncheck both hal and Atheros support
7. sudo vi /etc/modprobe.d/blacklist -> blacklist ndiswrapper (This is because I was using ndis, but it was a gimpy solution)
8. Reboot =(, so windows-y... ick
9. sudo modprobe ath_pci
10. Surf surf surf

I'm not sure who the aurthur is but whomever you are, THANKS !!!

---

### Post by biggest lund on 2008-09-04
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

