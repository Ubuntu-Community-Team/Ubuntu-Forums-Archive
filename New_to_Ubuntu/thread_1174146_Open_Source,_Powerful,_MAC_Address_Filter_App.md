---
title: "Open Source, Powerful, MAC Address Filter App"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by jeepfreak2002 on 2009-05-30
Hi all:

My wife is the assistant IT Administrator over 5 campuses of a local community college.  The cost of implementing a full blown network MAC Address filter package/bandwidth manager program is too great for their budget, so I was wondering if there is a network administration package available as open source.

The college basically wants to administer both a wired and wireless network,be able to grant access by MAC Address, and also be able to throttle bandwidth on every account.  

Is there an opensource product that can do this?

Thanks,

Jeepfreak

---

### Post by The Cog on 2009-05-30
You can do it with Linux if you use it as the gateway. You can use iptables to marh the packets from approved MAC addresses, and tc to then apply bandwidth restrictions. It's a bit complicated, but this howto will give you the direction:
[http://lartc.org/howto/](http://lartc.org/howto/)

You do know that it is possible to reconfigure the MAC address of a wireless card?

---

### Post by niteshifter on 2009-05-30
Hi,

Not only wireless, but wired as well. Here's how:
```
ifconfig eth0 down
ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX
ifconfig eth0 up

```
where XX:XX:XX:XX:XX:XX is whatever MAC you'd like to use.

MAC address filtering is not the panacea most people think it is. Not saying you shouldn't implement it - it will keep the script kiddies out (maybe) - but it's no obstacle to the higher skill level types.

---

### Post by durand on 2009-05-30
Maybe coyote linux is what you want? I don't think you can have load balancing and stuff without routing the traffic through the linux box.

[http://coyotelinux.com](http://coyotelinux.com)

---

### Post by jeepfreak2002 on 2009-05-31
thanks all - I appreciate it.  I will look into that coyote linux today.

I was not aware of the ability to change you MAC address, but unless someone shares their approved MAC address and you change your MAC to theirs, what's the big deal?  I agree that it is a vulnerability, but I don't know of any other way to screen networks, and to monitor bandwidth.

---

### Post by jeepfreak2002 on 2009-05-31
> **durand said:**
> Maybe coyote linux is what you want? I don't think you can have load balancing and stuff without routing the traffic through the linux box.

[http://coyotelinux.com](http://coyotelinux.com)

Well, that site says that it is for networks under 200 users, the college has thousands of users...

---

### Post by durand on 2009-05-31
Hmm, you could try posting on their forums. They might be able to help you more than we can: [http://forums.coyotelinux.com/](http://forums.coyotelinux.com/)

You could also try the networking or server categories on this forum:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

---

### Post by jeepfreak2002 on 2009-05-31
> **durand said:**
> Hmm, you could try posting on their forums. They might be able to help you more than we can: [http://forums.coyotelinux.com/](http://forums.coyotelinux.com/)

You could also try the networking or server categories on this forum:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

Can a Moderator push this thread to the networking forum?  Maybe that is where I need to take this question...

---

