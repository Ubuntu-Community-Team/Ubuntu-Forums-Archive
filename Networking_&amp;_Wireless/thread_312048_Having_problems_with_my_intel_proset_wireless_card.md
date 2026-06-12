---
title: "Having problems with my intel proset wireless card help"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by rdxdude on 2006-12-03
Help I have been lurking around the forums for something that looks like my problem.  I am on a laptop running edgy with a intel proset wireless.  I think i got the driver which was the ipw2200 because i can do somestuff like iwconfig iwlist and can connect to a specific essid.  The problem arises when it determines the ip address.  It just times out and doesn't get one.  If anybody can help that would be great.  Thanks.

---

### Post by rdxdude on 2006-12-04
bump please help anyone

---

### Post by Sponge34 on 2006-12-04
hi,
I have been having loads of issues with the intel card - turns out for some reason it was being set up as eth1 instead of wlan0. I changed the config file for that and now it associates ok with the AP but dhclient doent run on boot.... however if I use swscanner to associate with the AP the card stays online OK....

now you are going to ask what file did I change :( it was somewhere in /etc... it is iftab... change where it says eth1 to wlan0 and restart the networking.

For some reason bits of Ubuntu don't like eth1 to be wireless.....

HTH

S.

---

### Post by rdxdude on 2006-12-04
tried changing it, but it doesn't work.  It just says error while getting interface flags no such device.  any help would be great.

---

### Post by rdxdude on 2006-12-05
bump.  Help would be great don't know what the problem is.

---

### Post by yopnono on 2006-12-05
intel wifi should be eth0 or 1 and it's detected automatic.
You can try this.
[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

---

### Post by rdxdude on 2006-12-05
yeah it works thanks but why does the connection manager work while when i tried doing it using the command line it didn't work at all all it did was associate and then not get an ip address.

---

### Post by yopnono on 2006-12-06
don't know you maybe are doing something not right

---

### Post by rdxdude on 2006-12-06
i have looked at all the guides and did what is said to do.

---

### Post by trubblemaker on 2006-12-06
are you up and running? Or are you still trying to get it to work?
post this output and I'll try and help you:
```

cat /etc/network/interfaces
iwconfig
iwlist scan 
ifconfig 
sudo iwconfig eth1 essid any
iwconfig 
sudo dhclient eth1

```

---

