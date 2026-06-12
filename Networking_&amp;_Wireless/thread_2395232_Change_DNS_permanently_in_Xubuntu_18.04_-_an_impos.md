---
title: "Change DNS permanently in Xubuntu 18.04 - an impossible mission?"
date: 2018-06-28
forum: Networking &amp; Wireless
---

### Post by martago on 2018-06-28
I have already spent two days trying to figure out how to replace the ISP router address as the first DNS server, and not only ADD extra dns servers.  No matter what I do, my dns servers are always added to the ISP router address, that appears at the top of the dns servers list.  I already dealt with symbolic links to the file resolv.conf, changed resolvconf files in various directories, sudo network-admin, used the new netplan software and configuration file, etc.

In that particular computer, for security reasons, using the ISP router as dns server is not safe enough for me, so I will have to uninstall xubuntu and grub manager, and use Windows 10 solely.  It is a pity that with every new ubuntu/xubuntu release comes new ideas and deep changes the way system behaves.  Changes that are not well documented, together with the documentation being spread in various places.  Its is not difficult to understand why linux is not widely accepted by the general public.  If a person like me with many years of IT experience (not in linux) has this kind of difficulty, what about a common lay person?

---

### Post by martago on 2018-06-30
Further investigating this subject, I came to the conclusion that every new networking software that is added with new ubuntu/xubuntu releases, does not replace the previous technology, it just adds up another layer of complexity.  That is the case with the new Netplan that should replace the previous networking configurations, but whatever you define with Netplan, like your dns servers, it will append to the other previous network configuration technology, such as NetworkManager, resolvconf, etc.  The only possible conclusion is that there are no one centrally controlling what is being done with every new release of ubuntu, it is up to the several and separated teams that work in each area of the o.s., and they seem not to worry too much with the impact of introducing new software, without actually replacing the already existing and running software, probably it would be too much work to do otherwise, although in my view that would be the correct way.

---

### Post by martago on 2018-07-01
Here is the long and very exhausting solution I found out in order to ENTIRELY replace the default dns servers by the Google dns servers (applied in the latest Xubuntu 18.04):

Sudo nm-connection-editor

   -  Change method to &#8220;Automatic, addresses only&#8221;
   -  Fill in the DNS servers you want in the tabs &#8220;IPv4 Settings&#8221; and &#8220;IPv6 Settings&#8221;


sudo network-admin

   - In the DNS tab, fill in all the DNS server addresses (ipv4 and ipv6 dns servers)


sudo nano /etc/network/interface :

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

dns-nameservers 8.8.8.8 8.8.4.4
dns-nameservers 2001:4860:4860::8888 2001:4860:4860::8844


sudo nano /etc/resolv.conf :

nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 2001:4860:4860::8888
nameserver 2001:4860:4860::8844
search lan


cd /etc/resolvconf
sudo mkdir resolv.conf.d
cd resolv.conf.d
sudo cp /etc/resolv.conf head
sudo cp /etc/resolv.conf tail


Change and correct all resolv.conf files in various directories, namely:

- /etc/systemd/resolved.conf
- /lib/systemd/resolv.conf
- /run/NetworkManager/resolv.conf
- /run/systemd/resolve/resolv.conf
- /run/systemd/resolve/stub-resolv.conf

- /etc/dhcp/dhclient.conf
  ( uncomment and/or add line:  prepend domain-name-servers 8.8.8.8,8.8.4.4; )


If required, these optional procedures:

sudo rm -f /etc/resolv.conf       (delete file and symbolic links to it)

sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf


Restart the computer and check the network:

nmcli dev show | grep DNS

dig [www.cnn.com](www.cnn.com)    (check the dns server used!)

---

### Post by martago on 2018-07-01
Of course this is the opposite of how an operating system should be conceived and upgraded, it makes me remind the time of Novell Netware where a simple change of a fixed IP address had to be modified in so many configuration files, usually requiring a certified Novell technician to do it.  I just remember how devastating it was to Novel the appearance of MS Windows Server, muach easier to configure and all GUI.

Here in Xubuntu 18.04 you supposedly could do everything in a graphical way, using network-admin and nm-connection-editor, but if do so, you are not replacing the dns of your isp router but adding extra dns servers, that will remain after the dns of your isp router.

---

