---
title: "Internet Connection via Automatic Proxy Configuration URL"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by EnderTheThird on 2006-12-19
I wanted to try Ubuntu 6.10 on a computer at work, but had trouble because of the way we obtain a connection here.  We use a proxy configuration URL like this:

[http://mywork.com/array.dll?Get.Routing.Script](http://mywork.com/array.dll?Get.Routing.Script)

I can get Firefox to work once I boot off the Desktop CD, but I can't get any other Internet-dependent applications to work (apt-get and Synaptic).  Is there any way to globally set the computer to use that URL/script when trying to access the Internet?  Any help would be appreciated.  I was hoping to show a few co-workers Beryl, and lugging my desktop here is WAY too much work.  :-)  Thanks!

---

### Post by EnderTheThird on 2006-12-21
](*,)   Bump!

Any help here?  I've tried following mini howto's on how to modify the bashrc file (The name was something like that) but none of them have worked.  And I can't get Beryl to install with all dependencies met without having apt-get and synaptic working.  :-/

---

### Post by mooha on 2006-12-22
](*,) 

if you find anything to make apt-get or synaptic work through proxy please let me know, I tried every possibility no chance, I am running my ubuntu dapper at work and our proxy require user and password. ](*,) 


Many thanks

---

### Post by fxeditor on 2007-03-15
I too am having problems getting anything other than FIrefox to work via the Internet  at work.   We have an automatic proxy  configuration script   but putting the URL into the "Network Proxy Preferences" doesn't do anything.  If I connect at home through straight DHCP everything is fine.  I am running 6.10   Any help would be greatly appreciated.

Hopefully this post made sense.

Thanks in advance,

Michael

---

### Post by tagra123 on 2007-03-15
Have you tried manually setting the dns addresses?

I'm not sure if it will work but since you seem to have som connectivity it might.

System-Administration-Networking

Click on DNS

Add these (and visit opendns.com)
208.67.222.222
208.67.220.220

Write down the address that were already there and then remove them.

By the way open dns will work great on your home connection to. It gets rid of those "looking up ..." messages in firefox. Mad by browsing seem much faster too.

You might also see this post.

[http://www.linuxquestions.org/questions/showthread.php?p=358050#post358050](http://www.linuxquestions.org/questions/showthread.php?p=358050#post358050)

---

### Post by Mr. C. on 2007-03-15
Proxies can be setup in many ways, for various services.  Without knowing anything about your corporate environment, we can't know how you should connect.

You should contact your IT department and inquire about which services require proxies.

It is very highly doubtful that you can simply choose your own IP information and expect your system to bypass their firewalls and proxies.

MrC

---

### Post by tagra123 on 2007-03-15
> **Mr. C. said:**
> Proxies can be setup in many ways, for various services.  Without knowing anything about your corporate environment, we can't know how you should connect.

You should contact your IT department and inquire about which services require proxies.

It is very highly doubtful that you can simply choose your own IP information and expect your system to bypass their firewalls and proxies.

MrC

What about tunneling?

---

### Post by Mr. C. on 2007-03-15
A proxy is a go-between.  The proxy establishes the policies.  You can only do what the proxy allows or provides.  If a router is configured to force, say port 80 traffic through a proxy, you cannot defeat that directly.   If the policy allows, or there is no proxy for a given service such as SSH, then you can tunnel.

Many corporations are very restrictive about the type of outbound connections they allow.   Browsing, for example, may go through a proxy to a) cache content to save bandwidth, and b) to control what users do.

MrC

---

### Post by tagra123 on 2007-03-16
I know what a proxy is but I'm positive Ive read where folks have used ssh tunnels to avoid the firewalls etc..   That's why I brought it up.  Interesting stuff.  

Correct me if I'm wrong but couldn't ssh be told to use another port. Surely more than port 80 is open.  If port 22 is blocked why not use 1022 or 2222 etc.

From what I understand is my home pc is set to ssh on for 40001 and if the company port also has that port open I can get the connection and tunnel even in windows using putty and have unfettered access.

[http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall](http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall)

and

This page has a several descriptions of how to get past the proxy.

[http://polishlinux.org/apps/ssh-tunneling-to-bypass-corporate-firewalls/](http://polishlinux.org/apps/ssh-tunneling-to-bypass-corporate-firewalls/)

starting at this section

Battle continues with a corkscrew

---

### Post by Mr. C. on 2007-03-16
We're in complete agreement.

I have no idea what your company allows.

Your premise that you can just get around the firewall by using random high-numbered ports is incorrect.   If the firewall is set by default to block ALL outbound traffic, you can search until your last days.

Best of luck,
MrC

---

