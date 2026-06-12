---
title: "How to Setup Local DNS Using /etc/hosts - NOT WORKING"
date: 2021-11-28
forum: Networking &amp; Wireless
---

### Post by dev-sad-ops-9 on 2021-11-28
[FONT=&amp]So I have Jenkins installed on my local machine, and I access it via [FONT=inherit]IP_Host_Address:8080[/FONT], (going with localhost:8080 is not working). When I use the service, I want to login via [FONT=inherit]jenkins.home:8080[/FONT]. How can I make this work?[/FONT]
[FONT=&amp]I tried editing the [FONT=inherit]/etc/hosts[/FONT] file like:[/FONT]
[FONT=&amp][FONT=inherit]IP_Host_Address jenkins.home[/FONT][/FONT]
[FONT=&amp]When I ping [FONT=inherit]jenkins.home[/FONT] I get the right output but when I type in my browser [FONT=inherit]jenkins.home:8080[/FONT] I can't access the login page.[/FONT]
[FONT=&amp]What's the best way to achieve this?[/FONT]

---

### Post by TheFu on 2021-11-28
Is the browser running on the same machine?

Does /etc/nsswitch.conf have hosts before other choices?

Which IP is being used in the /etc/hosts?  I'd use 127.0.0.1 or any in the 127.x.x.x/8.  All of them are the localhost.

Editing /etc/hosts doesn't magically create a DNS. That file is just for local use unless you've done something extremely non-standard.

---

### Post by SeijiSensei on 2021-11-29
> **dev-sad-ops-9 said:**
> [FONT=&amp]When I ping jenkins.home I get the right output but when I type in my browser jenkins.home:8080[/FONT] I can't access the login page.
I have no idea with jenkins is, but it looks like it's using a web server of some sort. You may need to modify its configuration to accept requests for "jenkins.home" and treat them the same as requests to the IP address.

---

### Post by slickymaster on 2021-11-29
Thread moved to **Networking & Wireless** for a better fit

---

### Post by TheFu on 2021-11-29
Jenkins is part of a CI/CD setup.  

Perhaps it is the browser causing the problem.  Many ignore the /etc/hosts and some even ignore the system-wide DNS settings.

For example, a few years ago, Chrome browser on Android ignored my LAN DNS, choosing to use Google's DNS exclusively.  On desktops, I think it ignores the /etc/hosts even today.  I was forced to setup a DNS to get around this problem. I use a pi-hole. [Https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454](Https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454)

About 2 yrs ago, Firefox did something different to solve the corrupted hosts/DNS problem. At least with firefox we can disable their "protect users from themselves" defaults.  I don't recall the exact setting in firefox, but I do remember it asked if I wanted to use their protection doing an install/first run.  Also, if the webapp is on a non-standard port, I've had to specifically tell firefox to allow that connection - my IRC bouncer listens on 6697, which is common for it, but firefox decided that was dangerous and blocked it. Think this required going into about:config to fix.

---

