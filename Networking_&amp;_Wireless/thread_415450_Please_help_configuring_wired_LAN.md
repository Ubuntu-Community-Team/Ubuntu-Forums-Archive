---
title: "Please help configuring wired LAN"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by O-pos on 2007-04-20
I need access to the internet and they gave me these parameters to enter in my computer

ip= 
gateway= 
subnet mask= 
dns1= 
dns2= 

I have Ubuntu 6.10 and can't update to 7.04 without broadband internet. I tried to configure the network parameters myself, but it doesn't work. Here's what I did:

I disabled all wireless connections, enabled wired conection in System>administration>Networking>Network settings. 

After this didn't work, I searched internet and opened following files:

/etc/network/interfaces
/etc/resolv.conf

in the first file, I removed # from 
# auto eth0
# iface eth0 inet dhcp
and changed them to following:
auto eth0
iface eth0 inet static
address 1****
netmask 1******
gateway 1****

in the second file there were two addresses 
nameserver 1******
nameserver 1*****
there I changed the numbers to dns1 and dns2, respectively

Then I restarded again and tried, but still doesn't work.

Any Ideas what should I do now? please use primitive language, as I don't understand much in Linux :(

---

### Post by bukwirm on 2007-04-20
If you run thse commands:

sudo ifdown eth0
sudo ifup eth0

do you get any error messages?

---

### Post by O-pos on 2007-04-20
No, apparently it doesn't work:

wacho@wacho:~$ sudo ifdown eth0
Password:
/etc/network/interfaces:29: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
wacho@wacho:~$ sudo ifup eth0
/etc/network/interfaces:29: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
wacho@wacho:~$

---

### Post by bukwirm on 2007-04-20
Can you post your /etc/network/interfaces file?

---

### Post by chili555 on 2007-04-20
In primitive language, please issue the following command and post the entire ouput:```
cat /etc/network/interfaces
```As well, I'd like to see:```
cat /etc/resolv.conf
```I think we can fix it pretty easily.

---

### Post by O-pos on 2007-04-21
Here is the output:


```

wacho@wacho:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 10.16.****
netmask 255.255.****
gateway 10.16.*****

##auto eth2
#iface eth2 inet dhcp

##auto ath0
#iface ath0 inet dhcp

##auto wlan0
#iface wlan0 inet dhcp











iface eth0 inet static
address 10.16.****
netmask 255.255.****
gateway 10.16.*****

auto eth0
wacho@wacho:~$ cat /etc/resolv.conf
nameserver 10.3.****
nameserver 10.17.****
wacho@wacho:~$ 

```

---

### Post by O-pos on 2007-04-21
no ideas? at least can anyone post deafult content of interfaces and resolv.conf? there's problem in opening these files when I write sudo gedit etc/resolv.conf or /etc/network/interfaces I get empty files without text, and when I try to modify them I get something like this: "problem occuder: file not found"

---

### Post by chili555 on 2007-04-21
A couple of ideas here. First, your interfaces file you posted contains a conflict. Although it states eth0 will be started with DHCP, you've specified an IP address, netmask and gateway. You also have two entries for eth0. Please amend /etc/network/interfaces exactly to the following:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.16.****
netmask 255.255.****
gateway 10.16.*****

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```
Assuming the DNS server addresses are correct, your /etc/resolv.conf looks correct.

When you try to edit an existing file and you get an empty file in gedit, it's because you have mistyped or misspelled the title, just as you did above. There should be no file called etc/resolv.conf but there *is* one called **/**etc/resolv.conf. That preceding slash mark has a very specific and needed meaning. A common error people, even me, make is typing ect when it's really etc.  Neatness counts.

---

### Post by O-pos on 2007-04-21
ok, I did that and changed the interfaces file.DNS server addresses are also correct, but it doesn't work. even when I ping 127.0.0.1 and 127.0.1.1 I  get "network is unreachable" :(

When I went to System>administration>Networking>Network settings, wired network was allowed, however, empty - didn't contain addresses. I entered them again, and that caused again the duplicate effect in /etc/network/interfaces.

Complicated situation, isn't it?

---

### Post by chili555 on 2007-04-21
Please return the */etc/network/interfaces* file to the text above and do:```
sudo /etc/init.d/networking restart
```Post the output, please.

---

### Post by O-pos on 2007-04-21
I did, here's the output:

```

wacho@wacho:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces" 
```

Then I tried do display interfaces content, and it seems normal:

```

wacho@wacho:~$ cat /etc/network/interfaces
&#65279;auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.1***
netmask 255.25***
gateway 10.1****

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
wacho@wacho:~$ 

```

---

### Post by chili555 on 2007-04-21
Either the address and the gateway are the same, for example:```
auto eth0
iface eth0 inet static
address 10.1.0.1
netmask 255.255.255.0
gateway 10.1.0.1
```Or one or both is mal-formed, like 10.1.12 instead of 10.1.0.12. There should be three dots separating four groups of numbers. Please recheck the information your ISP gave you.

---

### Post by O-pos on 2007-04-22
all numbers contain three dots, the address and gateway are not the same, I ckecked, there's difference in digits after third dot. ping 127.0.0.1 and 127.0.1.1 do not work again.

If you want, I can send you the full numbers in PM.

---

