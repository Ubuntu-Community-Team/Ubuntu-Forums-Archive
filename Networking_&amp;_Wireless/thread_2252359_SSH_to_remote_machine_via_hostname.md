---
title: "SSH to remote machine via hostname"
date: 2014-11-11
forum: Networking &amp; Wireless
---

### Post by errata2 on 2014-11-11
I have a machine in my office which we would like to start to use as some kind of local server. I installed Ubuntu Server on it and set up OpenSSH. Everything works fine when I try to use ```
ssh username@ip.address
``` but I wonder how can I set up this machine so that people can connect to it with ```
ssh username@machinename
```I am pretty dumb when it comes to networking, so I have no clue where to start? Should I set up some DNS thingie on that machine or editing hosts/hostname file should be enough?
I'd like to point out that there are just too many computers in our office so I'd like to sort this thing on "server-side" rather than editing ssh config or hosts file on each of them. Also, we have few different OS-es, like Ubuntu, Kali, Debian, OSX, Windows 7/8.
If any other info from my side is needed, I will be more than glad to provide it :)

Thanks for any help and tips!

---

### Post by Lars Noodén on 2014-11-11
The fancy way, if it is an external, public IP address with lots of users would be to register a domain name.  

If it is an internal address you could put an entry in /etc/hosts on each client or else add a line to your DHCP server's configuration if it is DNSmasq or something else that allows assigning names.

Though perhaps the easiest way, if it's just from one or two clients, would be to add a shortcut in ~/.ssh/config on each client's machine.  

```

Host b200
  HostName 198.51.100.26

```

The above configuration would allow you to run 'ssh foobar@b200' and it will connect to 198.51.100.26 as user 'foobar'  You can also set the User name in the configuration file.  The full list of options for your ssh client's configuration file are found in the manual page for [ssh_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html)

Edit: putting a line in /etc/hosts works for external addresses, too, but does not scale well.

---

### Post by errata2 on 2014-11-11
Thanks for reply Lars!
This machine is in our local network and has a static IP. I did edit my own ~/.ssh/config file for easier connecting to it but I'd like to avoid to set up each client that way since there is like 50+ clients in total. Is there a simple way to set up that machine to "broadcast" its hostname in some way so I can SSH to it like **ssh username@machinename** instead of using the IP? The reason for this is also because the IP might change sometimes in the future, so re-configuring all those clients will be a bit of pain-in-the-a** :)

---

### Post by Lars Noodén on 2014-11-11
If you have only a few machines, but many users per machine, then you could put your changes in /etc/ssh/ssh_config so as to make the change only once per machine.  

Otherwise, this is more a networking question and a little out of my area, but how are the clients set up for IP numbers and DNS?  Are they using DHCP?  What are you currently using for DNS?

---

### Post by errata2 on 2014-11-13
There are lots of machines around with one user per each. All clients have DHCP set up and our DNS is the one which our ISP is providing us. The only machine which has static IP is this one which should be used as a "server" and DNS on it is at the moment the same as on every client in the office.

---

