---
title: "[HELP] A few noob problems."
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-08-22
Hi,

I'm a beginner Linux user and I've just installed ubuntu on my laptop, however I have a few issues.

1. A really annoying problem here. Even with my sound switched off, if I press the backspace key when using the Login input boxes or the IRC input boxes etc etc I get a loud and very annoying "beep". Does anyone have any idea how I can disable this? Thanks.

2. As a web developer one of the first things I decided to install Xampp for Linux (LAMPP). I checked 'sudo apt-cache search lampp' and the same for xampp in the terminal but I couldn't find anything, so I went ahead and downloaded the .tar.gz file from their website, however, I have no idea what to do with it! Can anyone please help me install it using the .tar.gz file? Thanks.

~Letterbomb05.

---

### Post by BackwardsDown on 2009-08-22
For the beep problems you can try this:
[http://strabes.wordpress.com/2006/10/16/remove-the-system-beep-in-ubuntu/](http://strabes.wordpress.com/2006/10/16/remove-the-system-beep-in-ubuntu/)

LAMP is is php mysql apache and phpmyadmin, so:
sudo apt-get install mysql-server apache php5 php5-mysql phpmyadmin
(or install those packages with synaptic)

---

### Post by lisati on 2009-08-22
The dreaded "beep"! This is likely to be your computer's speaker. There are a number of discussions about this. One such discussion can be found here: [http://ubuntuforums.org/showthread.php?t=1246654&highlight=pc+speaker+beep](http://ubuntuforums.org/showthread.php?t=1246654&highlight=pc+speaker+beep)

---

### Post by earthpigg on 2009-08-22
are you sure you aren't looking for Apache webserver? and/or MySQL? and/or Perl?

LAMP = Linux, Apache, MySQL, and Perl/PHP.

synaptic (system -> admin -> synaptic package manager) is outstanding for browsing packages, by the way.

im no web dev, btw, so i really am not sure what the difference is between XAMPP and simply installing apache, mysql, perl, and php....

---

### Post by Letterbomb05 on 2009-08-22
> **earthpigg said:**
> are you sure you aren't looking for Apache webserver? and/or MySQL? and/or Perl?

LAMP = Linux, Apache, MySQL, and Perl/PHP.

synaptic (system -> admin -> synaptic package manager) is outstanding for browsing packages, by the way.

im no web dev, btw, so i really am not sure what the difference is between XAMPP and simply installing apache, mysql, perl, and php....

XAMPP is simple a package that has everything you need in one installation, and with windows at least its a lot easier to just install that than having to configure everything separately.

---

### Post by sandyd on 2009-08-22
p.s. after installing LAMP with the instructions above, you might want to check if you want some of the textensions.
their named php5-*

---

### Post by sandyd on 2009-08-22
```

sudo mkdir /opt
sudo mkdir /opt/webserver
sudo chown your_username_here /opt/webserver
sudo chmod 777 /opt/webserver
cd ~/Desktop
wget http://downloads.sourceforge.net/project/xampp/XAMPP%20Linux/1.7.2/xampp-linux-1.7.2.tar.gz?use_mirror=iweb
tar xvzf xampp-linux-1.7.2.tar.gz -C /opt/webserver

```

Then, to start XAMMP
```

sudo /opt/webserver/lampp/lampp start

```

Paremeters

[LIST]
[*]start - Starts XAMPP.
[*]stop - Stops XAMPP.
[*]restart - Stops and starts XAMPP.
[*]startapache - Starts only the Apache.
[*]startssl - Starts the Apache SSL support. This command activates the SSL support permanently, e.g. if you restarts XAMPP in the future SSL will stay activated.
[*]startmysql - Starts only the MySQL database.
[*]startftp - Starts the ProFTPD server. Via FTP you can upload files for your web server (user "nobody", password "lampp"). This command activates the ProFTPD permanently, e.g. if you restarts XAMPP in the future FTP will stay activated.
[*]stopapache - Stops the Apache.
[*]stopssl - Stops the Apache SSL support. This command deactivates the SSL support permanently, e.g. if you restarts XAMPP in the future SSL will stay deactivated.
[*]stopmysql - Stops the MySQL database.
[*]stopftp - Stops the ProFTPD server. This command deactivates the ProFTPD permanently, e.g. if you restarts XAMPP in the future FTP will stay deactivated.
[*]security - Starts a small security check programm.
[/LIST]
use them by doing
```

sudo /opt/webserver/lampp/lampp [parameter]

```
replace [parameter] with one of the parameters in the above messy list. 

there is unfortunately, no xampp control panel for linux yet... i think....
aren't i amazing? ;)

---

