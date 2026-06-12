---
title: "DNS Servers lost when rebooting!"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Rurushu on 2008-06-12
Each time I restart my laptop, I have to re-enter DNS servers!

This happened after installing kubuntu-desktop in Ubuntu!

How can I correct this?!

---

### Post by superprash2003 on 2008-06-12
follow this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Rurushu on 2008-06-12
Thanks alot...

EDIT: It didn't work! I had to re-enter the DNS Servers again after rebooting...

---

### Post by superprash2003 on 2008-06-13
go to the terminal and type **sudo gedit /etc/dhcp3/dhclient.conf** and paste the contents of the file here

---

### Post by Rurushu on 2008-06-13
It didn't work!

---

### Post by superprash2003 on 2008-06-13
the dhclient.conf file doesnt open up when you type the above command?? i want to see your dhclient.conf file.. it would be nice if you could attach it..

---

### Post by Rurushu on 2008-06-13
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

prepend domain-name-servers 217.10.162.8,217.10.160.8
```

---

### Post by jimv on 2008-06-13
What is your DHCP server?  A router or another computer?

---

### Post by Rurushu on 2008-06-13
another computer

---

### Post by jimv on 2008-06-13
OK then, did you set the DHCP scope on your other computer to include DNS servers?

Oh yeah, what kind of computer?  Linux, Windows2003, XP Internet Connection Sharing?

---

### Post by Rurushu on 2008-06-13
Windows XP...

I didn't face this problem before installing kubuntu-desktop! Is this related somehow?!

---

### Post by Rurushu on 2008-06-13
Windows XP Professional

---

### Post by jimv on 2008-06-13
Hmmmm...if you're using Windows XP ICS, then the other machine should be using 192.168.0.1 as it's gateway and DNS server.  Is DNS not working at all, or is it just not keeping your custom settings?

---

### Post by Rurushu on 2008-06-13
> Is DNS not working at all, or is it just not keeping your custom settings?

I have no problem with the DNS! It is working! The problem is that I have to re-enter the DNS Server in Network Settings--->DNS everytime I restart my laptop!

---

### Post by superprash2003 on 2008-06-13
mate you didnt follow instructions properly.. read this again [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) 
  you are supposed to end the line with a ; your line in the dhclient.conf file is just 
prepend domain-name-servers 217.10.162.8,217.10.160.8
  add a ; at the end..so the line would now become 
prepend domain-name-servers 217.10.162.8,217.10.160.8;

---

### Post by Rurushu on 2008-06-14
That still didn't work!

I still have to re-enter DNS servers when i reboot!

Any other idea?

---

### Post by jimv on 2008-06-20
What I don't understand is does DNS not work until you enter your DNS servers?  I mean, do you have to enter the DNS servers for your internet connection to work?

What are you using for you DNS servers, btw?

---

