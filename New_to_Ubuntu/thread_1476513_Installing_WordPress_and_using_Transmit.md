---
title: "Installing WordPress and using Transmit"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by macmike on 2010-05-07
I have set up a Web Server. The world can see it. I have also set up Virtual Hosting. Now I need to learn  how to install Word Press on to the Web site that is on this server. I  have downloaded the files from WordPress.org. Also can't figure out to use Transmit to get to the server either. Just can't get them into  the server. Please help.

Mike Hughes

---

### Post by brennydoogles on 2010-05-07
> **macmike said:**
> I have set up a Web Server. The world can see it. I have also set up Virtual Hosting. Now I need to learn  how to install Word Press on to the Web site that is on this server. I  have downloaded the files from WordPress.org. Also can't figure out to use Transmit to get to the server either. Just can't get them into  the server. Please help.

Mike Hughes


How are you currently accessing the machine? If it is local and you just sit down at it to use it, simply download the files, drop them into the directory that you set up in your Virtual Host, and follow the directions on Wordpress.org. Alternately, you can install wordpress using the repositories with:
```
sudo aptitude install wordpress
```

although I'm not sure where it will install the blog.

If you are connecting to the server using ssh or ftp, post back about it and I will see what I can do to help you get it set up.

---

### Post by macmike on 2010-05-07
Right now I can see the page by typing in [www.wilmingtoncoc.com](www.wilmingtoncoc.com). I have two Virtuals set up right now. One is the Wilmingtoncoc.com and the other one is my site [www.mikealrhughes.com](www.mikealrhughes.com). Although I haven't changed the forwarding on it. I will be administering it through Dreamweaver and it currently has some CGI scripts to get working again once it is forwarded to my server. I thought if I can get this one going first before moving to that site and then getting mailman going for my mail list. I also, as far as I know, don't have a user name and password set for this Website and didn't see how to do that. When I tried to use Transmit it wanted that information. Appreciate the help.

---

### Post by brennydoogles on 2010-05-07
> **macmike said:**
> Right now I can see the page by typing in [www.wilmingtoncoc.com](www.wilmingtoncoc.com). I have two Virtuals set up right now. One is the Wilmingtoncoc.com and the other one is my site [www.mikealrhughes.com](www.mikealrhughes.com). Although I haven't changed the forwarding on it. I will be administering it through Dreamweaver and it currently has some CGI scripts to get working again once it is forwarded to my server. I thought if I can get this one going first before moving to that site and then getting mailman going for my mail list. I also, as far as I know, don't have a user name and password set for this Website and didn't see how to do that. When I tried to use Transmit it wanted that information. Appreciate the help.

Have you set up any FTP users? If not, that will be your next step. Afterwards (or now if you have already set up FTP users), you will be able to log in using those credentials. Also, if you are using Dreamweaver and Transmit I assume you are using a Mac, correct? I won't be much help with Transmit having never used it, but you should be able to set up Dreamweaver to automatically FTP your work to the site when you save.

---

### Post by macmike on 2010-05-07
How do I set up FTP users? Yes I am on a mac.

See how I can send you my grab from transmit. Ok I converted the file to a JPeg so you can see the information I have to give Transmit.

Mike

---

### Post by brennydoogles on 2010-05-08
> **macmike said:**
> How do I set up FTP users?

[This link to UbuntuGeek]("http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html") should get you started.

---

### Post by macmike on 2010-05-08
I installed proftpd when I try and edit the conf file for it from the command sudo vi /etc/proftpd.conf . I get a blank screen like there is no file. When I go to the Desktop and then go to /etc/proftpd.conf I can get it on screen to edit. When I do and try to save it says access denied. So I am at a loss unless the directory structure isn't right. What do you think? Also how do I download Webmin. I tried the sudo apt-get install Webmin and it did nothing. I downloaded it using Firefox but can't get it to install.

---

### Post by sandyd on 2010-05-08
> **macmike said:**
> I installed proftpd when I try and edit the conf file for it from the command sudo vi /etc/proftpd.conf . I get a blank screen like there is no file. When I go to the Desktop and then go to /etc/proftpd.conf I can get it on screen to edit. When I do and try to save it says access denied. So I am at a loss unless the directory structure isn't right. What do you think? Also how do I download Webmin. I tried the sudo apt-get install Webmin and it did nothing. I downloaded it using Firefox but can't get it to install.
```

wget -c http://wordpress.org/latest.tar.gz
tar xvfz latest
cd wordpress*
mv * [I]_**/directory/where/your/virtual/hosting/root/is**_

```
[/I]As for webmin....
```

wget -c http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb
sudo dpkg -i webmin_1.510-2_all.deb
sudo apt-get -f install
```

---

