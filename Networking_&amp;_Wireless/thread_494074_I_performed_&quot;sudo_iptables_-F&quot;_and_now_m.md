---
title: "I performed &quot;sudo iptables -F&quot; and now my intenet does not works, what should i do?"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by legolas_w on 2007-07-06
Hi
Thank you for reading my post
I performed "sudo iptables -F" in order to disable the firewall and make my torrent applications work.
But after i did that, I can not connect to internet using browser, torrent, mail client....

Can some one post content of his/her iptable configuration files that i can use to make my internet works?

It would be far more than good if you could add some rules that allows connection from any source to any destination and vice-versa.
This way i can ensure that my torrent and mule works fine.

---

### Post by t4thfavor on 2007-07-06
Did you try to reboot, and see if it comes back? 

I know you can download firestarter and usee it to set up iptables. But that doesn't help much when you don't have internet access to the machine.


I have no iptables rules in my config either, and I get online just fine. Though I am using a hardware firewall.

---

### Post by legolas_w on 2007-07-06
Any other comment?

thanks

---

### Post by iqag1060 on 2007-07-06
In a default Ubuntu installation, IPTables is unconfigured. That is to say it doesn't block anything, in or out. Even if you had added some rules, you have now flushed them, as ```
sudo iptables -L
``` should confirm. (If it doesn't - i.e. if there are rules - check /etc/network/interfaces to see if it's loading  a set of rules on up, if so just comment it out, flush the iptables and shutdown then restart your interface.)
[Here's a tutorial]("http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html") on configuring iptables for use with bit torrent. You may want to change your port numbers, obviously.
Right now, see if you can ping out, if your interface is up (ifconfig), and that traffic is actually going through the rest of your network. Your problem is probably not iptables.

---

