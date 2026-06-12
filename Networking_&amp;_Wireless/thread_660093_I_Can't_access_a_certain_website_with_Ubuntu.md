---
title: "I Can't access a certain website with Ubuntu"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by VDVsx on 2008-01-06
Hi,

I have a very strange problem in my Ubuntu, I Can't access this website: [http://www.abola.pt](http://www.abola.pt)  (this is a website of a Portuguese sports newspaper). 
The website is accessible for other computer in my network using Ubuntu and to my computer to using Windows, but in the last days I lost the access in my Ubuntu. 
When I hit the page (I have Firefox and Opera) the browser wait for several minutes and after that give me a "Problem loading page".

The strange thing is, that is the only website it this behavior.

Any Clues ?

Tanks for the help.

Best regards.

---

### Post by Miademora on 2008-01-06
Try to ping your problematic website on a working and a not working ubuntu box.

ping [www.website.com](www.website.com)
dig [www.website.com](www.website.com)

Do they resolve to the same ip on both pc's?

Do ifconfig on both. Do they have the same mtu?
If not set them with sudo ifconfig eth0 mtu 1500 or whatever the working value is and try again.

to make it permanent change /etc/network/interfaces so it looks kinda like this
iface eth0 inet dhcp
post-up /sbin/ifconfig eth0 mtu 1500

and in /etc/dhcp3/dhclient.conf remove
interface-mtu

Make sure both arent using any proxies.

Or try tracepath [www.website.com](www.website.com) on both and compare the route theyre taking.

Then try w3m [www.website.com](www.website.com) from both and check if the page loads. Dont know if its installed by default on ubuntu though.

---

### Post by VDVsx on 2008-01-07
Tanks for the tips.
The tracepath in the two machines are the same.
Today I connect my Ubuntu in other network and I can reach the website, and now I can reach the site at home to, this is a very strange thing, because I don't change anything in my Ubuntu...
But now is resolve.

Best regards

---

