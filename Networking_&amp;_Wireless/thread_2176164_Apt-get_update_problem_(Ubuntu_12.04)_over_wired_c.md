---
title: "Apt-get update problem (Ubuntu 12.04) over wired corporate network"
date: 2013-09-23
forum: Networking &amp; Wireless
---

### Post by a5910218 on 2013-09-23
Hi all,

I run Ubuntu 12.04 as my main office OS along with a number of other users. We operate on either a wired corporate network or on a wireless connection (those of us with laptops and wireless cards at least). For those of you in the academic world the wireless connection we use is eduroam. Over the summer a number of major changes were made to our (Windows) server due to security flaws and since then all of those users running Ubuntu (12.04) cannot update their systems over the wired connection (although the wireless connection works fine). I realise that this is not a Ubuntu problem per se but our administration run solely on windows and have no experience of running Linux systems so they are struggling. Since a number of us have to use linux systems we have to resolve this.

What we know so far:

Admin have checked and port 80 (which we believe Ubuntu uses to update through http) appears open to windows systems.

Ubuntu 12.04 systems it seems cannot see port 80 and become very slow to resolve the repository mirrors when running apt-get update eventually timing out.

Interestingly our admin checked Ubuntu 13.10 in a virtual box inside windows this morning and it updated fine. Is there some innate difference between Ubuntu 12.04 and 13.10?

Our admin suspect the antivirus inside the firewall which checks all incoming traffic is the problem.

I wonder what checks and advice can you offer so that we along with our network admin can resolve this issue?

Cheers, Matt

---

### Post by grahammechanical on 2013-09-23
There is a lot of difference between 13.10 and 12.04 but, I suspect not so much in this area that you are having problems with.

When 13.10 is run inside a VM on a Windows OS then that machine still is able to get through the firewall. That is why 13.10 is accessing the Internet. The other machines running Ubuntu are not being allowed to get through the firewall to access the Internet which they need to do to update the OS. This is my guess, although I have no advice to give on how to fix it.

I have to smile. From what I have heard, the greatest risk to network security is allowing a Windows machine access to the Internet. And here you are with Ubuntu machines that present a lesser risk and they cannot access the Internet.

I used to work in a high street store and none of our Windows machines were allowed access to the Internet. We could access the company's Wide Area Network (WAN) through which we sent and received emails, but Internet access was not allowed.

As I have already indicated, I know nothing about network servers and firewalls but you say the Ubuntu machines with WiFi can still access the Internet. So, the wireless access point/router is allowed through the firewall. That access point is connected to the server by cable. The firewall is adjusted to allow the wireless access point through to the Internet. And any machine, whatever the OS, that connects to the wireless access point gains access to the Internet.

It is my guess that each of the Ubuntu machines needs to be individually allowed through the server firewall. I think will be done by means of the address that each machine's network card has. Network cards have a network address coded into them at the time of manufacture. The rules of the server firewall have to be adjusted to allow the network addresses of these cards through the firewall.

I am again guessing that in 12.04 you need to go to Edit connections in the network icon menu and look for the Device MAC address under the Ethernet tab.

Regards.

---

### Post by houstonbofh on 2013-09-23
You could try connecting to an external VPN server.  This would bypass the packet inspection.  Or it would totally fail as it bypasses the packet inspection. :)  This is a poorly configured Microsoft tool that prevents Windows machines that are no up to a defined standard from infecting the network.  It does this my denying anything that is not on the template.

---

