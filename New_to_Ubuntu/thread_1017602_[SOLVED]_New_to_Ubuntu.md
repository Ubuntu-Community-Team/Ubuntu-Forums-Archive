---
title: "[SOLVED] New to Ubuntu"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by my_everything78 on 2008-12-21
Dears 
My name is Sizar and im new to Ubuntu .
I mangaed to install ubunto and windows xp side by side .
now what i want is to install php5 + apache2 +mysql from the scratch so i can start developing my php files under ubuntu..
I know there is a lot of documentation and site do accomplish what i want . but it makes me confuse .

So can any body here help to start all from the start ,
I did install Xampp and php5 and apachee and nothing is working , so I guess i need to start all over again.

Can you help =D>=D>
 I feel so excited with Ubuntu , and i hope i will be able to deal with it soon :)

Thank you  so much

---

### Post by northern lights on 2008-12-21
Run```
sudo apt-get install php5 apache2 mysql-admin
```apt-get will ignore whatever is installed already. You've installed from the repositories and not some version off the web, right?

---

### Post by BDNiner on 2008-12-21
[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)

This site contains a lot of very good tutorials on how to install software on a lot of different platforms. Where exactly are you stuck?

---

### Post by my_everything78 on 2008-12-21
Thank you sir for the fast respond 

Yes I did use the apt- get install .
then i used a package called Xampp .

Now if i use what you asked me to do , it will be it???
I mean i can then open my browser to test any php page?

Ok what about the data base how can i use it ?
In windows Xp I used a software called NavicatMySql . in unbuntu how it would be ?

Sorry for asking so much questions :)

Thank you again , for being so helpful .

---

### Post by albinootje on 2008-12-21
> **my_everything78 said:**
> 
I mangaed to install ubunto and windows xp side by side .

Congrats! :)
> 
now what i want is to install php5 + apache2 +mysql from the scratch so i can start developing my php files under ubuntu..
I know there is a lot of documentation and site do accomplish what i want . but it makes me confuse .

Xampp is one of the easiest setups if you want to develop for php.
Check the xampp FAQ for Linux :
[http://www.apachefriends.org/en/faq-xampp-linux.html](http://www.apachefriends.org/en/faq-xampp-linux.html)
And it's a good idea to tell us what does not work.
If you want to try the recommendation in the other posting, make sure you remove xampp first.

---

### Post by northern lights on 2008-12-21
> **my_everything78 said:**
> Now if i use what you asked me to do , it will be it???Entirely depends on what it is you want to do.

> **my_everything78 said:**
> I mean i can then open my browser to test any php page?That will now work.

I have no experience with xammp and do not use it. I code in emacs. If it's indeed an easy way of doing things, I can't add to the topic.

---

### Post by my_everything78 on 2008-12-21
thank you for the link sir 
i have ubuntu installed already , so i need to install php5 and the other mentioned packages .

where Im stuck ???
Well the problem is -- I installed php5 using the apt-get for the first time , and i guess it didnt work ,so i searched the net and found about Xampp and installed it , but it confuse me cause in Windows XP I knew where to add my files , in htdocs, but here i found the htdocs and i add a test php file and the browser didnt show it , which means something wrong in the installation or something wrong in the configuration .
Thats why i want to start all over from the begining , so i can understand every step and how the system is working ?

---

### Post by BDNiner on 2008-12-21
Yes if you follow the instructions in section 14 on page 4 of the guide for MySQL and the instructions in section 17 on page 6 for Apache and PHP. They are all instructions from the command line since the software is being setup on server edition, you should have a functioning MySQL database and apache and PHP setup on configured correctly.

---

### Post by my_everything78 on 2008-12-21
Thank you sir for your response 
Will i do feel confused ...
how can I start all over again . and which is the better way to develop php scripts on ubuntu :)

---

### Post by albinootje on 2008-12-21
> **my_everything78 said:**
> 
Well the problem is -- I installed php5 using the apt-get for the first time , and i guess it didnt work ,so i searched the net and found about Xampp and installed it , but it confuse me cause in Windows XP I knew where to add my files , in htdocs, but here i found the htdocs and i add a test php file and the browser didnt show it , which means something wrong in the installation or something wrong in the configuration .
Thats why i want to start all over from the begining , so i can understand every step and how the system is working ?

I think xampp for Linux installs in the /opt directory.

---

### Post by BDNiner on 2008-12-21
That is OK, moving from windows to linux can be confusing. If you want to start over you can remove all the software u installed.
```

sudo apt-get remove php5 apache2 mysql-admin

```

---

### Post by northern lights on 2008-12-21
> **my_everything78 said:**
> and which is the better way to develop php scripts on ubuntu
That's a question of preference. Try several. I'd code in an IDE and my IDE of choice is emacs. Try the xammp thingy. Try vi or vim (cost me quite some effort to get myself to write this as an emacs supporter...).

If you have the server version (must have read around that info) it should have indeed worked out of the box...

---

### Post by BDNiner on 2008-12-21
You can also consider using ubuntu server edition since that will go though the setup of a LAMP server which installs all the software you need. You will only have to install the ubuntu-desktop when you are done since it is a command line installation.
```

sudo apt-get install ubuntu-desktop

```

the server edition creates a basic apache, mysql and php configuration.

[http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html)

---

### Post by my_everything78 on 2008-12-21
Ok guys 
I guess I will remove all the packages and install them once again , and will till you about the result :)


Thank you so much for helping me out :)

---

### Post by my_everything78 on 2008-12-22
Hello everybody 
Just wanna tell you that php is working perfectly now .
You were so helpfull .

thank you all .

---

