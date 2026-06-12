---
title: "editing dhcpd.conf using shell or perl script"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by cpyder on 2008-06-23
Hi,

I have setup a network at my workplace. We have around 10 PCs in the network, the dhcp server is running on Ubuntu 8.04 - server edition.

I want to reserve the ip addresses based on the MAC addresses of clients. I have a list of hostnames and thier MAC addresses ready. We are expecting a few more machines in some time.

 I dont want to spend entire day, writing the same configuration lines over and over again. (not to mention time needed for debugging to correct for a small typo :-( )

So, can someone help me out in writing a perl/shell script which can read these details from a text/csv file and modify the dhcpd.conf file, in a properly formatted fashion?

Can someone help me? 

Thanks for your time..

---

### Post by nixscripter on 2008-06-26
The general form of the part of the dhcp.conf file I think you want to look at is:

```

host atlantis {
  hardware ethernet 00:11:22:33:44:55;
  fixed-address 10.1.1.2;
}

```

So if you had a file of the form: ```
atlantis,00:11:22:33:44:55,10.1.1.2
```

A simple perl script would be like this, off the top of my head:
```

#/usr/bin/perl -n

chomp; 
@items = split /,/; 
print "host $items[0] {
hardware ethernet $items[1]; 
fixed-address $items[2]; 
}";

```

Understand that you would still have to set up things like logging, subnets, and ddns updates.

Hope this helps.

---

