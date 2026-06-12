---
title: "Getting DNS or DHCP Table information"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2008-11-30
I'm not quite sure how to do this, so I'm just going to say what I want to do.

I currently have three machines in my home network.  One is for the server and I have it set up with a static IP address in my Linksys Wireless router.  The other two get their IP addresses using the DHCP server that comes with the Linksys router.

I've just installed Amanda to do backups to S3 from the server and it's working great.

What I would like to do is to add on my two laptops and have them backup to the server and then to S3.  I would like to use the computer names to run the backups instead of the local IP address (like 192.168.1.102).  Is that possible?  How would I do it?

---

### Post by bab1 on 2008-11-30
If you are going to call the machine by its hostname the easiest way is to a consistent (the same) IP address.  This can be static (manually configured) or permanent (reserved DHCP lease).  With the IP address always the same you now can map the name to the IP several ways.  The simplest would be the /etc/hosts file on the host where Amanda is being run.  Or you could run [**DNSmasq**]("http://www.thekelleys.org.uk/dnsmasq/doc.html") for lightweight DNS server.  You could also use BIND9 or similar with all the DNS bells and whistles.

Some final thoughts -- Does the Linksys have the ability to reserve DHCP addresses (and maybe provide the hostname)?  Do you know how to configure your laptops to provide the hostname when requesting an IpPaddress via DHCP?

---

