---
title: "Problem installing phpmyadmin"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by _Cathy_ on 2011-03-08
Hi there :) I am new to Ubuntu and PHP, so would really appreciate some help with something I am having trouble with! 

I have just installed LAMP in Ubuntu from Terminal, but am having some problems. I can veiw files by putting "localhost" in the browser, but cant get phpmyadmin. I installed it using: 

sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
(I followed the steps here under "Install My SQL": [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

but when I point to localhost/phpmyadmin in the browser it says it cant be found?!  

I would really appreciate any help!

Thanks :)

---

### Post by wizard10000 on 2011-03-08
phpmyadmin needs to be configured before it can be run.  Look here -

[http://www.phpmyadmin.net/documentation/](http://www.phpmyadmin.net/documentation/)

Hope this helps -

---

### Post by vivek.pandey on 2011-03-08
In ubuntu by default, phpmyadmin is installed in /etc/phpmyadmin Setting a symbolic link should help you. The command would be as follows :

$sudo ln -s /etc/phpmyadmin /var/www/phpmyadmin

After this, open [http://localhost/phpmyadmin](http://localhost/phpmyadmin) in browser and it should work.

---

### Post by _Cathy_ on 2011-03-08
> **neo_aryan said:**
> In ubuntu by default, phpmyadmin is installed in /etc/phpmyadmin Setting a symbolic link should help you. The command would be as follows :

$sudo ln -s /etc/phpmyadmin /var/www/phpmyadmin

After this, open [http://localhost/phpmyadmin](http://localhost/phpmyadmin) in browser and it should work.

thanks for your reply :) 

doesn't seem to work though...It returns "sudo: In: command not found"

---

### Post by vivek.pandey on 2011-03-08
> **_Cathy_ said:**
> thanks for your reply :) 

doesn't seem to work though...It returns "sudo: In: command not found"

no its without $..$signifies the prompt here

---

### Post by uRock on 2011-03-08
```
sudo ln -s /etc/phpmyadmin /var/www/phpmyadmin
```

---

### Post by btindie on 2011-03-08
You shouldn't need to do that as the phpmyadmin apache configuration file contains
```
Alias /phpmyadmin /usr/share/phpmyadmin
```which maps the php code into the web space.
/etc/phpmyadmin contains the configuration files for phpmyadmin, it's not the main installation point.

OP: did you restart apache after installing phpmyadmin?

---

### Post by _Cathy_ on 2011-03-08
> **uRock said:**
> ```
sudo ln -s /etc/phpmyadmin /var/www/phpmyadmin
```

doesnt do anything...?
EDIT: actually, now when I go to localhost/phpmyadmin I get an Index of /phpmyadmin with links to the files in the folder..

> **btindie said:**
> 
OP: did you restart apache after installing phpmyadmin?

yes- I did the last 5 steps in the link I posted in the OP

---

### Post by willow315 on 2011-03-13
I am having the exact same problem. Installed LAMP successfully, using apt-get on Ubuntu running in VirtualBox on a MACBook Pro.

All except phpMyAdmin....the installation completed successfully, but I cannot access phpMyadmin via [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin).

I have tried do the symbolic link as suggested, and I, too am getting nothing but a directory list. I was disappointed that there were no further posts about this problem.

Is there anyone checking these posts that could assist? 

I've tried about a million other remedies, and uninstalled and reinstalled numerous times. 

Thanks in advance, and Oh, BTW....how do I undo the symbolic link I created, since it does not seem to be the correct solution.

---

### Post by wizard10000 on 2011-03-14
Have either of you read the install documentation posted earlier?

phpmyadmin has to be configured before it'll run.

---

