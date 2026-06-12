---
title: "Need advice: Redoing networking on an old server?"
date: 2022-08-26
forum: Networking &amp; Wireless
---

### Post by bsh on 2022-08-26
Hi all,
I apologize if this is going to be long. I am also not an expert and very out of date too. And I'm quite confused trying to figure all this out.
The story is: I have a very old server, that has gone through several dist upgrades (is now at 20.04.5) and many many customization, so there's surely a lot of junk and "noone knows why this was needed back then" stuff. The network hardware and setup has changed a lot since.
I was thinking, I should "redo" the networking on the server, cleaning up the ages old junk, and do it the "proper, modern" way. But I need advice, what should I do.
Currently it is running the old style "networking" setup, using /etc/network/interfaces (and also ifup for iptables) using a static ip configuration. At one point I remember after an upgrade it installed NetworkManager as well, which caused trouble so it's been removed but there could be remains of it in some configs.
At one point systemd-networkd and resolved was disabled due to conflicting with dnsmasq and ntpd. For a period it was also the DHCP server so there are host configs and dns for that.
Now I don't need any of that anymore, as I can "offload" all of that to the new network gear, it handles vlans, dhcp, dns.

So I'm thinking of changig the server to a (statically assigned) DHCP configuration, that pushes ip, gateway, dns and search domain.

But I'm confused: should I do all of this with systemd-networkd and resolved, or netplan, or NetworkManager? I tried a fres install in a VM and it seems to be using networkmanager? I thought it was dperecated? I'm also confused by netplan and systemd, since apparently I can configure the network interfaces through both of them? Which one then?
Thanks for any help guys.

---

### Post by chili555 on 2022-08-26
Typically, recent versions of Ubuntu server use netplan. You can find your current file in /etc/netplan and example templates in /usr/share/doc/netplan/examples

If you make any changes to your /etc/netplan/xxx.yaml file, be sure to respect spacing, indentation, etc. Netplan is strict. Follow with:

```
sudo netplan generate
sudo netplan apply
```

---

### Post by TheFu on 2022-08-26
> **bsh said:**
> 
So I'm thinking of changig the server to a (statically assigned) DHCP configuration, that pushes ip, gateway, dns and search domain.
I wouldn't do any of this.  Any server should have locally assigned, static IPs. Actually, any desktop that doesn't move should too.  DHCP fails and when it does, life sucks.  Use DHCP reservations for portable devices and devices that don't provide a reasonable method to set static IPs locally.  All laptops, IP-cams, TV-tuners ... things like that should use DHCP reservations ... that are outside the dynamic DHCP range given to guest devices.  Really, guest devices need to be put onto a completely different subnet as do all wifi devices.

> **bsh said:**
> But I'm confused: should I do all of this with systemd-networkd and resolved, or netplan, or NetworkManager? I tried a fres install in a VM and it seems to be using networkmanager? I thought it was dperecated? I'm also confused by netplan and systemd, since apparently I can configure the network interfaces through both of them? Which one then?
Thanks for any help guys.

If you are running Ubuntu Server, network-manager would never have been installed.  Are you calling this a "server" even though it has a GUI?  GUIs bring all sorts of added complexities.

BTW, overall, I think you need a fresh OS install.  You'll never clean up the cruft otherwise.  Also, you should clearly document the steps specific to your setup as you do this.  After you get the system exactly as you like, wipe it again and follow those instructions to correct anything missing/wrong.  This is a normal professional IT method.  If properly documented, you'll have a script that can be run to recreate the system when done.  You'll want to edit files using sed or a devops tool like ansible, rather than using sudoedit, but that will just make the "configuration as code", which is a best practice for running servers.
Creating the /etc/resolv.conf file is pretty trivial for ansible.  A simple file-copy task.  Or if you need to make it more difficult, use a template with variables that are replaced during the copy.  Re-running ansible playbooks 1 or 1000 times shouldn't change anything.  Omnipotent is the term they use.  It is a different way of thinking.  There are ansible install/configure tasks posted and available for our use as we like. Lots of modules for almost anything we'd want in normal infrastructure is available as a starting point for our needs.  BTW, no need to pay for anything related to ansible, though the marketing makes it seem necessary. It isn't.  Ansible will change your life FOR THE BETTER.  Some other DevOPS tools are worse than the initial problem, I'm sad to say.  I've spent 4-12 hours in training from the most popular DevOPS tools and keep returning to Ansible.  Ansible was NOT the first tool I used, BTW.

In ubuntu 20.04 and later, netplan is the way to setup networking.  It sorta sucks that we have to learn a new file format that is crazy-picky when the interfaces file was fine and worked.  Systemd isn't involved in anything networking, except starting and stopping the services.  I think system-resolved is an abomination. When I've tried to use it or fix issues it cause, I've always failed and found it easier to purge from my systems.  I run a DNS (pihole w/ local DNS via dnsmasq), so there is no need to have a local caching DNS on each computer here.

