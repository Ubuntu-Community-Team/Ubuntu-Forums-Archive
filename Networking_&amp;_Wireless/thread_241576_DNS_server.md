---
title: "DNS server"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by Mr.er on 2006-08-22
my new install of ubuntu keeps setting the dns server to the routers ip. I then go into settings to set the dns servers properly and the internet works fine, but then ubuntu resets the dns server back to 192.168.1.1 rendering the internet useless. Note that entering ip adresses still works.

is there a way to get out of this?

any help appreciated.

---

### Post by Mr.er on 2006-08-22
just loaded the dns settings into my /etc/resovle.conf

works fine now.

---

### Post by BrowneR on 2006-08-22
I have a suggestion for you that may do the trick:

(I suggest you backup the files before you make changes)

You want to stop your machine from getting its DNS servers over DHCP and overriding the one you have set manually.

To do this edit your /etc/dhcp3/dhclient.conf 
```
sudo nano /etc/dhcp3/dhclient.conf
```

 find the section looking like this:

```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

```

remove "domain-name-servers," from that section and save the file with ctrl+x, Y, Enter.

now you need to set the correct DNS servers in the file /etc/resolv.conf (sudo open it and add them one per line).

This way they wont get changed when you grab an IP via DHCP.

Let me know how you get on.

---

### Post by BrowneR on 2006-08-22
oh haha i just saw your last post - guess you beat me to it :p

glad its working for you now.

---

### Post by Mr.er on 2006-08-25
yeh but now i find that they get reset to my routers ip on reboot. Ill try your tip, hope that will stop the rewrite at boot.

---

### Post by prands on 2007-01-02
Hi Guys,

I am having the same issue with 6.06.1. Except after I make all the changes they get changed back again, am I doing something wrong? Thanks

Paul

---

### Post by 454redhawk on 2007-01-02
Ping all 4 of these address, find the fastest 2 and make them your primary and scondarry DNS's. (optional if you want to use your own)

4.2.2.2 and 4.2.2.1 and 208.67.222.222 and 208.67.220.220 (optional if you want to use your own)


Edit the /etc/resolv.conf file and add your DNS values.

Then apply this
```
sudo chattr +i /etc/resolv.conf
```

That will lock down that file and prevent overwriting.

To unlock it, 

```
sudo chattr -i /etc/resolv.conf
```

This has created much disscussion and would appear to be a bug. It seems alot of people are having a similar problem (myself included). The above is a fix that has worked for me and others.

---

### Post by prands on 2007-01-03
Thanx RedHawk!

It worked a treat!

Paul

---

### Post by Ux64 on 2008-02-15
Hmm. What if I want to use temporarily another DNS server? 

I have tried using networking tab and set my own DNS rows there. But after that DNS doesn't seem to be working at all.

Is there any commandline command to just set DNS servers "on-line" when I still keep using DHCP for other IP related information?

What's the easist way on commandline to see what DNS servers I'm using right now?

- Thanks!

---

### Post by gordintoronto on 2008-03-28
Thanks, Browner!

---

### Post by Eiríkr on 2008-03-28
Consumer-grade routers with DHCP servers turned on will almost always automatically specify that DHCP clients should use the router as the DNS server.  The router then forwards DNS requests to whatever DNS server it got assigned via its own DHCP client request to your ISP.  

If you want to use a different DNS server IP address, it's actually easier and less error prone to change your router's DHCP server settings to provide the DNS server IP address of your choice to DHCP clients.  Changing your dhclient.conf file works for that one machine, but any other DHCP clients on your router will still be getting the router's DNS IP address.  Moreover, if you ever have to reinstall or do anything that might replace your dhclient.conf file, you're right back to getting the router's DNS IP address again.  And if you're anything like me, by the time that happens, you will have forgotten all about this thread, and you'll be scratching your head trying to remember how the heck you set up your DNS IP address last time.  ;)

Cheers,

Eiríkr

---

### Post by alex sun on 2008-05-23
Thanks a lot!
Works greatly!

---

