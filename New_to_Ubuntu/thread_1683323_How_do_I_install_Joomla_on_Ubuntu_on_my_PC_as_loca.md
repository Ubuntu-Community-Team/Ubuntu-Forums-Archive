---
title: "How do I install Joomla on Ubuntu on my PC as localhost?"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by kopial on 2011-02-07
Why is it so difficult to install Joomla on Ubuntu? Its so frustrating...there is no complete guide on how to exactly do this on Ubuntu. I've been trying for to get help for the last 6 hours but I just still can't get it going.  Joomla supposed to be open source friendly system seems to have better guides on how to do it on a Windows OS but not an official documentation on how to do it on Ubuntu. Maybe they have begun to feel Windows is more relevant than Linux?? :confused:

For goodness sake, 
1. Could someone tell me where should I install XAMPP or LAMPP?
2. Where do I move my unzipped Joomla directory?? To /var/www/Joomla or /opt/lampp/htdocs/Joomla??:confused:
3. All the guides I found on the forum assume that beginner Ubuntu users don't exist.

---

### Post by [Snc] on 2011-02-07
hm ... i never installed Joomla!, but maybe can shed some light on some matters here ...

When you install LAMP (Linux Apache Mysql PHP) you get a /var/www location, which is the root of your web server, the documentation says "open a browser and type 'localhost' in the URL" and you should get a "It works!" message.

This means, WWW is running. now find something like MySQL Administrator or MySQL Browser (i use both) and check if the MySQL server is up and running.

From now on you have all you need. You can follow the rules, that apply for windows, just consider /var/www as your Apache root.

---

