---
title: "installing LAMP"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by ubscott on 2010-09-21
hi,

i'm a newbie running Ubuntu 9.10.  i am trying to get Linux/Apache/PhP started.

when i start Synaptic package manager, search for 'MySQL Server', two appealing packages appear at the top of the list: libmysqlclient16 and mysql-common.  if i right-click on libmysqlclient16, choose properties, i see a dialogue saying it is installed.  If so, how come I don't see it as an option on one of my menu items?

i've been reading info on how to install mysql.  i've tried this command in a terminal window: sudo apt-get install libmysqlclient16, i get the message that this is 'already the newest version.'  

i'm also trying to get Apache and Php going.  Is it possible to find one package that installs them both?

when i search for Php in Synaptic package manager, i get one result: libgtksourceview2.0-common.  this is already installed (according to the properties).  does anyone know how i verify this?

when i search for Apache in package manager, i get python-couchdb, libdotconf1.0, libssl0.9.8, libcouchdb-glib-1.0-1, evolution-couchdb, librpc-xml-perl and couchdb-bin.  these are all installed, as per the properties dialogue.

when i search \dev\var\archives i see a folder: partial.  it is empty.  I was told this is where packages are installed.

so, do i have the correct packages for Apache/mySQL/PhP?  if so, how do i run one, say the MySQL server?

if not, what is a good suggested package for each?  it would be great to find one LAMP package if it exists.

thanks for the help.

---

### Post by sandyd on 2010-09-21
> **ubscott said:**
> hi,

i'm a newbie running Ubuntu 9.10.  i am trying to get Linux/Apache/PhP started.

when i start Synaptic package manager, search for 'MySQL Server', two appealing packages appear at the top of the list: libmysqlclient16 and mysql-common.  if i right-click on libmysqlclient16, choose properties, i see a dialogue saying it is installed.  If so, how come I don't see it as an option on one of my menu items?

i've been reading info on how to install mysql.  i've tried this command in a terminal window: sudo apt-get install libmysqlclient16, i get the message that this is 'already the newest version.'  

i'm also trying to get Apache and Php going.  Is it possible to find one package that installs them both?

when i search for Php in Synaptic package manager, i get one result: libgtksourceview2.0-common.  this is already installed (according to the properties).  does anyone know how i verify this?

when i search for Apache in package manager, i get python-couchdb, libdotconf1.0, libssl0.9.8, libcouchdb-glib-1.0-1, evolution-couchdb, librpc-xml-perl and couchdb-bin.  these are all installed, as per the properties dialogue.

when i search \dev\var\archives i see a folder: partial.  it is empty.  I was told this is where packages are installed.

so, do i have the correct packages for Apache/mySQL/PhP?  if so, how do i run one, say the MySQL server?

if not, what is a good suggested package for each?  it would be great to find one LAMP package if it exists.

thanks for the help.
[s]
```

sudo tasksel

```Press Enter.
Use the arrow keys to select LAMP 
press spacebar.
Use tab key to highlight OK. Press enter.
[/s]
mySQL is not a GUI app. Neither is Apache or PHP. All of them (Only mysql and Apache are servers) are started at computer bootup.

To install LAMP (Linux, Apache, MySQL, PHP)
```

sudo apt-get install php5 php5-gd php5-imagick php5-mcrypt php5-mysql php5-sqlite php5-suhosin mysql-server apache2 
```To get phpmyadmin
```

wget -c http://cdnetworks-us-2.dl.sourceforge.net/project/phpmyadmin/phpMyAdmin/3.3.7/phpMyAdmin-3.3.7-all-languages.tar.gz
sudo rm /var/www/*html
sudo tar xvfz phpMyAdmin-3.3.7-all-languages.tar.gz -O /var/www
sudo chown -R www-data:www-data /var/www

```

---

### Post by ubscott on 2010-09-22
hi, thanks for the reply.  

