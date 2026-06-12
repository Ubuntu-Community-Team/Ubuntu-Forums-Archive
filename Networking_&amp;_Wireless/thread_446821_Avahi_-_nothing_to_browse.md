---
title: "Avahi - nothing to browse?"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by Ububurns on 2007-05-17
I used to be able to use avahi to listen to shared iTunes, and to list other shared network resources.

However, now in Feisty, all I get are the things I publish myself!  For some reason I am unable to list almost anything, even using

 $ avahi-browse --all

Is avahi only looking on my computer?  How might  I go about fixing this?

---

### Post by red_five on 2007-06-05
I second this question. I have a desktop and a laptop running Feisty, and avahi is up and running on both. I can only see whatever services are shared from the local system, on both computers. Neither one will discover anything that is not running on itself. I have no software firewalls running anywhere.

On second thought, my desktop may not be exactly right, as it seems that a couple of services are not even detected locally. What config files can I look at? And do all systems need the dnsconfd service running, or should there only be one system running it?

---

### Post by huygens on 2007-06-15
I have just started playing with Avahi a few minutes ago. At least I can tell you that it ought to be working on Ubuntu 7.04, as it is here.
I can share my music on Rhythmbox on my laptop and see it on my desktop, both now configured to use Avahi.

I have tried your command, avai-browse --all, it is also working.

So, do you have a firewall configured?
Try: sudo iptables -L

If you get something different than below, you have a firewall:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```To remove the firewall: sudo iptables -F

Then, take care that Avahi daemon is up and running. If you do: ps waux | grep avahi
Do you have one or more line listing avahi-daemon?
If it is not running, verify that the file /etc/default/avahi-daemon as the variable AVAHI_DAEMON_START set to 1 and not 0. If it is not the case, edit the file and change it: sudo nano /etc/default/avahi-daemon
(replace nano by your favourite editor)
Then restart the avahi daemon:
sudo /etc/init.d/avahi-daemon restart

Check if it is now working.
Instead of using the command line, there is a nice applet for Gnome to see what service are available: service-discovery-applet

---

