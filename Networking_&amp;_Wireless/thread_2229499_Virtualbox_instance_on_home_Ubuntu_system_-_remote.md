---
title: "Virtualbox instance on home Ubuntu system - remote access?"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by mark2741 on 2014-06-13
I have a Virtualbox with an Ubuntu Server 14.04 VM setup on my home Ubuntu desktop. The purpose of the VM is simply as a development server for a Drupal-based website I'm working on. It is more a testing sandbox. The majority of the time I plan to work on it in person at the desktop, so no issues. I start up the VM and leave it running all the time, and then I access the Drupal instance via the browser on the host machine. 

But, from time to time, I'd love to be able to access the Drupal website when I am out of the house, remotely.

I have Verizon FiOS for my home internet service, so bandwidth shouldn't be an issue. 

What is the best way to do that? I know it is something to do with dynamic IP/router setup. Any pointers/advice is greatly appreciated.

---

### Post by TheFu on 2014-06-13
* setup bridge mode for the VM, not NAT.
* inside the VM, set a static IP.
* inside the VM, install both openssh-server and fail2ban.
* On your router, open port 61022 and forward it to port 22 on the VM static IP.
* On all the client machines that will be remote, install ssh-clients, create ssh keys - **ssh-keygen** and push those keys to the VM using **ssh-copy-id**
* Now, setup the VM ssh connection for higher security - prevent root logins, prevent password-based logins
* Most people at home do not have static public IPs, so a dynamic DNS service is needed. Your router probably supports a few automatically - if you pick one of those, life will be easier.  For many, many, years, DynDNS was free for subdomains - which worked.  I'd check through the list in your router for a free offering and use that. Of course, you can pay DynDNS.org something (sorry - I'm grandfathered) annually for their
* fail2ban will automatically firewall attempts to connect to your server if they fail. This is necessary these days, even when running on a non-standard port, like we've setup above.

Ok - now you have ssh working.  With this, you can securely access the VM from anywhere in the work.  You can setup a secure tunnel from anywhere in the work too.

I didn't say how to get to the web server - you should know that already.  And you should know that putting a website on the internet, especially one that is under development, is a very dangerous thing.  When it gets hacked, your entire internal network is open to the world.

So - good luck and have a good time!

---

