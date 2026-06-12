---
title: "setting up a server"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-04-03
im setting up a ubuntu 9.10 server for my anime website and i was wondering how would i go about doing the following


1.how to put the episodes on there 

2.how do i make it to where it looks like a website when people go to it


its a private web server so limited people will have access to it so i dont neet like a domain name or anything like that at all

---

### Post by johngreth on 2010-04-03
Open terminal, run:
```
sudo apt-get install lamp-server^
```
follow the directions to install it.

To make it look good, install [wordpress blog]("http://wordpress.org/") by downloading and unzipping it, thin copy the files into /var/www on the server. 

Run:```
sudo apt-get install phpmyadmin
```
and goto [http://serveraddress/phpmyadmin](http://serveraddress/phpmyadmin) and login username: "root" password whatever you set it as when installing LAMP server. Add a user and database for wordpress to use and goto [http://serveraddress/](http://serveraddress/) to configure the wordpress. Then you can log into wordpress and create posts to serve as your episodes.

Also, are you using server edition or desktop edition?

---

### Post by pyrofreak99 on 2010-04-03
im using server edition

---

### Post by johngreth on 2010-04-03
In that case it will automatically run tasksel when you install it, so just select and install Lamp-server.

---

### Post by abeisgreat on 2010-04-04
> **pyrofreak99 said:**
> im setting up a ubuntu 9.10 server for my anime website and i was wondering how would i go about doing the following


1.how to put the episodes on there 

2.how do i make it to where it looks like a website when people go to it


its a private web server so limited people will have access to it so i dont neet like a domain name or anything like that at all

I'd recommend running apache2
```

sudo apt-get install apache2

```
Then place any files you want to server in /var/www/. An index.html file will already be in that folder, you can edit it to make a webpage to link to your videos. Some configuration may need to be done to properly server the videos, I'm not sure. But that should get you started.

---

### Post by johngreth on 2010-04-04
Are you comfortable writing html code? If so what abeisgreat said would be a lot easier to set up. Other wise what I suggested will take more time to set up but will be easier to use in the future.

---

