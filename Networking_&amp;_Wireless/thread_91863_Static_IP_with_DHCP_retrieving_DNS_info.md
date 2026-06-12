---
title: "Static IP with DHCP retrieving DNS info"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by avc on 2005-11-18
How do I maintain a static IP while still querying my router for the correct DNS servers? I want this to happen automatically in every boot. My idea was to start out with DHCP and script ifconfig to set the IP static, but I'm sure there's a better way, possibly using /etc/interfaces.

---

### Post by Lambert on 2005-11-18
Not sure what kind of router you have or it's capabilities but my set up is like this.

My card is set up with dhcp settings but is always assigned the same ip address.

d-link di624 router. I've set it so when it recognizes a specific mac address it assigns it a specific ip, sort of like a static situation but it's still broadcasting dhcp.

---

### Post by avc on 2005-11-18
I've got a cheap Belkin wireless router. I don't think I can configure the DHCP much there. Is there something in the DHCP protocol that allows just getting DNS rather than IP? Maybe a dhclient option?

---

### Post by Lambert on 2005-11-18
You may want to search more on this or read the man page ( man dhclient.conf)

sudo gedit /etc/dhcp3/dhclient.conf

Look for this section

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

deactivate your interface first.
I believe you can set your ip to be fixed here. remove # change to the address you want, not sure about the option part, you may be able to remove this., just remember the syntax so you can addit back in or just set the subnet mask correctly. If you don't know it look at ifconfig when connection is active.

save, activate the interface and see if that gives you what you want.

If this is the wrong section you may want to search and read more as I believe this is where you can do what you want.

---

### Post by Abhi Kalyan on 2007-03-15
Check this link out, 
A part of it answers your questions.
[http://ubuntuforums.org/showthread.php?t=267974&highlight=DNS](http://ubuntuforums.org/showthread.php?t=267974&highlight=DNS)

Here we set fixed IP in the dhcpd.conf

Thank you

---