sudo tasksel ==> upon authentication, gives me a window with 'package configuration' at the top, background is navy blue. the three options are: 'print server', 'Ubuntu desktop'[ and 'Manual package selection'.

there's no way to find LAMP.  for each one i try, it takes me back to the terminal window.  i can arrow up and see old attempts i made to install packages, which i discussed in my first post.

how do i find LAMP and select it?  thanks.

---

### Post by ubscott on 2010-09-22
hi,

i think the problem is i'm running Ubuntu desktop, not server.  i am going to install the server.  thanks sandyd for the help.

---

### Post by CharlesA on 2010-09-22
You could probably run it on the desktop version fine.

After you do:

```
sudo tasksel
```

Select LAMP server and hit ok.

---

### Post by sandyd on 2010-09-22
> **CharlesA said:**
> You could probably run it on the desktop version fine.

After you do:

```
sudo tasksel
```Select LAMP server and hit ok.
ooh. 2800 beans.
and whats with all the mods having monster avatars :D ?

Anyways...
it works....

ans anyways too...
```

sudo apt-get install php5 php5-gd php5-imagick php5-mcrypt php5-mysql php5-sqlite php5-suhosin mysql-server apache2

```
should sort you out...

---

### Post by CharlesA on 2010-09-22
> **sandyd said:**
> 
and whats with all the mods having monster avatars :D ?

Not monsters... exactly..

> ```

sudo apt-get install php5 php5-gd php5-imagick php5-mcrypt php5-mysql php5-sqlite php5-suhosin mysql-server apache2

```


Yup, that'll work too.

Check [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") as well.

---

### Post by lisati on 2010-09-22
> **sandyd said:**
> 
and whats with all the mods having monster avatars :D ?

Wut?

---

### Post by ubscott on 2010-09-24
> You could probably run it on the desktop version fine. After you do:
sudo tasksel
 
hi Charles, thanks for the reply. However, in the prior post i said that LAMP is not an option for me when i do sudo tasksel. I wrote:
 
> sudo tasksel ==> upon authentication, gives me a window with 'package configuration' at the top, background is navy blue. the three options are: 'print server', 'Ubuntu desktop'[ and 'Manual package selection'.
 
there's no way to find LAMP. for each one i try, it takes me back to the terminal window. i can arrow up and see old attempts i made to install packages, which i discussed in my first post.
 
 
meanwhile, i was so sure that i needed Ubuntu server that i downloaded it, burned it to CD and then tried to install it, overwriting the Ubuntu desktop. unfortunately, the installation failed. i will start up a new post that describes it. (but i'll see that no one else has posted first about it.)
 
so, i'm kind of in limbo. if i could get LAMP with Ubuntu desktop i probably would. however, sudo tasksel doesn't give me LAMP. maybe i need to pursue the server.
 
thanks.

---

### Post by sandyd on 2010-09-24
> **sandyd said:**
> <snip>
```

sudo apt-get install php5 php5-gd php5-imagick php5-mcrypt php5-mysql php5-sqlite php5-suhosin mysql-server apache2

```should sort you out...

> **ubscott said:**
> hi Charles, thanks for the reply. However, in the prior post i said that LAMP is not an option for me when i do sudo tasksel. I wrote:
 

 
 
meanwhile, i was so sure that i needed Ubuntu server that i downloaded it, burned it to CD and then tried to install it, overwriting the Ubuntu desktop. unfortunately, the installation failed. i will start up a new post that describes it. (but i'll see that no one else has posted first about it.)
 
so, i'm kind of in limbo. if i could get LAMP with Ubuntu desktop i probably would. however, sudo tasksel doesn't give me LAMP. maybe i need to pursue the server.
 
thanks.
.

---

### Post by perspectoff on 2010-09-24
So I'm guessing the direct command

 sudo tasksel install lamp-server

does nothing for you either?

---

### Post by ubscott on 2010-09-24
Sandyd, thanks.  i ran the command you gave and it installed a lot of packages.  i am now taking a look at the presents that are now underneath the Christmas tree.  :P
 
i'll get the phpmyadmin when i can.  thanks a million.

---

### Post by CharlesA on 2010-09-24
At least phpmyadmin is easier to install with apt-get:

```
sudo apt-get install phpmyadmin
```

---

### Post by ubscott on 2010-09-25
hi Charles,
 
i installed phpMyAdmin using your syntax and it seemed to work fine. i saw the packages listed and i didn't see any error messages.
 
however, i can't seem to run it. i now have Apache, so this resolves:
[http://localhost](http://localhost)
 
however, neither of these do:
[http://localhost:80](http://localhost:80)
[http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)
 
i've visited this thread:
[http://ubuntuforums.org/showthread.php?t=386907](http://ubuntuforums.org/showthread.php?t=386907)
 
i've looked for phpMyAdmin installation files under var/www, but don't see them.
 
do you know how to fire up phpMyAdmin? thanks in advance.

---

### Post by sandyd on 2010-09-25
> **ubscott said:**
> hi Charles,
 
i installed phpMyAdmin using your syntax and it seemed to work fine. i saw the packages listed and i didn't see any error messages.
 
however, i can't seem to run it. i now have Apache, so this resolves:
[http://localhost](http://localhost)
 
however, neither of these do:
[http://localhost:80](http://localhost:80)
[http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)
 
i've visited this thread:
[http://ubuntuforums.org/showthread.php?t=386907](http://ubuntuforums.org/showthread.php?t=386907)
 
i've looked for phpMyAdmin installation files under var/www, but don't see them.
 
do you know how to fire up phpMyAdmin? thanks in advance.
```
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

---

### Post by ubscott on 2010-09-25
Hi Sandyd,
 
thanks for the command.  i ran it, and now i have phpMyAdmin files under var/www .
 
however, i still can't resolve this:
[http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)
 
I've tried these commands:
sudo slocate -u
sudo slocate phpmyadmin | grep index
 
but i get an error: 'slocate: command not found.'
 
do you have an idea how to move forward?  thanks.

---

### Post by sandyd on 2010-09-25
> **ubscott said:**
> Hi Sandyd,
 
thanks for the command.  i ran it, and now i have phpMyAdmin files under var/www .
 
however, i still can't resolve this:
[http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)
 
I've tried these commands:
sudo slocate -u
sudo slocate phpmyadmin | grep index
 
but i get an error: 'slocate: command not found.'
 
do you have an idea how to move forward?  thanks.
should be
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by ubscott on 2010-09-25
it works!! :P
 
thanks for the help!

---

