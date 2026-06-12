---
title: "two ip's"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by su_penguin on 2010-11-11
Hello all,

I have a public IP and private IP and instead of NAT'ing the public to the private I'd like to use both of them on my network config file(if possible). I only have one eth0. Is this possible?

Thanks,
Pengu

---

### Post by Whiteice on 2010-11-11
What are you trying to accomplish with these two ip's. everyone has two ip's one public setup by your ISP and then a local modem/router address for you computer/computers.

---

### Post by toekneewood on 2010-11-11
Never done this before but here goes.  In a terminal
```

sudo nano /etc/network/interfaces

```


Add the following to the end of the file.  You will need to change the IP data to match yours
```

# The primary network interface Private
auto eth1
iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

# The primary network interface Public
auto eth1
iface eth1 inet static
address 73.0.0.2
netmask 255.0.0.0
network 73.0.0.0
broadcast 13.0.0.255
gateway 73.0.0.1

```

Then "Ctrl+x" press "y" and press enter

Then
```

sudo /etc/init.d/networking restart

```

Then do this to see the settings
```

ifconfig

```

If this did not work you will need to remove the IP settings and run "sudo /etc/init.d/networking restart" to get back to a working state

---

### Post by CharlesA on 2010-11-11
If you don't have a static external IP, you'd need to use this instead:

```
iface eth1 inet dhcp
```

You'd still have to use NAT to go between the two interfacesl since private IP's aren't allowed on the internet.

Since the OP only has one network card, that wouldn't work.

@OP: What are you trying to accomplish exactly?

---

