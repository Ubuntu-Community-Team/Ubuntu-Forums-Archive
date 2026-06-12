---
title: "BIND for home local network"
date: 2015-02-22
forum: Networking &amp; Wireless
---

### Post by denis35 on 2015-02-22
Hello,
I want to setup a local DNS ubuntu 14.04.01 ESX 5.5 VM as my local DNS server.
I have a bunch of VM's running and a couple of physical servers.  I also have a domain name I use for a website that uses dynamic dns with ddclient to google domains where my domain is hosted.
My home router is currently my dhcp server and provides dns.  I want to convert my VM's and physical servers to static IP addresses in my local network. 

I've read a lot of tutorials on setting up BIND but not clear on what the considerations are when using a wireless router and dynamic dns (dynamic dns updates using ddclient on another ubuntu VM).
I would like to keep my wireless router (netgear R7000) for all my wireless devices.  

Do I disable DHCP on my wireless router and let my soon to be setup ubuntu become my DHCP and local DNS server?
Any special considerations using dynamic dns? Should I use my public domain name as the domain name for my local network also? I would like to if possible but not necessary.

Is there a write-up anywhere that goes through a setup similar to mine?

Appreciate any help.

---

### Post by TheFu on 2015-02-22
All of these tools are extremely flexible. You can do whatever you like. It really comes down to what you want and what YOU think is a good idea for your needs.  

I would NOT use the same domain internally - make it harder to troubleshoot LAN vs WAN access issues that way. I wouldn't run my own public domain DNS - last time I was hacked, it was through an out-of-date BIND. I was behind a few months on patches. BIND is one of the hardest things to run securely, so as you learn about the correct, secure, architecture to use, definitely only keep it internally. Pay a pro to run DNS for you on the internet - if you like, you can have your BIND be the master and replicate to the external service. This is part of the BIND best practices.  

You can have DHCP run anywhere you like. It is easier to have the router handle both static IP reservations AND DNS, IMHO.

I don't run BIND internally anymore. It isn't worth the hassle to me or the security concerns.

---

### Post by denis35 on 2015-02-22
Thanks for the reply and I appreciate your input.  How would you recommend I manage name resolution for all the hosts I have running? My challenge is with VMware I have many more machines than ever before so I figured local DNS would make it much easier than remembering all the IP addresses.  I guess I can always manage host files but that seemed a bit cumbersome.  Is there a scenario where I can just spin up a VM to run local DNS for local name resolution only?  I'm fine leaving DHCP and reserved addresses to my wireless router. Would a Caching Nameserver do the trick? thanks!

---

### Post by TheFu on 2015-02-23
> **denis35 said:**
> Thanks for the reply and I appreciate your input.  How would you recommend I manage name resolution for all the hosts I have running? My challenge is with VMware I have many more machines than ever before so I figured local DNS would make it much easier than remembering all the IP addresses.  I guess I can always manage host files but that seemed a bit cumbersome.  Is there a scenario where I can just spin up a VM to run local DNS for local name resolution only?  I'm fine leaving DHCP and reserved addresses to my wireless router. Would a Caching Nameserver do the trick? thanks!

Here's how I do it for about 30 hosts here:
* DHCP managed by a pfSense box
* Static IP reservations for DHCP-based IPs managed by a pfSense box
* Static IPs for all non-portable systems/VMs managed by /etc/hosts centrally managed thru ansible
* External caching nameserver in the router
* external DNS management for different public domains by dyndns and no-ip (depends on who owns the domain)

The router or the pfSense box could do everything and that might happen in the future. [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) I'm uncomfortable having network security, single-purpose devices running inside a VM. I've been doing virtualization on many, many different platforms since the late 1990s. By default, we use VMs here for everything ... but using it for network security stuff is just wrong for a number of reasons. Perhaps in 10 more years, after that technique is well proven, I'll allow it. We are cautious.

BIND is ugly and has a long history of being hacked. It is also extremely flexible and capable. If you intend to learn BIND for corporate use with thousands of hosts, definitely run it at home and carefully learn the best practices from a strong mentor with decades of BNID experience.  For, I never intend to run BIND again since I can pay an expert to handle these things for me for $20-40/yr. 

Ansible is a devops tool and if you are running more than 3-5 systems/VMs, then you need to switch to management with a tool like that. I use a template for /etc/hosts which gets customized for each host as it gets pushed to each machine.  Ansible works like most web frameworks - based on the base CWD.
```
$ more tasks/common_etc_hosts.yml
---
- name: Copy /etc/hosts
  template: src=templates/etc_hosts.j2 dest=/etc/hosts backup=yes 
            owner=root group=root mode=0644
```

```
$ more templates/etc_hosts.j2 
# {{ ansible_managed }}

127.0.0.1 localhost
127.0.1.1 {{ ansible_hostname }}
172.20.2.1 g_rt1

172.22.22.1 rt1 
172.22.22.2 qbe 
172.22.22.3 regulus 
172.22.22.4 romulus 
172.22.22.5 tivo 
172.22.22.6 hadar 
# continues for 12K lines http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file
```

Then the ansible playbook to run this task that modifies the template for each machine as necessary:
```
$ more plybk-push-etc_hosts.yml
---
- name: Push new /etc/hosts file
  user: thefu
  hosts: cur
  sudo: True
  vars:
    DEBIAN_FRONTEND: noninteractive

# #####################################################################
  tasks:
  - include: tasks/common_etc_hosts.yml 
```

Ansible uses ssh and sudo. This is a simple, but powerful example. Actually, I think I'll put this simple example on my blog. There are many better introductions to Ansible links are in [here]("http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server").

**Opinion** Please ignore:
And lastly ... dump VMware. Use KVM. Completely my preference for F/LOSS over commercial software from a vendor who has screwed their customers previously. KVM almost always runs faster than ESX/ESXi - according to the SPECvirt numbers. VMware changed their license model to increase costs 2x here. Within 6 months, we had removed all VMware products. We didn't have any choice. Of course, VMware lessened the screws 4 months later after the **outrage from their customer** base those license changes caused. That taught us we were at the complete whim of 1 SVP inside VMware who wanted to make more money without doing anything different or better - just by changing license terms.  If I were running 500 physical servers, all with Windows inside the VMs, then VMware could make sense. I'd look at Microsoft's VM solution first just to avoid VMware.  For linux production VMs ... KVM wins hands down.  For linux dev/test VMs - LXC containers on a trusted network, never for production and never internet facing.
When a company needlessly screws their clients, we need to remember. That's what my intent is here.
**End Opinion**

Anyway - hope this helps you decide.  It is your network, only you can decide what is best.

---

