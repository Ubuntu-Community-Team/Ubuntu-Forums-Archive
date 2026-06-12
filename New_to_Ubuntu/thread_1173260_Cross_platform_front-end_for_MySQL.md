---
title: "Cross platform front-end for MySQL"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Johan-Steyn on 2009-05-29
Hi All,

I talked to one of our developers this afternoon and we discussed the possibility of moving our MS Access 2007 .accdb custom office applications over to MySQL for purposes of using it in both Ubuntu Linux and Windoze.

I am pushing for the entire office to dump Windoze altogether and move to Ubuntu / Open Office. We have already incorporated KMyMoney in the finance dept as standard accounting package (Awesome App!). We are running XP dual boots on certian pc's. 

The only thing keeping us back from totally dumping Windoze, is the few remaining Access db's that were developed for HR / Training data management.  

The developer suggested that the MySQL db would require a front-end that is able operate cross platform as well.

Any suggestions?

Regards,

JS

---

### Post by Tibuda on 2009-05-29
What about the official MySQL tools?
Download the Windows version [here]("http://dev.mysql.com/downloads/gui-tools/5.0.html") and the ubuntu version with the [mysql-gui-tools-common]("apt:mysql-gui-tools-common") package.

---

### Post by funkyali on 2009-05-29
LAMP or better now known as XAMMP has a windows/linux front end.

I don't know if you heard of ORACLE Application Express (APEX) ([http://apex.oracle.com](http://apex.oracle.com)) its a user friendly open source application that sits inside an oracle DB. 

You can install it on ubuntu and then you use any web browser to access the data and create really fancy reports quiet quickly. It also has an easy to use MS Access DB migration setup as well.

If you need any help with APEX or need help just PM me.

---

### Post by Johan-Steyn on 2009-05-29
Hi danielrmt & funkyali,

Thanks for the suggestions.

I will check out both and post back.

Regards,

JS

---

### Post by kellemes on 2009-05-29
[phpMyAdmin]("http://www.phpmyadmin.net/home_page/index.php")

---

### Post by OffAxis on 2009-05-29
phpmyadmin and the mysql tools are good for administering databases, but not very good on the user side; no client inputs data with phpmyadmin.
Most people develop web pages with html & php for the client-side (front-end) stuff. It's cross platform but more than a little tedious.
If you're writing a front-end from scratch it can be coded in kbasic, python , or even java to be cross-platform.
 

if you're using ms access already, why not just use kexi?

[http://www.kexi-project.org/](http://www.kexi-project.org/)

It also has a mdb driver plugin, so you may be able to use your existing mdb backend with a kexi front end immediately. It's in the repos

```
sudo apt-get install kexi
sudo apt-get install kexi-mdb-plugin
```

---

### Post by funkyali on 2009-05-29
Johan,

Did not realise that you were from SA. Hows the Weather ov er there? I'm from there(Durban) but moved to the UK

---

### Post by Johan-Steyn on 2009-05-30
Hi funkyall,

Just saw you message. Weather's fine thank you. It's late autumn, so it's getting a bit chilly in Kempton Park.

Your post regarding Oracle looks promising. I'll ask the developer check it out on Monday. 

The problem is that it's not .mdb by accdb. 

Regards,

JS

---

### Post by funkyali on 2009-05-30
I was born in Joburg and stayed in Kempton Park as well, we coming into summer now so its getting really nice having lekker braai's.

I would sugest downloading Oracle XE which is a free oracle database that into APEX v2.2 and then upgrade APEX to the latest 3.1. 

If you go to the oracle link I sent you and click the top left hand corner the "sign up" you can try it before even downloading/installing it for free.

Just PM if you need any more help.

---

### Post by Johan-Steyn on 2009-05-30
Thanks,

I will check it out this weekend

Regards,

JS

---

### Post by anewguy on 2009-05-30
It's also fairly easy to create apps using GTK (available for Windows and Linux) as the GUI component.  I've done this with a few things, and other than (in C) a few #ifdef's to handle very very minor things between Windows and Linux, everything is a breeze.  As mentioned by someone else, JAVA would work as well.

Dave :)

---

