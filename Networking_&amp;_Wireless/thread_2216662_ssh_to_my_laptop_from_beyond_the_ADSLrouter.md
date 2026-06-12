---
title: "ssh to my laptop from beyond the ADSL/router"
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by tomaasj on 2014-04-13
Dear all,

my current setup is:

Laptop A and laptop B and an ADSL/router

Both laptops run ubuntu 12.04

Both laptops are connected wireless to my ADSL/router and are capable to surf the internet.

Both laptops have static IP-addresses:  laptop A: 192.168.1.100  Laptop B: 192.168.1.101

Both laptops have OpenSSH-server installed.

I am able to make a SSH connection from laptop A to laptop B, and vice versa.

So that works.

Interestingly, within my home network, the ssh command does NOT work like this (for instance from laptop A to laptop B):

```
ssh 192.168.1.101
```

I get:

```
username-laptop-A@192.168.1.101's password:
```

An unexpected result, since I expect to get:

```
username-laptopB@192.168.1.101's password:
```

It only works like this:

```
ssh username-laptop-B@192.168.1.101
```

I get:

```
ssh username-laptop-B@192.168.1.101's password:
```

By entering the password for laptop B, I can proceed.

Sofar so good.

However,

When I ask today what my public Ip address is in firefox from laptop A, I get 87.212.142.51
When I ask today what my public Ip address is in firefox from laptop B, I get 87.212.142.51

So it seems that both laptop A and B get assigned the same public Ip address.

But my ADSL/router Device info shows:

```
Device Info

This information reflects the current status of your connection.

ADSL Link Status: 	PASS
WAN IP Address: 	87.212.142.51
LAN IP Address: 	192.168.1.1
Primary DNS Server: 	62.58.153.220
Secondary DNS Server: 	62.58.48.30
```

Question:

So how to access my laptop (laptop A) from beyond my home network with SSH ?

Any help will be appreciated,

Tomaasj

---

### Post by Lars Noodén on 2014-04-13
The will both share the same external IP because they are using the same modem.  So probably the simplest way is to use multiple ports.  Have unique external ports on the ADSL modem / router forwarded to the different machines.  Thus 22 would go to one and 2222 could go to the other.

---

### Post by tomaasj on 2014-04-13
Hallo Lars,

can you give me directions how to set unique external ports for each laptop on my modem ?  I am new to do this

---

### Post by Lars Noodén on 2014-04-13
It depends on the make and model.  So there are no generalized solutions.  You'll have to connect to it in admin mode and look at your configuration options.  Somewhere there will be a menu which will allow you to forward or redirect external ports to specific internal ip numbers and ports.  Which model of ADSL/router do you have?

---

### Post by tomaasj on 2014-04-13
my ADSL modem is: Multimedia modem DV2020

---

### Post by Lars Noodén on 2014-04-13
This might be the same:

