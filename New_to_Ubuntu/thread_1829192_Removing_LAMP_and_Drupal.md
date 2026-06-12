---
title: "Removing LAMP and Drupal"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by youngros on 2011-08-20
Although I have tried Ubuntu before, this is the first time I have installed it on its own. No problems there, but trying to get LAMP and Drupal running. Already run WAMP and Drupal. Just want it as a test area, not live to the world and it is the problem of passwords that has got me in a mess. I thought I had used the same username and passwords for everything, but obviously not as I couldn't access phpmyadmin.
Is there a fool proof way to remove all that I have installed and then to reinstall it? 101 different ways seem to be out there and it just gets confusing. Really don't want to start out by reformatting the hard drive as the basics are running well.
Thanks.

---

### Post by cariboo on 2011-08-22
You didn't tell us what version you are using, or how you installed LAMP and Drupal. If you used the Software Center, you can use it to uninstall the applications. Personally I prefer Synaptic Package Manager, but use which ever application works best for you.

---

### Post by Overcast32 on 2011-08-22
Well.. I did something similar lately.
I removed LAMP to install XAMPP.. 

I did this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Followed the steps for *"Starting over, How to remove the LAMP stack"*

> Starting over, How to remove the LAMP stack

To remove the LAMP stack remove the following packages:

    * Note: This assumes you have no other programs that require any of these packages. You might wish to simulate this removal first, and only remove the packages that don't cause removal of something desired. 

apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

To also remove the debconf data, use the purge option when removing. To get rid of any configurations you may have made to apache, manually remove the /etc/apache2 directory once the packages have been removed. 

You would 'sudo apt-get remove *package*' for most of the above - I worked backwards on that above list - many were already gone as it removed dependencies along the way. This, of course, assumes the versions listed for the modules above too... 

Don't forget a 'sudo apt-get update' in the end too ;)

Then installed XAMPP without any issues.

XAMPP is a nice, clean version that totally 'installs' to a single folder (/opt/lampp). I would recommend it for web development, but not web production servers.. but even then, if you are security conscious and make sure you get it secured, not sure it wouldn't work just fine.

I would recommend **cariboo907**'s method if that works, however. Using the built-in Debian/Ubuntu installers keeps everything clean.

---

### Post by youngros on 2011-08-26
Thanks for the replies.
I installed the LAMP stack using sudo tasksel install lamp-server and then initially installed Drupal using sudo apt-get install drupal6 which installs Drupal in the etc folder, as this wasn't the latest version of Drupal, I uninstalled  via the synaptic manager, but this left the drupal folder still there. I reinstalled Drupal using the wget method that installs to /var/www/ and everything eventually worked, sort of trial and error. But what I couldn't get to work was phpmyadmin which I am used to working with. So I think I will go back and remove LAMP and install XAMPP instead as I see that includes phpmyadmin. 
Hopefully the more I use Ubuntu the more familiar I will get with everything.

---

### Post by sandyd on 2011-08-26
> **youngros said:**
> Thanks for the replies.
I installed the LAMP stack using sudo tasksel install lamp-server and then initially installed Drupal using sudo apt-get install drupal6 which installs Drupal in the etc folder, as this wasn't the latest version of Drupal, I uninstalled  via the synaptic manager, but this left the drupal folder still there. I reinstalled Drupal using the wget method that installs to /var/www/ and everything eventually worked, sort of trial and error. But what I couldn't get to work was phpmyadmin which I am used to working with. So I think I will go back and remove LAMP and install XAMPP instead as I see that includes phpmyadmin. 
Hopefully the more I use Ubuntu the more familiar I will get with everything.
Theirs a seperate password for phpmyadmin.
Should be set during the mysql configuration.

---