When setting up each service for your LAN, you might want to create a separate container for each, to bundle each service into a nearly self-contained set of dependencies and security sandbox/container.  Somethings don't work well inside containers, but many things do.  For example, my piholes run in an lxd/lxc container.  LXD containers are not like Docker. They are closer to a very light virtual machine and can be maintained just like any other VM.  I treat VMs just like a physical machine. Same for lxd containers.  With docker, we have to learn how to update the container to have only the minimal requirements to run the 1 service the docker is about.  Plus, the port forwarding of docker seems to get lots of people into trouble.  LXD can be connected to any Linux bridge, have IPs on the same subnet as other servers, while still being extremely light and fast.  

I moved my wallabag server from a VM to an lxd container. The resources needed dropped greatly and the speed that it handles requests became instant. No waiting for swapping.  I also run an email SMTP gateway in an lxd container. Works fantastic.  I moved a pihole from 18.04 to 20.04 a few days ago.  It was crazy easy and under 2 minutes total time.  This weekend, I'll move the backup DNS/pihole to 20.04.  Plus, since lxd uses ZFS as backing storage, cloning/migrating/moving the lxd container to a different host isn't hard. It is built-in.

---

### Post by bsh on 2022-08-29
> **chili555 said:**
> Typically, recent versions of Ubuntu server use netplan. You can find your current file in /etc/netplan and example templates in /usr/share/doc/netplan/examples

If you make any changes to your /etc/netplan/xxx.yaml file, be sure to respect spacing, indentation, etc. Netplan is strict. Follow with:


netplan is installed, but not used. there's nothing in /etc/netplan. I guess it was ignored on dist upgrade because I am using static interfaces setup.
I am however using Webmin too, which (if used - I didn't use it for that yet) to configure network, it actually uses netplan yaml's.
Just by looking at neplan configs, I fail to see why is it any goot, it seems overly complicated to me, especially with that strict indenting etc.

---

### Post by bsh on 2022-08-29
> **TheFu said:**
> I wouldn't do any of this.  Any server should have locally assigned, static IPs. Actually, any desktop that doesn't move should too.  DHCP fails and when it does, life sucks.  Use DHCP reservations for portable devices and devices that don't provide a reasonable method to set static IPs locally.  All laptops, IP-cams, TV-tuners ... things like that should use DHCP reservations ... that are outside the dynamic DHCP range given to guest devices.  Really, guest devices need to be put onto a completely different subnet as do all wifi devices.

It's like that, everything is in separated vlans. That's the main reason why I want to redo things. I was thinking, if the server was also getting it's configuration via DHCP, including name server and resolution etc, then it was quite easy to say, put the whole vlan group into another, just by poking the gateway or the switch only. Not that it happens often... so probalby doesn't worht the hassle.
But I already see that the archaic netwoking/interfaces stlye setup is not going to be supported. So how long can I still ive with it? Some time in the near future I'd have to move along with the operationg system evolution, wheter I like it or not.


> **TheFu said:**
> If you are running Ubuntu Server, network-manager would never have been installed.  Are you calling this a "server" even though it has a GUI?  GUIs bring all sorts of added complexities.

yes it is a desktop install, always has been. I thought I mentioned that, didn't I?

---

### Post by TheFu on 2022-08-29
> **bsh said:**
>  yes it is a desktop install, always has been. I thought I mentioned that, didn't I?

Not in this thread that I can see.  I treat different threads like they are different universes, since people can have multiple systems, completely unrelated.

Desktop installs use network-manager, unless you do something different.  I always purge those packages because they've been unreliable and screwed things on my systems with more complex setups.  You need to decide what type of networking you'd like, since you get to live with it.  DHCP seems like the easy answer, until your network is down due to a dumb mistake.

As for managing lots of systems on the same network, use ansible for local configurations.  For years, rather than running a DNS on my LAN, I had ansible updating the /etc/hosts file on all the systems instead.  Then Android stopped honoring the /etc/hosts file and only used DNS, so access to internal webapps didn't work. Thanks Google, NOT!  The only answer was to setup a DNS.  Since my hosts files were also used for malware and ad blocking, the replacement is a pi-hole running inside an LXD container on a server here.  A pi-hole has dnsmasq, which can also be used for lite-DNS needs. More than sufficient for a small LAN.

Anyway, best to honor the type of install used when posting here, not the purpose.  If a desktop install, regardless of DE, best to call it a "desktop".  Ubuntu Server installs don't have any GUI and all those pesky end-user applications aren't installed like network-manager. Plus, other assumptions can be made for a "server" install vs a "desktop" install.

---

