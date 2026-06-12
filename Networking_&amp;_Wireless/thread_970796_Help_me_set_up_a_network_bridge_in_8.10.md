---
title: "Help me set up a network bridge in 8.10"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Joe of Parma on 2008-11-04
So 8.10 is the first version of Ubuntu that installs on my laptop, and overall I'm enjoying the experience for the most part. However, I've run into a little trouble trying to set up a network bridge.

Under Vista I was getting wireless internet and then sharing it with my Xbox 360 via my ethernet port. I was told to use Firestarter to bridge my two connections, but I can't get that working - it always says that eth0 (my NIC) is not ready. Is there any way to fix this, or a better/easier way to do it through the terminal?

Thanks in advance. :)

BTW: I don't really know much about Ubuntu yet - still kind of learning the ropes. Let me know if any other information I can provide would be helpful.

---

### Post by nixscripter on 2008-11-04
This is the command line method which usually works for me:

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

Hope this helps.

---

### Post by Joe of Parma on 2008-11-05
That method failed for me here:

route add default gateway <default gateway ip address>
dhclient <bridge name>

I did the first of those commands and it said that "route" wasn't a command, and I tried it with sudo and I got the same message. Then I did the dhclient command and it basically said "looking for DHCP servers 255.255.255.255" and eventually stopped after doing that eight or nine times.

---

### Post by nixscripter on 2008-11-05
Route wasn't a command? That's a new one. Try **/sbin/route** instead.

And if it doesn't work, the rest of it won't either. This part is necessary to let the dhcp client (the next step) know what address to use.

---

### Post by Joe of Parma on 2008-11-05
Sorry, I slightly misreported the error message last time:

root@joptop:~# route add default gateway 192.168.1.1
SIOCADDRT: No such process
root@joptop:~# /sbin/route add default gateway 192.168.1.1
SIOCADDRT: No such process

:-[

---

### Post by Joe of Parma on 2008-11-06
Blah, anyone have any advice on this? I'm slowly pondering the thought of getting out the ol' Vista disc :(

---

### Post by nixscripter on 2008-11-06
Oh, that error message is quite different. That means it can't decide what interface to use. Please post the output of ```
ifconfig -a
```.

---

