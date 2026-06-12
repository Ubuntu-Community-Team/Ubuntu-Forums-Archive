---
title: "Ubuntu Server 14.10 No Ethernet Device"
date: 2014-11-09
forum: Networking &amp; Wireless
---

### Post by marco-mattei on 2014-11-09
Hi

So, I have a pretty bad problem...

The thing is, I bought a new router and it gave my server a different IP as before, which was not ideal. So I've tried to update my Ethernet configuration from DHCP to a static IP, in order to give it the same one as before. 

On my server is Webmin installed, so I did the configuration through webmin, as I did many times before. But aparently something went wrong, because now I don't have an Ethernet Device. Before there was one of course (called em1 or something like that, it was not called ETH0) but now, all I see if I do an ifconfig is the lo (loopback) device.

Okay, so my /etc/network/interfaces file looks like the following:
```

auto lo
iface lo inet loopback

```

I've tried to add auto eth0 and auto em0 but nothing worked, it just waited for 120 seconds at boot and I still had no network.

In the lspci list there is a line called:
```

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I218-V (rev 04)

```

Then, I checked, I do not have the files /etc/udev/*rules*.*d*/*70*-*persistent*-*net*.*rules and /etc/udev/[I]rules*.*d*/*70*-*persistent*-*cd*.*rules*[/I]
I did not delete them by myself, I have no idea how that could have happened.

One last info: My Hardware is a intel nuc D34010WYK

Of course I could just reinstall the whole thing, but I do not want to lose the whole configuration... Well, if I can't figure this problem out, I guess i don't have another way, but if it's possible somehow, I'd prefer to do it without a fresh reinstallation.

As allways: Thanks in advance for any help.

---

### Post by praseodym on 2014-11-09
Please run:
```

sudo udevadm trigger
sudo service udev reload
sudo service udev restart
```and check the udev files again.

---

