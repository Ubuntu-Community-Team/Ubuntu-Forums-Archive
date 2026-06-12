---
title: "installing third party application"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by andjer on 2009-08-15
Real beginner here - i've been using Windows for years but have decided to dip my toe into the ubuntu water.

At work we are setting up a social network based on the elgg platform. I want to play around with this set up at home and so have used VirtualBox to set up a virtual server , onto which I've installed ubuntu server 9.0.4. I included the LAMP set-up as this suits the elgg Apache/MySQL,PHP requirements.

I've logged in on my virtual server and am at the command prompt, but have no idea what I need to do next. basic questions are:
1. is there a gui i can install which will make the next steps easier?
2. i have the elgg install on a usb key - how do i get it installed on to the virtual server?

---

### Post by fraser_m on 2009-08-15
If you wanted a GUI, you probably should've installed the Desktop version, but if you want a GUI, and already have a network connection, run:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by andjer on 2009-08-15
Thanks.

The reason I installed the server version was to replicate what we'll be doing at work. Can I install the desktop version and still add the LAMP environment to get the same overall functionality?

Sorry if this is real simple stuff - this is day one for me!

---

### Post by theozzlives on 2009-08-15
> **andjer said:**
> Thanks.

The reason I installed the server version was to replicate what we'll be doing at work. Can I install the desktop version and still add the LAMP environment to get the same overall functionality?

Sorry if this is real simple stuff - this is day one for me!

Yes, I'm running a LAMP on Ubuntu Desktop. Instead of "dipping a toe" why don't you jump in with both feet (the water feels cold when you go in slowly)? Did you "dip a toe" in Windows? Here's a free .PDF that'll help [http://www.ubuntupocketguide.com/index_main.html]("http://www.ubuntupocketguide.com/index_main.html")

---

### Post by progone on 2010-05-14
> **andjer said:**
> Real beginner here - i've been using Windows for years but have decided to dip my toe into the ubuntu water.

At work we are setting up a social network based on the elgg platform. I want to play around with this set up at home and so have used VirtualBox to set up a virtual server , onto which I've installed ubuntu server 9.0.4. I included the LAMP set-up as this suits the elgg Apache/MySQL,PHP requirements.

I've logged in on my virtual server and am at the command prompt, but have no idea what I need to do next. basic questions are:
1. is there a gui i can install which will make the next steps easier?
2. i have the elgg install on a usb key - how do i get it installed on to the virtual server?


How is Ubuntu and ELGG working out for you?

What I love about Ubuntu you can bring it back from the dead?  Windows is another story. 

I'm curious if you ever got ELGG working.

---