[http://portforward.com/english/routers/port_forwarding/Davolink/DV-2020/defaultguide.htm](http://portforward.com/english/routers/port_forwarding/Davolink/DV-2020/defaultguide.htm)

If not, you'll have to poke around and experiment.  Do you have an outside computer (not on the same LAN) that you can test from?

---

### Post by tomaasj on 2014-04-13
no I do not have an outside computer right now to test it from.  I just checked out the page and I will play around with the settings.  How many portnumbers can I choose with regard ssh.  I have three laptops in my home network.  I  am playing around with two right now to have them talk to eachother through ssh.  I am totally new to this.

---

### Post by Lars Noodén on 2014-04-13
You can keep each of the laptops set to port 22 as normal.  Just on the outside ADSL/router you would have one port number per machine, forwarded to 22 on the appropriate machine.  You can basically choose what you want for the outside ports, if you're not providing any other services.  2022, 2023, and 2024 could work for example.

---

### Post by tomaasj on 2014-04-13
I will play around with the settings...

---

### Post by tomaasj on 2014-04-13
hallo Lars,

I did something like this on the settings of my modem:

```


Server Name 	External Port Start 	External Port End 	Protocol 	Internal Port Start 	Internal Port End 	Server IP Address 	Remote Host
Laptop_A 	2022 	2022 	TCP 	2022 	2022 	192.168.1.100 	
laptop_B 	2023 	2023 	TCP 	2023 	2023 	192.168.1.101 	
```

is this correct ?

---

### Post by tomaasj on 2014-04-13
I am stuck.

How to reach either laptop, each with their own static Ip address from outside my home network with SSH ?  I do not know how to tell my router to forward to a specific Ip address within my wireless home network.

Anyone ?

tomaasj

---

### Post by Lars Noodén on 2014-04-13
It looks like you've got it part way.  You need an internal destination. Internal Port Start and Internal Port End could be 22, since you are using the default on the laptops.  The Server IP Address(es) would be the internal IP addresses for your laptops.

---

### Post by tomaasj on 2014-04-13
something like this ?

(cannot get the table displayed correctly, sorry)

```
Server Name 	External Port Start 	External Port End 	Protocol 	Internal Port Start 	Internal Port End 	Server IP Address 	Remote Host
laptopA 	2022 	2022 	TCP 	22 	22 	192.168.1.100 	
laptopA2 	2022 	2022 	UDP 	22 	22 	192.168.1.100 	
laptopB 	2023 	2023 	TCP 	22 	22 	192.168.1.101 	
laptopB2 	2023 	2023 	UDP 	22 	22 	192.168.1.101
```

---

### Post by Lars Noodén on 2014-04-13
That looks about right.  You should be able to connect from outside to your machines.

```

ssh -p 2022 *xx.yy.zz.aa*

```

Should connect you to 192.168.1.100.  Depending on your ADSL router, you might not be able to test that from inside the LAN.

---

### Post by tomaasj on 2014-04-13
Now I went back to the terminal and tried to reach laptopA (the one I am working on) with ssh:

```
:~$ ssh 87.212.142.51 -P 2202
```

the Ip address is the one I obtained from what-is-my-Ip and must assume that it is the public address from my router.   The -P option for the ssh command followed by the port I want to reach: 2022

with the following result:

```
ssh: connect to host 87.212.142.51 port 22: Connection refused
```

Where do I go wrong ?

---

### Post by Lars Noodén on 2014-04-13
It should be a lowercase p to set the port.   The uppercase P is undefined.

---

### Post by tomaasj on 2014-04-13
I guess that xx.yy.zz.aa should be the public Ip address which should be my ADSL/router ?  In my case: 87.212.142.51

---

### Post by tomaasj on 2014-04-13
ok, terminal command and result :

```
~$ ssh tamas@87.212.142.51 -p 2202
ssh: connect to host 87.212.142.51 port 2202: Connection refused

```

---

### Post by Lars Noodén on 2014-04-13
Is it port 2022 or 2202?

---

### Post by tomaasj on 2014-04-13
just to make it clear:  I am trying to reach the laptopA from laptopA.  But I guess, this should not be a problem to test the configuration.

---

### Post by tomaasj on 2014-04-13
sorry:

~$ ssh -p 2022 87.212.142.51
ssh: connect to host 87.212.142.51 port 2022: Connection refused

---

### Post by Lars Noodén on 2014-04-13
Your router might not support 'hairpinning' or whatever it is called.  In order to do the test properly you might have to try from a machine outside your own LAN.  I think it will work if you  can try it from outside.

---

### Post by tomaasj on 2014-04-13
sorry.  Should be 2022.

Retyped the ssh command in the terminal but got the same reply.

---

### Post by tomaasj on 2014-04-13
OK, I will try from work.  I appreciate your help.  Thanks !

---

### Post by Lars Noodén on 2014-04-13
Remember to double-check the external IP number before leaving the house, just in case it changes with DHCP.

---

### Post by tomaasj on 2014-04-13
Yes !  Good point.  I will do that 

:p

---

### Post by tomaasj on 2014-04-14
Hallo Lars,

it worked !

I can now get into my laptop from work !

Thanks for your help

:p

---

### Post by Lars Noodén on 2014-04-14
Excellent!  

By the way, your router might also support dynamic DNS accounts so that you won't have to look up the IP number each day.  There are a number of free-of-charge services available still.

---