### Post by [Snc] on 2011-02-07
And if that is not helpful :) here is the documentation from Ubuntu [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

---

### Post by kopial on 2011-02-07
Hi, thanks...I have managed to install XAMPP on ubuntu however I am still having problem installing Joomla on my localhost. The error message is  as below:

  	 	 	 	p { margin-bottom: 0.08in; }  You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TYPE=MyISAM CHARACTER SET `utf8`' at line 29 SQL=CREATE TABLE `jos_banner` ( `bid` int(11) NOT NULL auto_increment, `cid` int(11) NOT NULL default '0', `type` varchar(30) NOT NULL default 'banner', `name` varchar(255) NOT NULL default '', `alias` varchar(255) NOT NULL default '', `imptotal` int(11) NOT NULL default '0', `impmade` int(11) NOT NULL default '0', `clicks` int(11) NOT NULL default '0', `imageurl` varchar(100) NOT NULL default '', `clickurl` varchar(200) NOT NULL default '', `date` datetime default NULL, `showBanner` tinyint(1) NOT NULL default '0', `checked_out` tinyint(1) NOT NULL default '0', `checked_out_time` datetime NOT NULL default '0000-00-00 00:00:00', `editor` varchar(50) default NULL, `custombannercode` text, `catid` INTEGER UNSIGNED NOT NULL DEFAULT 0, `description` TEXT NOT NULL DEFAULT '', `sticky` TINYINT(1) UNSIGNED NOT NULL DEFAULT 0, `ordering` INTEGER NOT NULL DEFAULT 0, `publish_up` datetime NOT NULL default '0000-00-00 00:00:00', `publish_down` datetime NOT NULL default '0000-00-00 00:00:00', `tags` TEXT NOT NULL DEFAULT '', `params` TEXT NOT NULL DEFAULT '', PRIMARY KEY (`bid`), KEY `viewbanner` (`showBanner`), INDEX `idx_banner_catid`(`catid`) ) TYPE=MyISAM CHARACTER SET `utf8`
 

I do no know that means.:confused:

---

### Post by M0use on 2011-02-08
Once you install xampp unpack joomla into the directoryyouinstalledto/xampp/htdocs then run the installation from the web browser make sure that you have the apache and mysql services running on xampp. 
read this joomla document for installation directions [http://downloads.joomlacode.org/docmanfileversion/1/7/4/17471/1.5_Installation_Manual_version_0.5.pdf](http://downloads.joomlacode.org/docmanfileversion/1/7/4/17471/1.5_Installation_Manual_version_0.5.pdf)

---

### Post by kopial on 2011-02-08
Hey guys really appreciate all your help, I'm still having error on this after following the steps below:

1. Unpack xampp 1.7.4 into /opt
2. Start lampp: sudo /opt/lampp/lampp start (apache, mysql & ftp ok)
3. Unpack Joomla 1.5 into /opt/lampp/htdoc & rename folder to "joomla"
4. Open [http://localhost](http://localhost) in firefox (ok, all seems to be ok)
5. Open phpMyAdmin & create a database named "joomla" using "utf8_general_ci"
6. Open [http://localhost/joomla](http://localhost/joomla) & try to install Joomla
7. Pre-installation check 1 red : configuration.php Writable, rest is ok (green)
8. Proceed to install (localhost, root, password, joomla)
9. Upon pressing next, I get an error:

[http://i1138.photobucket.com/albums/n533/kopial/Ubuntu%20stuff/Screenshot.png](http://i1138.photobucket.com/albums/n533/kopial/Ubuntu%20stuff/Screenshot.png)

---

### Post by kopial on 2011-02-09
Finally I got through this problem. Remove the Lampp 1.7 then install an older Lampp 1.64 version.

---

### Post by ferdz_30 on 2011-02-16
Ihaven't tried installing joomla yet. But I've succesfully configured XAMPP in UBUNTU. This might be helpful.
You can follow my steps on how I perfectly installed and configured my  XAMPP. I also experienced a lot of issues regarding the installation and  configuration of XAMPP on Ubuntu.

Here is what I did.

[SIZE=6]How to perfectly set-up XAMPP 1.7.4 in Ubuntu version 10.x[/SIZE]
 

 **[Step 1:] DOWNLOAD THE .tar FILE.**
 

 Download the tar file of xampp from  
 

 [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)
 

 and choose "Xampp for Linux"
 

 **[Step 2:] PASTE .tar FILE TO YOUR DESKTOP**
 

 After downloading the TAR file, cut and paste it to your desktop
 

 **[Step 3:] LOG IN AS ROOT**
 

 Open-up your terminal  
 

 Type in:
 

 sudo   (to enter commands with the root privileges, then type in your root password.)
 Enter your 'root password.'
 

 Then, type in:  
 

 cd /
 cd home/j0rdann3/Desktop
 

 **[Step 4:] UNTAR / EXTRACT ALL FILES OF &#8220;xampp-linux-1.7.4.tar.gz&#8221; TO /opt FOLDER**
                **IN YOUR FILE SYSTEM ** 
 

  by typing in the following codes:
 

         tar xvfz xampp-linux-1.7.4.tar.gz -C /opt
 

 **[Step 5:] START THE XAMPP SERVICE ** 
 

 by typing:
         /opt/lampp/lampp start
 

 **[Step 6:] SET SECURITY PASSWORDS FOR APACHE, MYSQL, PHPMYADMIN and FTPD**
 

 by typing:  
         /opt/lampp/lampp security
 

 Set your passwords to whatever you want. Then write it to a paper so you won't forget.
 

 

 

 **[Step 7:] OPEN XAMPP PAGE ON BROWSER**
 

 Open-up your web browser then type:
                         [http://localhost]("http://localhost/")
 

 A message box will appear asking for you username and password.
 

 Type '**lampp**' as your username (without quotes) and type the password you set for FTPD
 

 **[Step 8:] STOP XAMPP SERVICES FOR A MOMENT TO CHANGE THE OWNERSHIP OF THE ** 
 

 **       FOLDER  _/opt/lampp/htdocs_   AND THE FILE _ lang.tmp_ inside the ** 
 

 **       /opt/lampp/htdocs/xampp/ directory to 'nobody'**
 

 Note: Before perfoming A,B & C, make sure that you're still logged in as root. (If your not anymore, type su -s on the terminal)
 

 **A. **To stop XAMPP's services, on the terminal, type '/opt/lampp/lampp stop' (without quotes)
 

 **B. **To change **htdocs' folder** ownership to your username: (For example, my username is j0rdann3)
        
      On the terminal, type '**chown j0rdann3 -R /opt/lampp/htdocs**' (without quotes)
 

 **C.** To change **lang.tmp's** ownership to 'nobody'
 

     On the terminal, type '**chown nobody /opt/lampp/htdocs/xampp/lang.tmp** ' (without quotes)
 

 

 The reason of performing step 8 is to avoid known issues such as  
 
[LIST]
[*]
[LIST]
[*]persistent redirection of xampp's         language selection page over and over
[*]Unableness to copy files to         'htdocs' folder
[/LIST]
 
[/LIST]
 

 **[STEP 9:] START XAMPP's SERVICES AGAIN (Make sure you're still logged in as root in the       ** 
 

 **terminal)**
 

     by typing '**/opt/lampp/lampp start**' (without quotes)
 

 

 

 That's it, that's what i did for it to work.
 

 I hope that this would, in someway help you. 

 

 Goodluck. =)

---

### Post by YeeP on 2011-02-27
Followed your instructions to a T (and others)...

-----------
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
-----------

This is all I ever get, no splash screen for XAMPP like what is shown on their web site. I have all of the files for the apache server, and phpmyadmin that where downloaded with xampp, so I dont understand the purpose of going to these instructions and following them.

[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

Seems like you are doing it twice.  [http://localhost/phpmyadmin](http://localhost/phpmyadmin) gives a 404 error.

Any help would be much appreciated.

---

