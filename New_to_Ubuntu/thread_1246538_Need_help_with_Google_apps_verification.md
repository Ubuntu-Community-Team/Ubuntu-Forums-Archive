---
title: "Need help with Google apps verification"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by amc.ath.cx on 2009-08-21
I want to use Google apps on my site. I use dyndns for my site but my isp blocks port 80.
So I want to have a site at amc.ath.cx:8080. 
To use google apps I need to verify that I own the site by uploading a verification file name googlehostedservice.html with googlea82da852441e636 in it. 
But google will look at amc.ath.cx/googlehostedservice.html and not amc.ath.cx:8080/googlehostedservice.html

I can only think of one solution. If someone here with a dedicated ip hosted the file, I cound point amc.ath.cx at their server then google would think it was me.
After googled verified it. I will point it back to my ip. And the person the helped me could delete the file. You only verify once.

Anyone here with a websever or an isp that dosn't block port 80 willing to help?

Sorry for not joining before. Normally I just read threads with solutions to my problems. This is the first problem I need to post about.
[I]
Problem resolved you may close this.[/I]

---

### Post by SoftwareExplorer on 2009-08-22
I have apache running and port 80 open, but with a dynamic address that is updated to a domain name. I think that it is possible to have one domain name point to another, so if you think it would help you I would be willing. My domain name is softwareexplorer.with-linux.com and the file is in place and should be ready in case you get it to work. I think it is called a cname alias when one domain points to another if that helps.

---

### Post by SoftwareExplorer on 2009-08-22
Welcome to the ubuntu forums. (Well kind of, now you get to be part of all the action :))

---

### Post by amc.ath.cx on 2009-08-22
Thank you but I got it working! I used Dnydns port 8080 redirection. I made a new host name at amcm.ath.cx:8080 pointed it at my computer and had amc.ath.cx redirect to it.

I'm surprised Google follows redirects but I think its a 301 redirect not a meta refresh.
Using Google apps is great. I can use up to 50 @amc.ath.cx email accounts with 7 gb of space and use it like gmail. dyndns has mx redirection so I set the mx to the google server. 
I just log in at mail.google.com/a/amc.ath.cx and use the webmail. 
I'll probly set up pop/smpt so I can use Evolution.

I like having an email with its own domain. Some websites won't let you sign-up with free online email. Plus I can have any name I want. :)

I recomend Dyndns. It's free, It's built in with my router for instant ip updates, good coice of subdomains availible, free mail redirection, free ad-free port 8080 redirect, and easy to use with google apps for personal email at your subdomain.
[I]
Problem resolved you may close this.[/I]

---

### Post by SoftwareExplorer on 2009-08-22
So does it cost to set something like that up, or it is free?

---

