---
title: "Can't access Workgroup if I boot up wireless"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by whitetrash on 2007-05-22
Hi Everyone,

I have a problem and I haven't been able to find a fix for it yet.

I have a home network consisting of my Ubuntu laptop and 2 Windows XP boxes. I have shared files on my Windows machines that I can access just fine from Ubuntu - as long as I access them via a wired connection for the firs time. I can then go wireless and access the shares no problem. However, if I boot up and go wireless right away, I can't access any of my network shares. I get this error:

The Folder Contents Could Not Be Displayed
Sorry couldn't display all the contents of "Windows Network [name of PC].

I can ping the machines in question, I can even access them remotely using the internal network IP (192.168.x.x) but I can't access the shares.

Is there a security feature I need to enable (or dissable) - it's just really odd because it works fine when I'm wired.

Could this entry in SAMBA have anything to do with it:
#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


Any help would be much appreciated.



Thanks.

---

### Post by whitetrash on 2007-05-22
I just noticed I CAN see\access my Ubuntu share from Windows.

---

### Post by tact on 2007-05-22
I had what seemed an intermittent problem accessing shares on windows boxes when using wifi at home too.  I could also access if I switched my ubuntu box to wired connection.  

Finally I worked it out (why its intermittent)...   I avtually have two wifi access points at home.  I find that if the ubuntu box and the windows box are connected to different wifi acess points the problem arises.   If both boxes are on the SAME wifi acess point then can share no problems.

Its not to do with subnets or routing as both access points give access to the same subnet on the private LAN. (albeit via different wifi channels)

Not sure the solution.  So I just diaabled one access point (only need one anyway).

---

### Post by whitetrash on 2007-05-22
Thanks for the reply tact.

Minds not intermittent, its reproducible. If I boot up with a wired connection, my network is 100% fine (even if I later go wireless).

But it I boot up without my wired connection and go straight to wireless I can't access my network shares from Ubuntu. I can see\access my Ubuntu shares from Windows PCs but I can't access my Windows shares from Ubuntu. In order to get Ubuntu to see the shares I have to wire in the connection and log out or restart.

I just don't understand why that one little thing won't work. If I boot up wireless first, I can surf the internet (I wrote my starting post like that) - use Terminal Server Client to control either XP machine (using the local IP - 192.168.1.x) and I can even see the Ubuntu share from those machines. I can access the files in the share, copy to it etc. I just can't make Ubuntu see the Windows Machines.

I tried going into Services and placing a check beside "Multicast DNS service discovery" - that didn't help (I'm not 100% sure what its supposed to do though ;)

I've tried rebooting a few times, nothing I can think of helps, though I'll be the first to admit, I'm quite new when it comes to Linux so it might be something simple, just nothing I know about or can find in the GUI menus.

---

### Post by whitetrash on 2007-05-22
Anyone else having the same issue or have any ideas?

---

### Post by whitetrash on 2007-06-03
Ok, I've found a solution (sort of).

If I crash X (alt + ctrl + backspace) I go back to the login screen. From there I can log back in and my network is functional. I think the reason for this is because wireless is already authenticated so as soon as the services that start on login are launching my internet is on.

My theory is that I can re-start whatever service Ubuntu uses to discover network shares, but I have no idea what that service is or how to re-start it.

Anyone have any ideas?

---

