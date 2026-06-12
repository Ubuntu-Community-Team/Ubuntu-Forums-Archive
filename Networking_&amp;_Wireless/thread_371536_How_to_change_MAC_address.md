---
title: "How to change MAC address"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by Alex N on 2007-02-27
With little help from this forum I've just installed Ununtu and solved all problems with GRUB.
Now comes another part of the quest.

I need to change mac-address of my card in order to connect to the Net. My provider
recognises computers by MAC address.

I can do it using ifconfig, and everything works fine. Now the question - where 
to place the ifconfig command so that this change will be automatic ?

I understand that unlike DOS, Linux has a quite complicated startup process.

---

### Post by slayerboy on 2007-02-27
would it not be easier to just call up your provider and ask for them to change the MAC address they have on your account?

---

### Post by txapelgorri on 2007-02-27
Hi:

There is a fast solution for your qestion. You can create a small bash script that does all the steps that you do manually. Then put it at, for example /usr/local/bin, give to it executing permission, and finally link it to be executed when the system starts. You can do this last step with:
```
sudo ln -s /usr/local/bin/change_mac.bash /etc/rc2.d/S99changemac
```
Supposing that you didn't touch the default runlevel (2).

Hope this helps, Ibon.

---

### Post by Alex N on 2007-02-27
2 txapelgorri:

Does it mean that only one user on a computer will have these changes ?

---

### Post by txapelgorri on 2007-03-01
No, all the users will benefit from that script.

Cheers, txapelgorri.

---

### Post by Alex N on 2007-03-02
Sorry, but it did not help. It does nothing. The command ifconfig eth0 hw ...
works only when the network adapter is disabled. So I think it starts in some incorrect
moment.

Currently I am disabling it manually via GUI

---

### Post by scxtt on 2007-03-02
what if you do it VERY early on - before the boot up process brings the device up?  so instead of S99, do something like S10 (or S1 or S01, whatever you can get away with) ...

---

### Post by netztier on 2007-03-02
If you are not using network-manager for that interface, you may be able to configure it via the file **/etc/inet/interfaces**.

*[COLOR="Red"]Edit: of course the correct file is **/etc/network/interfaces** [/COLOR]*

Assuming the interface in question is **eth0** , you probably have lines in that file like this:

```
[FONT="Courier New"]...
auto eth0
...
iface eth0 inet dhcp
...[/FONT]
```
change this to look something like
```
[FONT="Courier New"]...
auto eth0
...
iface eth0 inet dhcp
 hwaddress ether 11:22:33:44:55:66
...[/FONT]
```

best regards

Marc

---

### Post by scxtt on 2007-03-02
> **netztier said:**
> **/etc/inet/interfaces**shouldn't that be /etc/network/interfaces?  unless a lot has changed since dapper ...

---

### Post by netztier on 2007-03-02
> **scxtt said:**
> shouldn't that be /etc/network/interfaces?  unless a lot has changed since dapper ...

**OUCH!**

OK, you got me there! Been editing  /etc/inet/networks on my HP OpenView server all morning...

Of course the file is **/etc/network/interfaces**.


apologies,

Marc

---

### Post by Alex N on 2007-03-03
```
[FONT="Courier New"]...

...
iface eth0 inet dhcp
hwaddress ether 11:22:33:44:55:66
...
auto eth0
[/FONT]
```

Thank you. It worked.

---

