---
title: "ifcfg-eth1 location?"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Dylnuge on 2008-05-08
Hello,

I recently tried messing around with my ifconfig command and realized that:
```
sudo ifconfig eth1 down
```
followed by
```
sudo ifconfig eth1 up
```
will not reboot the Ethernet device completely, leaving me unable to reconnect to the internet.

I have not yet tested it, but I believe that this is a result of the DHCP protocal not being recalled. I will run a dhcpcd afterwords to test it.

However, I did look for my /etc/sysconfig/network-scripts/ifcfg-eth1 file. Of course, I am aware this isn't a red-hat system, but I couldn't even get as far as the sysconfig directory. Where is the ifcfg file located in Ubuntu?

Thanks,
Dylan

---

### Post by unutbu on 2008-05-08
I think the equivalent on Ubuntu is /etc/network/interfaces.

Some commands which may (or may not) be useful:

```
sudo /etc/init.d/networking restart
sudo /sbin/dhclient-script

```

---

### Post by Dylnuge on 2008-05-08
Thanks.

I don't seem to be right on dhcp being the problem though. I ran DHCLIENT after shutting down and turning on the ethernet device, but it still didn't help.

Anyone have any suggestions on why this mught be?

---

### Post by chili555 on 2008-05-08
> I did look for my /etc/sysconfig/network-scripts/ifcfg-eth1Debian based systems are very different from Red Hat systems. Wait, are all those ladies wearing red hats pushing Linux? No, probably not.

The file that is closest is */etc/network/interfaces*. However, in a system running Network Manager, which is installed by default, *interfaces* contains next to nothing. NM controls all those details.

You might try:```
sudo ifdown eth1 && sudo ifup eth1
```I fear I may have provoked more questions than I answered.

---

### Post by unutbu on 2008-05-08
If you'd like to try your hand at a CLI approach to networking without Network Manager, check out kevdog's excellent guide:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

At the end it also provides a nice list of useful commands.

---

### Post by Dylnuge on 2008-05-10
So is there a way to instruct NM to send eth1 down for a minute, then bring it back up and reconnect?

Oh, and ifdown/ifup don't do anything (I get an eth1 not configured error).

---

### Post by unutbu on 2008-05-10
I don't think I understand your situation very well. 

It sounds like you start with a wireless internet connection, but then perhaps the connection is lost and you are looking for a way to reconnect. Is that right?

Or are you starting with a working connection and want to bring down the network yourself, wait for a minute, and then restart?

I'm perplexed that you get a 

```
ifdown: interface eth1 not configured
```

error, because I think you would not normally see that error after you've got a working connection (or even if the connection is lost).

---

