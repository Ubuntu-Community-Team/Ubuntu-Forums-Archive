---
title: "how to print from mySQL database (to an ink printer)"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by gfunkera on 2009-06-02
how do you make it so you can print information from a mySQL server to a hard-wired ink printer (that prints on paper)?

the idea is to have users visit a PHP page and fill out a form. Then i want to go to the computer with the mySQL database and print out the form that was filled out by the user.

Its an order form web page that *should* (but doesnt have to) autoprint a page with the information on it everytime a user uses the form.. in order to keep records for a later date i would like to store the information somewhere, hence the mySQL database... thanks!

---

### Post by jonabyte on 2009-06-04
you may want to hire a developer to help you with this project.
there are free programs that can help you view your mysql data such as phpmyadmin, etc.

---

### Post by dje on 2009-06-04
have a look at using MySQL with PHP, you could then create a PHP/HTML/CSS page which shows the form and answers all filled out (using select statement to get required data) and neatly formatted. You could then print this page out. There are loads of tutorials out there, even the non specific PHP 5 For Dummies (i have it, it's good) has some info on basic MySQL usage

you may also wish to look into sqlite which is not as powerful, although great for small databases, but it does not require a database server. There is also some information in PHP 5 For Dummies and loads of tutorials on the web

dje

---

