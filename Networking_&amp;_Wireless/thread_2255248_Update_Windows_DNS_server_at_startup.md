---
title: "Update Windows DNS server at startup"
date: 2014-12-03
forum: Networking &amp; Wireless
---

### Post by Romu on 2014-12-03
Hi,
I've 2 Ubuntu 14.04 servers which update my Windows Active Directory DNS server at startup.

This works well by adding to the **/etc/rc.local**, the following lines:

```

echo "update delete {myhostname}.{my suffix}" > /home/user/nsu
echo "update add {myhostname}.{my suffix} 86400 a {my ip}" >> /home/user/nsu
echo "send" >> /home/user/nsu
nsupdate -v /home/user/nsu
```

This works like a charm. Notice the IP address is not hard coded but retrieved through a regular expression (not the purpose of my question).

Now, I need to do the same with Xubuntu 14.04. I proceed exactly the same way and....nothing, the DNS server is not updated at all.

The nsu file is well created with the right information. And if I manually run **nsupdate -v nsu**, it works. Any idea?

Thanks.

---

### Post by JKyleOKC on 2014-12-03
With all the emphasis on booting as rapidly as possible, there's a good chance that rc.local is executing before the network is fully available although it's supposed to be the very last thing done during the boot process. It sounds to me as if this may be what is happening to you.

I would try introducing a "sleep" command between the three "echo" commands and the actual attempt to do the update, in rc.local itself. This will slow down the boot process, of course, but if that makes it work again would tend to confirm my suspicions. I'd start with a value of 30 to 60, and reduce it via trial and error to the smallest value that still works reliably...

Hope this helps!

---

### Post by Romu on 2014-12-04
That sounds a pretty good idea, boot time is not an issue on this case. Let you know.

Thanks Jim.

---

