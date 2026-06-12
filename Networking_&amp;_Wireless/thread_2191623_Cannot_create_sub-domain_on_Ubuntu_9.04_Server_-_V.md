---
title: "Cannot create sub-domain on Ubuntu 9.04 Server - VHOST problem?"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by aekschwartzberg on 2013-12-03
Hey folks! First posting here in Ubuntu forums - thanks in advance for your paitience. I'm a novice / intermediate Ubuntu user who's having trouble setting up a subdomain with a virtual host file. 

At work we're running several websites from Ubuntu 9.04 Server in the office. All the websites work but I'm having trouble adding another subdomain. I've removed two of the previously working subdomains - figuring perhaps there weren't enough open ports or IP addresses and maybe that was causing a problem -  but I've still been unable to find a solution to make the index.html or index.php appear in browser at sub.example.com.

All my known particulars are below:

/////////////////////////

VHost File for NEW sub-domain: [http://pastebin.com/AhsL4kYG](http://pastebin.com/AhsL4kYG)

Apache2 Details
Server version: Apache/2.2.11 (Ubuntu)
Server built:   Mar  9 2010 22:04:38

Running Ubuntu 9.04 Server Edition

/////////////////////////

**What I've tried thus far..**

I've made sure that the directories "/var/log/ispconfig/sub.example.com" and "/var/www/sub.example.com/web" and I have no problems starting, stopping, restarting or reloading Apache2.

I've tried "a2ensite sub.example.com.vhost" followed by "/etc/init.d/apache2 restart" with no errors, but also no results. Also tried "a2dissite" followed by the previous to no avail.

/////////////////////////

**What I believe to be true...**

I believe that my resolv.conf is in working order as all the other sub-domains function perfectly well.

My access.log file shows no attempt on my end to access the site - so there is definitely something wrong there.

In the "/var/www" all the folders of the sites that function are colored in Teal, however my sub.example.com site is colored in dark blue like a regular directory. Perhaps that can shed some light on the problem?

[COLOR=#000000]/////////////////////////
[/COLOR]
Anything that I'm missing here? I do need the site to run PHP, which I believe my VHost file states despite the fact that it evidently does nothing :neutral:


Looking forward to your responses - thanks again in advance for all the help!

---

