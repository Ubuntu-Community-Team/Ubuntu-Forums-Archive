---
title: "Ubuntu 18.04 LTS"
date: 2019-10-24
forum: Networking &amp; Wireless
---

### Post by heinz09 on 2019-10-24
I am in the process of setting up PHPVirtualBox on Ubuntu LTS 18.04.

everything went smooth, I installed VirtualBox and PHPVirtualBox. When it came to opening up the firewall I have hit a brick wall.

I did the following to my ufw:

ufw default deny incoming
ufw default allow outgoing
ufw allow 22/tcp
ufw allow 80/tcp
ufw allow 443/tcp

I rebooted the server and ran "ufw status"

Status: active
[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD]To[/TD]
[TD]Action[/TD]
[TD]From[/TD]
[/TR]
[TR]
[TD]22/tcp[/TD]
[TD]ALLOW[/TD]
[TD]Anywhere[/TD]
[/TR]
[TR]
[TD]80/tcp[/TD]
[TD]ALLOW[/TD]
[TD]Anywhere
[/TD]
[/TR]
[TR]
[TD]443[/TD]
[TD]ALLOW[/TD]
[TD]Anywhere[/TD]
[/TR]
[TR]
[TD]22/tcp (v6)[/TD]
[TD]ALLOW[/TD]
[TD]Anywhere (v6)[/TD]
[/TR]
[TR]
[TD]80/tcp (v6)[/TD]
[TD]ALLOW[/TD]
[TD]Anywhere (v6)[/TD]
[/TR]
[TR]
[TD]443/tcp (v6)[/TD]
[TD]ALLOW[/TD]
[TD]Anywhere (v6)[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

 When I run a NMAP scan on the server it says 80 is open, but 22 and 443 are closed. For the life of me I cannot see why those   ports are closed when they are obviously open on UFW.
 
 Any idea what might be causing this? This is for my internal test server to run PHPVirtualBox.

---

### Post by uRock on 2019-10-24
Have you installed openssh-server and have you configured the server to serve anything on 443? 

I just set my firewall to allow 443 but it did not show in my port scan, as I do not have a service configured to do anything with the port.

---

### Post by heinz09 on 2019-10-25
Thank you my OpenSSH was not installed (strange as I always install it). Still strange that my 443 does not have anything. My Apache is supposed to have my one application running on it, but I will take a look, you just fixed the biggest issue I was having.

---

### Post by uRock on 2019-10-25
I'm glad that helped. Do feel free to mark the thread solved by clicking on Thread Tools in the upper right and selecting Mark thread as solved.

---

