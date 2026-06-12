---
title: "Static IP in 9.04sudo gedit"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by rodh on 2009-08-11
I just got my internet set to a static IP by my ISP, It is set up in the router, but I cant get on with Jaunty. I tried to set the address by clicking edit connections but I am unsure why it never gets to where the Apply button in not grayed out. I have attached a file with the ifconfig text. 
 
And here are my Router settings
 
IP:                      65.74.80.223
Gateway:            65.74.80.1
Subnet Mask        255.255.240.0
Stqatic DNS         209.165.1.12

---

### Post by DGortze380 on 2009-08-11
> **rodh said:**
> I just got my internet set to a static IP by my ISP, It is set up in the router, but I cant get on with Jaunty. I tried to set the address by clicking edit connections but I am unsure why it never gets to where the Apply button in not grayed out. I have attached a file with the ifconfig text. 
 
And here are my Router settings
 
IP:                      65.74.80.223
Gateway:            65.74.80.1
Subnet Mask        255.255.240.0
Stqatic DNS         209.165.1.12

If you're using a router, you'll need to set a private IP on your Ubuntu machine and use NAT or PAT to get on the internet.

If you want to use your ISPs settings directly, then skip the router and just configure Ubuntu with the settings you posted above. I would not suggest this.

What kind of router? Maybe we can explain a little better what you'll need to do.

---

### Post by rodh on 2009-08-11
Lynksys wrt54g

---

### Post by DGortze380 on 2009-08-11
> **rodh said:**
> Lynksys wrt54g

ok, so you'll have to configure the static IP on the router.
Just use DHCP inside unless you have a need for static addresses.

Why the static from your ISP? Are you trying to run a server? That will be a little different.

---

### Post by rodh on 2009-08-11
No tech support is trying to figure out why it keeps loosing the IP when I am trying to download updates or other larger files.  They gave me a static IP to see if it will lock in and stay.  How to set up internal dhcp

---

### Post by kambrik on 2009-08-11
DGortze380 is right you do need the internal lan ip address of your router. Since it is a WRT54G just use a web browser and log in to your router (default: 192.168.1.1)

Under Setup > Basic Setup scroll down till you see "Network setup" then "Router IP".  That is the routers internal lan ip.

Under that is what the DHCP is set to. So fool around with those and see what you come up with.

Also check this article out on how to set a static ip on Ubuntu.
[http://www.compuhowto.com/linux/ubuntu/ubuntu-static-ip/]("http://www.compuhowto.com/linux/ubuntu/ubuntu-static-ip/")

---

### Post by rodh on 2009-08-11
Tryed that, not sure where or what to change. I also no longer have anything but MAC Address showing in ifconfig.
New Attachment ifconfig2
 

Under Router IP 198.162.1.1
DHCP Enabled
Starting IP 198.162.1.100
Max Number DHCP Users 4
Client Lease time 0  (0 Means 1 day)
WINS 0 0 0 0
Time Zone GMT -09:00 AK

---

### Post by rodh on 2009-08-11
Well small change in things,  the router sees me, the ubuntu machine shows up twice in the routers IP Tables

---

### Post by kambrik on 2009-08-11
rodh - Did you set your Ubuntu server to a static ip?  If not if your using dhcp do

dhclient to make it get the ip info from the dhcp

But if you set it to a static ip also make sure it is in the range of the dhcp scope. Since the router sees you what is the current problem?  Are you able to ping compuhowto.com? If not then we need to adjust your dns/nameserver settings under ubuntu.

---

### Post by rodh on 2009-08-11
Thanks for all the info,  I just got off the phone with the ISP and the Tech that set me up with the static IP got the DNS server address wrong, The tech this evening was very patient and was able to figure out where things went wrong.  I should not have had any problems in the switch over to Static because my LAN did not change.  Just the setting of the router for internet access.  And with the help of Tech's at Linksys and my ISP we are now back online.  No wonder nothing worked in ifconfig or Network Manager.  I hope I never have to go through that again.

---

