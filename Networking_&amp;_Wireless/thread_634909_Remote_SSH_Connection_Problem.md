---
title: "Remote SSH Connection Problem"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by pb3004 on 2007-12-08
Hi,

I'm trying to connect via ssh from a remote computer. Currently I can connect from another computer on my local network, but every time I try to connect through my DynDNS, or directly with my IPAddress it won't accept my password and says:
"Permission denied, please try again."

I have the following:

    * Port forwarding on port 22, from a bt voyager 2110 router.
    * DynDNS registered account, which is setup ok (i think).
    * I'm running ubuntu (obviously)
    * I have the OpenSSH client & server.


I've tried just about everything I can find in various forums but I still can't get it to work. Any ideas?

---

### Post by scrooge_74 on 2007-12-08
It has to be a forwarding port problem since you get to connect from inside.

Check that the port forwarding is sent to the correct internat ip (I had that screwed in the past), and check that you have DynDNS set up correctly (I had that screwed also)

Beside that I can't think of any reason why you can't connect

---

### Post by pb3004 on 2007-12-08
Hi, Cheers for the reply.

For DynDNS I definitly have the right IP address double checked it here [http://www.lawrencegoetz.com/programs/ipinfo/]("http://www.lawrencegoetz.com/programs/ipinfo/")


And this is my port forwarding rule.
Secure Shell Server  	ALL  	TCP  	22  	192.168.1.2  	22

And I can ssh to username@192.168.1.2 fine.

When I do:
ssh username@[my_ip], I get the password prompt, but I just says "Permission denied, please try again." when I enter my password.

---

### Post by webdr on 2007-12-08
When I do:
ssh username@[my_ip], I get the password prompt, but I just says "Permission denied, please try again." when I enter my password.[/QUOTE]

Is you caps lock on? LOL, no seriously,

This generally indicates to me that when I am sshing to a public IP, the port is forwarding to the wrong device or forwarding is not working at all.

You can test for this condition by using 
the command tcpdump -i eth0 port 22 and monitoring for packet flows during attempted accesses to ssh via the public ip, odds are, you won't see any packets, which means that your packets are not arriving to the destination you intended.

I hope this helps.
-WebDr

---

### Post by pb3004 on 2007-12-08
Hi,

Thanks for the quick reply. I do get output with "tcpdump -i eth0 port 22" when I try to connect so the port forwarding is working? any ideas?

Cheers for the "tcpdump -i eth0 port 22" btw I didn't know how to do that.

---

