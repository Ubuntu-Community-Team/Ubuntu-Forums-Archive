---
title: "Am I screwed?  chown on joomla folder, can't login"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by dawemmy on 2010-07-09
hey wow do I need help!!
wanted to be able to change the css in a template in joomla folder in var/www/joomla
but the folder had lock on it  did--
sudo chown -R dawemmy:dawemmy /var
now i can't log in to backend of joomla installed as localhost  as admin
error is "don't have access to adminstrator section"
have linux lampp intalled  done by a tut through terminal
tried clearing cache and reversing the chown
did:  chown -R root /var  but operation not allowed


here is the contents of the bash file

[CENTER]lspci
cd desktop
sudo -s
cd desktop
cd Desktop
tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
/opt/lampp/lampp start
/opt/lampp/lampp security
dawemmy -R /opt/lampp/htdocs
chown dawemmy -R /opt/lampp/htdocs
cd -/Desktop
cd ~/local/share/applications
sudo ./lampp start
sudo /opt/lampp/lampp
cd..
gedit ~/.local/share/applications/xampp-contrl-panel.desktop
sudo
sudo gedit /usr/share/applications/xampp-control-panel.desktop
sudo /opt/lampp/lampp start
gedit ~/.local/share/applications/xampp-control-panel.desktop
sudo /opt/lampp/lampp start
sudo /opt/lampp/lampp stop
sudo /opt/lampp/lampp start
sudo /opt/lampp/lampp stop
sudo rm -rf /opt/lampp
tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
/opt/lampp/lampp start
/opt/lampp/lampp security
chown  yourusername -R /opt/lampp/htdocs
chown dawemmy -R /opt/lampp/htdocs
/opt/lampp/lampp stop
cd Desktop
sudo -s
/opt/lampp/lampp start
/opt/lampp/lampp stop
sudo ln -s ~/public_html /opt/lampp/htdocs/
chown dawemmy -R /opt/lampp/htdocs
/opt/lampp/lampp start
chown lampp -R/opt/lampp/htdocs
chown lampp -R /opt/lampp/htdocs
chown dawemmy -R /opt/lampp/htdocs
sudo -s
/opt/lampp/lampp start
/opt/lampp/lampp stop
sudo -s
rm -rf /opt/lampp
cd Desktop
sudo -s
tar xvfz xampp-linux-1.7.3a.tar.gz 
/opt/lampp/lampp start
tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
/opt/lampp/lampp start
rm -rf /lampp
chown dawemmy -R /lampp
chown dawemmy -R lampp
rm -rf lampp
/opt/lampp/lampp security
/opt/lampp/lampp stop
/opt/lampp/lampp start
/opt/lampp/mysql start
sudo ln -s ~/public_html /opt/lampp/htdocs
chown dawemmy -R /opt/lampp/htdocs
/opt/lampp/lampp stop
sudo -s
/opt/lampp/lampp start
/opt/lampp/lampp stop
rm -rf /opt/lampp
cd Desktop
sudo -s
tar xvfz xampp-linux-1.7.2.tar.gz -C /opt
/opt/lampp/lampp start
/opt/lampp/lampp security
chown dawemmy -R /opt/lampp/htdocs
/opt/lampp/lampp stop
/opt/lampp/lampp start
/opt/lampp/lampp stop
wget [http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb](http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb)
gksudo gedit /etc/apt/sources.list
sudo add-apt-key ppa:chromium-daily/ppa
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
sudo apt-get update
sudo apt-get install chromium-browser
sudo apt-get update
clear
sudo apt-get apache2
sudo -s
clear
sudo apt-get install apache2
sudo apt-get install php5 php5-mysql libapache2-mod-php5
sudo chown -R dawemmy /var/www
gedit /var/www/testinfo.php
sudo /etc/init.d/apache2 restart
clear
sudo apt-get install mysql-server
sudo apt-get install phpmyadmin
sudo /etc/init.d/apache2 restart
sudo apt-get remove phpmyadmin
sudo apt-get install phpmyadmin
sudo /etc/init.d/apache2 restart
sudo apt-get remove phpmyadmin
sudo dpkg-reconfigure -plow phpmyadmin
sudo apt-get install phpmyadmin
sudo dpkg-reconfigure -plow phpmyadmin
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
sudo dpkg-reconfigure -plow phpmyadmin
clear
sudo dpkg-reconfigure -plow phpmyadmin
sudo apt-get remove phpmyadmin
cd /var/www/
sudo svn checkout [https://phpmyadmin.svn.sourceforge.net/svnroot/phpmyadmin/tags/STABLE/phpMyAdmin](https://phpmyadmin.svn.sourceforge.net/svnroot/phpmyadmin/tags/STABLE/phpMyAdmin) phpMyAdmin
sudo apt-get install phpmyadmin
Include /etc/phpmyadmin/apache.conf
sudo dpkg-reconfigure -plow phpmyadmin
sudo /etc/init.d/apache2 restart
start apache
cd var/www
cd /var/www/
mkdir joomla
cd joomla
cd..
cd Desktop
SOURCEPKG=Joomla_1.5.15-Stable-Full_Package.tar.bz2
sudo -s
tar xvjf Joomla_1.5.15-Stable-Full_Package.tar.bz2 -C /var/www/joomla
sudo chown -R www-data /var/www/joomla
rm -f $SOURCEPKG
cd /var/www/joomla
sudo find . -type -exec chmod 644 {} \;
sudo find . -type f -exec chmod 644 {} \;
sudo find . -type d -exec chmod 755 {} \;
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart
mysqladmin -u root -p create joomlawib
mysql -u root -p
gedit ~/.mysql_history
sudo /etc/init.d/apache2 restart
rm -rf installation
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/php5
sudo /etc/init.d/mysql
sudo /etc/init.d/mysql stop
cd downloads
cd Desktop
sudo dpkg -i AdbeRdr9.3.2-1_i386linux_enu.deb 
cd Desktop
sudo dpkg -i leo_4.7.1-1_all.deb 
sudo add-apt-respository ppa:sevmek/ekiga-released
sudo ufw status
sudo chown -R dawemmy:/var/www/joomla
sudo chown -R dawemmy/joomla
chown --help
sudo chown -R dawemmy:dawemmy filesystem/var/www/joomla
sudo chown -R dawemmy:dawemmy var/www/joomla
sudo chown -R dawemmy:dawemmy /joomla
cd filesystem
cd home
cd var
cd dawemmy
cd root
sudo chown -R dawemmy:dawemmy /var
gedit ~/.bash_history
sudo chown -R root:root /var
chown -R root /var
[/CENTER]

what can I do now? don't want to start over, almost done with my site
please, please, please!
dawemmy

---

### Post by nothingspecial on 2010-07-09
But you didn`t reverse the chown because not everything in /var is owned root:root

So I would say, yes you are screwed.

Someone may have an idea, but because everyones`s /var is different there isn`t much point attaching the output```
 sudo ls -l -R /var
``` and I can`t see how else you could put it right other than going through the thousands of files in there individually.

---

