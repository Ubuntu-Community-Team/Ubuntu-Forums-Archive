---
title: "Setting up usb wifi as an access point in ubuntu"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by kthdsn on 2006-10-20
Hello

I have a laptop connected to the internet via a cable.  I have a usb wifi adapter which is connected to this laptop.

What I want to do is make this usb wifi doodah behave like an access point, so that other devices can access the internet wirelessly, ie:

internet->modem->laptop->wifi->other stuff

The other stuff is a second laptop and a nintendo ds, in case that is important.  Both laptops are running edgy as of yesterday.  The usb doodah has a zydas chipset.

So far I have connected the usb wifi doodah to the laptop and given it an ESSID.  It is on eth2.

iwconfig outputs this:

```
eth2      802.11g zd1211  ESSID:"pink"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality=32/100  Signal level=32/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have no idea what any of that means, and I could use some real step by step beginner type help.  Thanks in advance :KS

---

### Post by binks on 2006-10-22
[http://www.ubuntuforums.org/showthread.php?t=151781&highlight=wifi+access+point](http://www.ubuntuforums.org/showthread.php?t=151781&highlight=wifi+access+point)


have a look at this m8 
plus to get the card into access point mode 
```
 sudo iwconfig wlan0 mode Master 
sudo ifconfig wlan0 up
```

but sub you eth id into wlan0

---

### Post by kthdsn on 2006-10-22
That post is way over my head :confused: 

When I try the command you suggested I get this:
```
kthdsn@kthdsn-laptop:~$ sudo iwconfig eth2 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; Invalid argument.

```

Further information that may or may not be helpful, in network tools there is no data shown for eth2.  It is in the list but Hardware address, Multicast etc all say "not available".

If I go into networking and fill in the ip addresses instead of choosing DHCP then network tools shows up with some data.  I'm not sure that I put the correct information in though, I don't really know what I am supposed to be entering.

I don't know if any of that is useful or not :???:

---

### Post by binks on 2006-12-12
hey sorry ive been away did you get any further with this

---

### Post by kthdsn on 2006-12-12
Sort of, I bought a router instead :D 

Thanks for checking in to see how it was going.

---

