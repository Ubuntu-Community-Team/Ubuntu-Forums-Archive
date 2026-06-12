---
title: "Trying to run xampp (PHP, APACHE, MYSQL) do I need root?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by jcathcart on 2009-03-23
Hello Everyone,

I am not sure how much of an absolute beginner I am, but it's been a while so I'm starting here.  This is what I am trying to do:

I want to use xampp, which is a bundle of the apache web server with PHP and MySQL, so that I can test my web applications locally.  I was using it in Windows recently, but Windows and I had an argument and it no longer lives.

[http://www.apachefriends.org/download.php?xampp-linux-1.7.tar.gz](http://www.apachefriends.org/download.php?xampp-linux-1.7.tar.gz)

The file I downloaded is:

xampp-linux-1.7.tar.gz


When I used to use Linux (slakware or Mandriva) I logged in as root to do the following parts, but as I read in the -edit- Ubuntu -edit- pocket guide it doesn't seem that you can use root in the console....  

So I ran the command:

tar -zxvf xampp-linux-1.7.tar.gz

It then did what you would expect and extracted all of the files to their appropriate directory/subdirectory.

The steps for installation and downloadable files are on there website:
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

Under step three (which is where we find ourselves) it says to simply go to the directory and run this command:

/opt/lampp/lampp start

When I try to do this I get the following:

james@james-linux:~/Applications/XAMPP/opt/lampp$ lampp start
bash: lampp: command not found

I am a bit confused, but was wondering if maybe it is because it is installed into my 'home' directory, or maybe it is because Ubuntu wouldn't let me use root in the command line.  

I hope I explained this well enough and I would be happy to clarify anything for you. I would definitely appreciate your help.  Thanks guys and gals!

---

### Post by jcathcart on 2009-03-23
Update:


I tried using ./ infront of the command and got this error:

james@james-linux:~/Applications/XAMPP/opt/lampp$ ./lampp start
You need to start XAMPP as root!


How do I become root or get root privelidges in the command line?

---

### Post by thehouseofho on 2009-03-23
> **jcathcart said:**
> Update:


I tried using ./ infront of the command and got this error:

james@james-linux:~/Applications/XAMPP/opt/lampp$ ./lampp start
You need to start XAMPP as root!


How do I become root or get root privelidges in the command line?

In terminal, just type sudo *command* to run as root.  However, if the command you're running will launch a graphical application, you should type gksudo *command*.

---

### Post by jcathcart on 2009-03-23
Thanks!  Really appreciate the help.  I am one step further, but its still giving me trouble.  At least the command is running.  If I can't figure it out I'll be back.

Thanks again!

---

### Post by jcathcart on 2009-03-23
Yay! IT WORKS I LOVE YOU.... sorry just excited

---

### Post by Cheesemill on 2009-03-23
Instead of using XAMPP you could always use the LAMP stack included in the Ubuntu repositories, just do the following to install:

```
sudo apt-get update && sudo apt-get -y install lamp-server^
```

This will install Apache, MySQL, and PHP on your machine and automatically start them all at boot time. Using this method all of the required packages will be updated with the rest of the system when you do an apt-get upgrade instead of you having to update XAMPP manually.

Cheesemill

---

### Post by trump1 on 2009-03-23
> **Cheesemill said:**
> Instead of using XAMPP you could always use the LAMP stack included in the Ubuntu repositories, just do the following to install:

```
sudo apt-get update && sudo apt-get -y install lamp-server^
```

This will install Apache, MySQL, and PHP on your machine and automatically start them all at boot time. Using this method all of the required packages will be updated with the rest of the system when you do an apt-get upgrade instead of you having to update XAMPP manually.

Cheesemill

I searching for solution about lampp problem and i saw this threat, i try to install the lamp stack now i can't remove it from my sistem :(
Can you give me the command please **Cheesemill**  ???

---

### Post by Cheesemill on 2009-03-24
trump1, just do a

```
sudo apt-get remove lamp-server^
```

Cheesemill

---

