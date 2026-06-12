---
title: "website redirects"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by 007casper on 2010-09-23
I am trying to figure out why the site isnt provisioning properly.  


I have set an IP to be on a certain subdomain.  Everything worked fine. 

i.e. 1.2.3.45 subdomain.site.com

Then, I need to move the subdomain.site.com to another server with a different IP.  So, now the subdomain.site.com had to have an IP that is 7.8.9.47.  And the old IP 1.2.3.45 had to point to another-subdomain.site.com

I reset the dns server
1.2.3.45 another-subdomain.site.com
7.8.9.47 subdomain.site.com

subdomain.site.com is working fine.  However, when you go to another-subdomain.site.com it goes to subdomain.site.com

???

I cant figure out why this is happening?  7.8.9.47 doesnt have htaccess.  

It seems 1.2.3.45 has the right virtual host set up.  I have checked the virtualhost and restart apache and reload it afterwards.  Same problem.

I have checked the dns if 1.2.3.45 is pointing to right domain with A record.  It looks fine 

Please, advise. Thank you.

---

### Post by PriceChild on 2010-09-23
Could you tell me which tool you are using & finding these problems in?

---

### Post by 007casper on 2010-09-23
I am not using any specific tool.  When I type 'another-subdomain.site.com' it goes to 'subdomain.site.com'

I put the IP address on the browser for 'another-subdomain.site.com' and it redirects to subdomain.site.com

I used [http://www.whatsmydns.net/](http://www.whatsmydns.net/) to see if dns picks up, and it seems fine.  However, I dont know why it redirects.

---

### Post by 007casper on 2010-09-24
I used live http headers.  It shows it is 302.  So, it is redirecting. 

Is there a way to find out where it is redirecting from?

It is either apache config, or htaccess.  Apache config should be fine, so thats out, and there are several htaccess files on the script.  So, I am wondering if there is a way to find out what file is redirecting.

---

