---
title: "How to open and close a specific Port using the Terminal?"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by spid3y on 2010-07-02
Hi, 

I'm hooked to Ubuntu 10.04 Lucid Lynx, use Transmission a lot for file sharing and downloading torrents. Few questions,

1) How do I open a specific port? How do I close it after use?

2) Will manually opening a port increase my download and upload speed? Is it safe?

I dont have a router and my modem doesn't support port forwarding. 
[http://www.transmissionbt.com/help/gtk/1.9x/html/portforward.html](http://www.transmissionbt.com/help/gtk/1.9x/html/portforward.html)
So the last option takes me here 
[http://www.transmissionbt.com/help/gtk/1.9x/html/pffirewall.html](http://www.transmissionbt.com/help/gtk/1.9x/html/pffirewall.html) (tells me something about Linux Firewall config using terminal.)

Step-by-Step instructions for opening and closing a port on the firewall will be very much appreciated. 

Thanks and Regards,

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

Whoa...I did a 'zcat /vmlinuz > /dev/audio' and I think I heard God... :)
-- mikecd on #Linux

---

### Post by mcduck on 2010-07-02
How to configure a firewall depends on what firewall you are using.

Unless you have actually configured a firewall in some way none of the ports will be closed, so there's nothing for you to open...

The default install of Ubuntu has no running services that would listen for incoming connections from the network, so there's no need to close any ports with a firewall. So the default install has all the tools required to create a firewall, and some command line tools (like UFW) for easy firewall configuration, but there is no running firewall unless you enable one yourself.

---

