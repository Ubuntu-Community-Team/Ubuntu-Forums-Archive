---
title: "Property Managment Software"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by k33bz on 2010-09-16
I have been looking and only to find online sources, or things to upload to a server, which I am not ready to work off a server at this moment.

I buy real estate (Residential) fix them up and sale them some I turn around and rent out. So I need software that will keep track of expenses (all expenses) that I put into these properties. Also need a way to track properties that I rent out.

---

### Post by k33bz on 2010-09-16
Bump

---

### Post by jtarin on 2010-09-16
Are you looking for a Quickbooks equivalent? Might look at [GnuCash.]("http://www.gnucash.org/")

---

### Post by k33bz on 2010-09-17
Sorry no, I am not looking for a Quickbooks equivalent, for finances I am using Grisbi.

What I need is a way to keep track of not only expenses, but info on property, photos of property, schedule maintenance and inspections, tenant information, list of contacts. 

I know I could use several programs to achieve this, such as using Grisbi for finance tracking, Contacts for obviously contacts, Dates for appointments, any number of databases for keeping other info, and Project Management for keeping track of hours worked on properties. But I rather use one single program that can do all of this.

Does anyone have any ideas?

---

### Post by v1ad on 2010-09-17
sounds like helluva program, ill look around.

---

### Post by mastablasta on 2010-09-17
basically you need an offline database programme?! Why not hire someone to make it for you?
 
another way would be to use one of the web portal programms (Drupal, Joomla?!) and the use some plugins or extensions with it.

---

### Post by jtarin on 2010-09-17
[Browse and search here]("http://freshmeat.net/tags/database"). I always find something I can use.

---

### Post by JKyleOKC on 2010-09-17
Here's a couple from freshmeat:

