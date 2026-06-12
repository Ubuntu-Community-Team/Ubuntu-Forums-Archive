---
title: "Beginning Web Development: Major road-blocks"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Cheesemold on 2008-07-24
(I'm sorry, I'm not sure exactly where this thread would best fall under.)

So, I really want to learn how to develop web applications, but it seems I do not know enough about all the parts necessary.  What I mean, is that developing web applications requires multiple software packages and stuff running together smoothly, and a problem with any one of them results in the entire thing failing completely.  The entire world of documentation on the subject seems to implicitly know this, but sort of assumes that if you're reading up on a particular web framework, you must *already* know how to set everything else up.

I'm trying to learn web development with Django, since I already "know" the python programming language.  So far, the documentation on the site, and in wiki.ubuntu.com aren't helping that much.  For example, one of the first sentences in a piece of Django documentation told me to "make sure mod_python is activated."

Thanks.  Time to look up a second manual on apache to figure all of that out.

Literally every step is like this.

Right now I'm hung up on getting mysql set up.  Usually when I've had to do something like this, I type something like " sudo apt-get install NAME* -s" to look up all the packages associated with NAME.  This helped me narrow down what to use.  To my surprise, "sudo apt-get install mysql* -s" returns a very long list.  I already have 'mysql-common' installed, what now?  I also have python-mysqldb "installed" as well.

But in my week-long journey into starting to even *learn* web development I've found that it really does not matter if something is "installed" onto your server. No, that's not enough.  It has to be configured to run exactly in tuned with every other component of this project.  No apt-get commands for me.

This whole process is really frustrating and I wish there was some where that I could go to actually get through this without needing to look up manuals for the manuals that I looked up to read the introductory tutorial on a web framework.

Advice?

---

### Post by cdtech on 2008-07-24
The Ubuntu forum has a great social group called web development. You could sign up (no cost, just register). Everyone in that group will help you in your venture.

Just a suggestion.
Good luck..........

---

### Post by ad_267 on 2008-07-24
This sort of stuff will take a bit of getting used to but you should be able to get good help here. There's probably more information on setting up an apache - mysql - php server (eg [http://howtoforge.com/ubuntu_lamp_for_newbies](http://howtoforge.com/ubuntu_lamp_for_newbies)) than one with python but there might be something useful out there.

Some useful commands I can think of are:
sudo a2enmod - apache2 enable module
sudo a2dismod - apache2 disable module
sudo /etc/init.d/apache2 start - start apache
sudo /etc/init.d/apache2 restart - restart apache

You can just "apt-get install" most stuff you need, the tricky bit is working out what it is you need.

Edit: Google is your friend, this explains it. [http://www.fslog.com/2006/12/01/setting-up-lamp-on-your-ubuntu-desktop/](http://www.fslog.com/2006/12/01/setting-up-lamp-on-your-ubuntu-desktop/)

---

### Post by Cheesemold on 2008-07-24
> **cdtech said:**
> The Ubuntu forum has a great social group called web development. You could sign up (no cost, just register). Everyone in that group will help you in your venture.

Just a suggestion.
Good luck..........

How do I find social groups on the Ubuntu Forums?  Or are you referring to a different forums system than this one?

Thanks.

---

### Post by cdtech on 2008-07-25
Just go to the top "Quick Links > Networking > Social Groups".

Good Luck.......

---

