---
title: "Problem with Internet Sharing using Firestarter"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by churfsan on 2008-11-04
Hello all,

I have a laptop with Ubuntu Inrepid 8.10. I connect to a wireless router to the internet. I have a desktop PC which I want to connect to Internet through the laptop.

I used Firestarter, and did the setup as per the documentation.
I am using wireless to connect to Internet
I am using eth0 (wired ethernet) to connect to my desktop (client)

When I tried to configure eth0 as static IP (as required by Firestarter),
whenever I use the network manager to set the mask to 255.255.255.0 and then click on 'OK', the mark field somehow changes to '24' or '16' - funny?

When I try to start the firewall on the firestarter, it gives a message saying that eth0 is not ready

I checked that eth0 is working by connecting it directly to the router, and it works without problem.


Any suggestions or help will be very much appreciated.

---

### Post by stewsat on 2008-11-07
I am in the same leaky boat. Using a HSDPA E169, connects fine. Set eth0 to a static IP. Same message "eth0 is not ready". Installed DHCP3-server, so that is fine. Really at my wits end. Was using an old SME mitel server with 2 eth cards. Now upgraded from slow satellite to v fast HSDPA and just want to share it with my network of 4 computers, actually 3 and a TIVO. Please help anyone..
Stew :)

---

### Post by rhcm123 on 2008-11-07
> **churfsan said:**
> Hello all,

I have a laptop with Ubuntu Inrepid 8.10. I connect to a wireless router to the internet. I have a desktop PC which I want to connect to Internet through the laptop.

I used Firestarter, and did the setup as per the documentation.
I am using wireless to connect to Internet
I am using eth0 (wired ethernet) to connect to my desktop (client)

When I tried to configure eth0 as static IP (as required by Firestarter),
whenever I use the network manager to set the mask to 255.255.255.0 and then click on 'OK', the mark field somehow changes to '24' or '16' - funny?

When I try to start the firewall on the firestarter, it gives a message saying that eth0 is not ready

I checked that eth0 is working by connecting it directly to the router, and it works without problem.

Any suggestions or help will be very much appreciated.


Two things:
1. Are you connecting directly from the Desktop to the Laptop? Or is their a switch in between? (You might need a crossover cable)
2. configure the subnet mask with:
```
sudo nano /etc/network/interfaces
```
(add the subnet to the appropriate interface)
and restart them with
```
sudo /etc/init.d/networking restart
```
Now try to start firestarter.

I ditched firestarter when it became too much of a hassle. And be sure to edit sysctl.conf to route packets!
```
sudo nano /etc/sysctl.conf
```
and you should see a line that says "uncomment the next line to enable packet forwarding for IPv4
remove the # sign from the line after it

---

### Post by churfsan on 2008-11-10
> **rhcm123 said:**
> Two things:
1. Are you connecting directly from the Desktop to the Laptop? Or is their a switch in between? (You might need a crossover cable)
2. configure the subnet mask with:
```
sudo nano /etc/network/interfaces
```
(add the subnet to the appropriate interface)
and restart them with
```
sudo /etc/init.d/networking restart
```
Now try to start firestarter.

I ditched firestarter when it became too much of a hassle. And be sure to edit sysctl.conf to route packets!
```
sudo nano /etc/sysctl.conf
```
and you should see a line that says "uncomment the next line to enable packet forwarding for IPv4
remove the # sign from the line after it
Thanks for the reply.
I am using cross cable and connecting directly between the laptop and the desktop.

I have not edited any of the files mentioned in your reply. I will have to look into that.

I have seem some eloborate HOWTO on Internet sharing in these forums also, but it involves lot of file editing and manual setup. A friend suggested that I can use Fire Starter as the easy way out.

Looks like it is not going to be so easy anyway.

Thanks again, I will post my experience

---