[http://freshmeat.net/tags/property-management-system](http://freshmeat.net/tags/property-management-system)

I've not examined either of them in more detail, though.

---

### Post by k33bz on 2010-09-17
Thank you V1ad for looking around a bit. 

Mastablasta, To be honest I am just not in the mood to hire someone to program it, although, I might be left with no choice. But we shall see. Your other option however is out of the question, it is not my preference to be able to use it from a server (at least not at this time) and especially not from a web server.

jtarin, I will be checking out that link here soon. Thanks

JKyleOKC, thank you for this link, Wakodi looks promising, well at least with some stuff, took a minute to find a Download of it, but I got it, and will be checking it out soon.

---

### Post by Jazzy_Jeff on 2010-09-17
You can set up a webserver on your own computer to use though. Would not be hard.

---

### Post by k33bz on 2010-09-17
> **Jazzy_Jeff said:**
> You can set up a webserver on your own computer to use though. Would not be hard.

I agree it is not hard at all, I have had my own web server. But it is not what I am after, I have a specific program in mind for when I do decide to use a web server.

On a downside, Wakodi is for a web server. So I guess I have no choice but to use how I have it set up now, using several different programs till I am ready for the web server.

BTW-- the web server program I will be using (besides the basic LAMP) is here [http://propertymanagement-software.org/]("http://propertymanagement-software.org/")

---

### Post by perspectoff on 2010-09-17
> **k33bz said:**
> Sorry no, I am not looking for a Quickbooks equivalent, for finances I am using Grisbi.

What I need is a way to keep track of not only expenses, but info on property, photos of property, schedule maintenance and inspections, tenant information, list of contacts. 

I know I could use several programs to achieve this, such as using Grisbi for finance tracking, Contacts for obviously contacts, Dates for appointments, any number of databases for keeping other info, and Project Management for keeping track of hours worked on properties. But I rather use one single program that can do all of this.

Does anyone have any ideas?


Also, like Gnucash and KMyMoney, I think Grisbi is available as a Debian/Ubuntu package in the (Universe) repositories:

 sudo apt-get install grisbi


It's been about 3 years since I saw someone asking about property-management software for Linux, but the demand is certainly growing. There are so many small property managers...

I would be very interested in reviews of the two packages noted in the Freshmeat reference, if anyone evaluates them.

---

### Post by perspectoff on 2010-09-17
> **k33bz said:**
> I agree it is not hard at all, I have had my own web server. But it is not what I am after, I have a specific program in mind for when I do decide to use a web server.

On a downside, Wakodi is for a web server. So I guess I have no choice but to use how I have it set up now, using several different programs till I am ready for the web server.

BTW-- the web server program I will be using (besides the basic LAMP) is here [http://propertymanagement-software.org/]("http://propertymanagement-software.org/")

Because of security concerns, etc., in the beginning I have also been reluctant to use web-server based software. In the long-run, however, it is nice to have web access to a program like that, especially if you are traveling around to different properties and need mobile browser-based access.

While testing and setting up the software, of course, you needn't expose anything to the Internet. Just access it through "localhost" and leave the web-facing access (in Apache2) turned off. Once it is working properly and you are happy with security, then enable the site through Apache2 (or NGINX, or whatever it uses).

---

### Post by k33bz on 2010-09-17
> **perspectoff said:**
> Also, like Gnucash and KMyMoney, I think Grisbi is available as a Debian/Ubuntu package in the (Universe) repositories:

 sudo apt-get install grisbi


It's been about 3 years since I saw someone asking about property-management software for Linux, but the demand is certainly growing. There are so many small property managers...

I would be very interested in reviews of the two packages noted in the Freshmeat reference, if anyone evaluates them.

The programs I have installed right now, which there are several since I cant seem to find one program that runs on Linux (that is not for web servers) is:
Grisbi == For finances
Contacts == for contacts
Dates and Project Management == for keeping track of appointments and keeping track of rehabbing or maintenance on properties.
Glom == for Keeping track of tenants and properties

But as said I rather have just one single program to do it all. That is not web based. Once I am ready to open it up on the web (for my own use of course) I would be using Property Management (link is up above), even though there seems to be a few tweaks to make it run properly.

perspectoff thanks for the tips, I feel the same way, but as said before, I am not ready for the web on it as of yet. Sooner or later I will, just right now is not really an option.

---

### Post by eriktheblu on 2010-09-17
Would OO base be suitable for this?

It would require some work to create it, but I think it might suit your needs.

---

### Post by k33bz on 2010-09-17
> **eriktheblu said:**
> Would OO base be suitable for this?

It would require some work to create it, but I think it might suit your needs.

I am not familiar with that program at all, I will google and have a look see.

aww, nvm, I see that your talking about Open Office DataBase. Glom seems to have more power over OODB.

---

### Post by k33bz on 2010-09-20
So I broke down, and put my old server back together. Took most of it apart after my move and I shut down my web site. Was going to wait till I got a rack server before I got it up and running again. 

So for now it is a file server, have grisbi running off of it for finances, as well as Glom for everything else (well in process of configuring all the tables for it anyway). As well as storing some other stuff I did not want on my laptop taking up space no more.

Once I have the tables the way I like, if anyone wants a template for real estate on glom, just PM me, and I can send it to you. Be awhile before I have it operational though. :)

---

### Post by jtarin on 2010-09-20
Your probably aware of this and I don't know if you plan on using a Ubuntu setup but this quote from site.
> Unfortunately, Ubuntu's official Glom packages are not up-to-date so they contain significant bugs.they do have an updated non-repository [Ubuntu package onsite.]("http://www.glom.org/wiki/index.php?title=Download")

---

### Post by k33bz on 2010-09-20
> **jtarin said:**
> Your probably aware of this and I don't know if you plan on using a Ubuntu setup but this quote from site.
they do have an up to dated [Ubuntu package onsite.]("http://www.glom.org/wiki/index.php?title=Download")

I am using an Ubuntu setup, and was aware of a few bugs on glom. Sadly, or fortunately, I have yet come across those bugs. However in truth, I havnt really used Glom since 8.04. Looks like I will be going to the site and getting an update.

Thanks for looking out.

---

### Post by jtarin on 2010-09-20
> **k33bz said:**
> 
Thanks for looking out.That's what we do. :)

---

### Post by k33bz on 2010-09-21
> **perspectoff said:**
> Because of security concerns, etc., in the beginning I have also been reluctant to use web-server based software. In the long-run, however, it is nice to have web access to a program like that, especially if you are traveling around to different properties and need mobile browser-based access.

While testing and setting up the software, of course, you needn't expose anything to the Internet. Just access it through "localhost" and leave the web-facing access (in Apache2) turned off. Once it is working properly and you are happy with security, then enable the site through Apache2 (or NGINX, or whatever it uses).

Well property management software is out the window, not compatible with the most recent php5. And cant seem to force install it to a previous php5 that most likely would work. 

What software do you use?

---

### Post by perspectoff on 2010-09-21
> **k33bz said:**
> Well property management software is out the window, not compatible with the most recent php5. And cant seem to force install it to a previous php5 that most likely would work. 

What software do you use?

There is a method to downgrade from PHP5.3 to PHP5.2. Some Drupal users had to do that in Lucid, as well. Here is a link how they did it:

[http://groups.drupal.org/node/60908](http://groups.drupal.org/node/60908)

Also see:

[http://ubuntuforums.org/showthread.php?t=1459163](http://ubuntuforums.org/showthread.php?t=1459163)

Personally, I left my Drupal installation at Karmic. (I never upgrade a system directly. I always copy the Ubuntu system, upgrade the copy (only) and test it fully, and only if everything works 100% make it my production system).

---

