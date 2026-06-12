---
title: "Please help newbie w/ wireless"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by doctrdev on 2007-03-20
Please forgive my repost, but I'm not getting many responses in the newbie forum..

Hi all,

I just installed ubuntu edgy on my pc... I'm very happy with how it runs.. although I don't understand how to do the 'coding' yet... I am not a programmer.. but I have a desire to learn =)

It's taken me a while to get my linksys WMG54G wireless card working... I found a utility (dniswrapper) that allowed me to get it running...I'm assuming that it is running since 'wireless assistant' is now finding all the available wireless networks in my apartment complex - so now the card is working properly??

The only problem is that it won't hook up to my router... automatic DHCP is set... and I entered my WEP key... but it won't connect! Any idea why it won't hook up? When I launch wireless assistant it says I don't have adequate privileges and do I want to launch using 'sudo'... I have no idea what this means....I am logged in as an administrator..

Is the issue with my pci wireless card install or just my inability to configure it? I'm assuming that the wireless card is now running.. or perhaps I am missing something?

I'm usually pretty tech-savvy but this is a challenge!

I also get this error message when I try to configure wireless assistant manually:

File '/etc/resolv.conf' could not be opened for writing.
Nameserver(s) and/or domain are not set.

I have such a hard time with the coding... I need a book ;-)

---

### Post by eljalill on 2007-03-20
If you can't use the networking GUI because of permissions, you can also configure you Wnetwork with (sudo) iwconfig. 
Even if you are a computer administrator (if your user is in the admin group), as long as you are not logged in as root, you don't have full access. Usually it asks you for a password, when you try to start administrative things from the system panel, I don't know why it doesn't do that in your case.
type man iwconfig for a manual of that command, "q" lets you leave the manual and return to the shell.

Does that help?

---

### Post by rich.bradshaw on 2007-03-20
sudo lets you run things as a root user, so try

sudo iwconfig

it will prompt you for your password. You aren't running as an administrator unless you have changed things to let you do that - in Ubuntu (Linux in general) you never run as root, so to do administrative things, such as changing system settings you have to use sudo to run things.

If you are able to see your networks then you are more than halfway there!

---

