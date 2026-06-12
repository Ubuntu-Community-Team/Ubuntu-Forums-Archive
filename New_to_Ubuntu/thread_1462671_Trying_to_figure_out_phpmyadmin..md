---
title: "Trying to figure out phpmyadmin."
date: 2010-04-26
forum: New to Ubuntu
---

### Post by errand on 2010-04-26
I am trying to see phpMyAdmin through localhost and can't really see anything. It comes blind page out.
What I did was change permission for /var/www to write all, made a link to phpmyadmin folder in /etc directory and ....nothing not even a thing.
I do not remember how but I brought out log in screen once.](*,)

---

### Post by vivek40 on 2010-04-26
Hi errand!.. 
1.Instead of changing permissions to var/www .. it would be good if you could create a symlink (i.e your var/www folder will link to say home/myweb folder).. Now whatever you put in your myweb folder will automaticaly be detected by the var/www folder. I have seen this to be much easier.

2. Instead of installing phpmyadmin from synaptic.. you can download phpmyadmin from their site and unzip and place it in your myweb folder.. then whenever you call "localhost/www/phpmyadmin".. everything will happen automatically...

I have found this method much easier than any other methods described anywhere.. the same goes with drupal, joomla etc.. just download the packages and put it in your myweb folder and access it from your browser for going ahead.. however please note that you call the site in the browser using "localhost/www/phpmyadmin" and **not**"localhost/myweb/phpmyadmin"...
I am presuming you know how to create a symlink and all.. However if you want further info please post back

---

### Post by wmatthews on 2010-04-26
The best and easiest thing to do is download it from [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php).  I tried to install it from apt-get and nothing went right.

---

### Post by _0R10N on 2010-04-26
I always install phpMyAdmin using apt-get, or aptitude. Remember that you'll need to download php5, apache and of course, MySQL Server 5...

If you try this with no success, let me know, I may be forgetting something.

Kind regards!

_0R10N >>

---

### Post by Kellemora on 2010-04-26
Question for Vivek40

I recently started studying PHP and JavaScript.

It required a LOT of help from the folks here for me to even learn WHERE to put the php file.  My tutorials said nothing about /var/www as the location.

However, I prefer to keep all web documents (html, css, js, php, etc.) in my /home folder on a separate partition.  

I don't especially like having to sudo gedit to work on these files either.

I would like to know how to make a symlink that WORKS.  I've tried myself and failed.  And does it have to be in /home/kellemora/webpages or can it just be in /home/webpages/html/ (for html and css) or /home/webpages/php/ (for php, javascript and js)?

And one last thing.  I can access the web pages I'm working on using [http://localhost/nameoffile.php](http://localhost/nameoffile.php) from the working computer, or by using [http://192.168.1.xxx/nameoffile.php](http://192.168.1.xxx/nameoffile.php) from other computers on the LAN.

I have not yet figured out how to assign a static IP (in house only) to Apache2.  Using the NAME of the computer does not work either.
I'm JUST LEARNING PHP and merely installed LAMP in order to see my lesson pages, default setup, which might be a security risk since I'm on a LAN open to the Internet?

Thanks

TTUL
Gary

---

### Post by _0R10N on 2010-04-26
Hi Kellemora, I know that this question isn't for me, but I'd worded with PHP and MySQL for sometime, and I still do if I have to.

Apache is configured to "listen", or better said "serve" pages located in given locations. By default this location is
```
/var/www
```
You can change that, changing a simple line. Take a look to the /etc/apache2/sites-available/default file. You should change
```

 DocumentRoot /var/www

for

 DocumentRoot /home/user/sites


```

I hope this helps!

_0R10N >>

---

### Post by Kellemora on 2010-04-26
Hi Or1on

Thanks, I will give that a try.

Curious, would the files STILL have to be owned by root for Apache to use them?  

TTUL
Gary

---

### Post by vivek40 on 2010-04-26
Hii Kellemora, saw your message just now.. Personally speaking I would not do any modifications to apache, and in most of the cases I would not want to change any permission settings anywhere.
As posted by _OR1ON:
> Apache is configured to "listen", or better said "serve" pages located in given locations. By default this location is
 	Code:
 	/var/www 
 
You can get some info on the symlink thing here **[http://tinyurl.com/2u57rz7](http://tinyurl.com/2u57rz7) **.... However please note that the author there has suggested removing the www folder . I seriously dont know how apaache would behave if you deleted that folder.. Instead you could just make another folder named say "website" in "var/www" (such that it looked like var/www/website) and then create another folder"mywebsite" in "home/vivek"(such that it looked like /home/vivek/mywebsite).. and then create a symlink between "website" and "mywebsite" using "sudo ln -s /home/vivek/mywebsite /var/www/website".. so now whatever I drop in"mywebsite" will be recognized by apache.. for eg: if I put a file"RockOn.php" in "mywebsite"(/home/user/mywebsite/RockOn.php).. it can be accessed via (localhost/websit/RockOn.php)...Please note that there is no need of creating a website in var/www, it only lengthens the url.. If you just link var/www to /home/user/mywebsite.. further access will be much easier.
bye!

---

### Post by Kellemora on 2010-04-26
Thanks guys!

Sorry it took so long to get back!
Was working on a CSS problem that worked fine on one page, but not on another for some reason that I finally figured out after 4 hours of pulling my hair out.

I hope adding a link from just /var/www will not prevent things already in /var/www from being recognized by Apache.

I may have been using Ubuntu for a few years now, but I rarely get under the hood because it just flat out WORKS without doing so 99% of the time!

I'm thinking about creating a new USER named something like Webbie in the /home directory just for the website, so it doesn't show the actual /home/user name.  I figure as long as I give the right permissions, I could work on the web pages without using sudo to get to them and my backup will then save all the work off-site.

Again, thanks for all your wonderful help gang!

TTUL
Gary

---

### Post by errand on 2010-04-26
Thank you!!

I am really pleased that so many people answered. I took Vivek40's advise.
It is really easy to just link it and no worries any more.
May be one more small detail after the folder is linked to /var/www  permissions for access from others have to be changed to "Access files" otherwise Apache returns "403  Forbidden".
Now,  comes MySQL next....

Errand

---

### Post by vivek40 on 2010-04-27
Hii Kellemora:
> I hope adding a link from just /var/www will not prevent things already in /var/www from being recognized by Apache.

No it will not.. anything in var/www will be recognised properly by apache...

Bye

---

### Post by miyagison on 2010-04-27
> **errand said:**
> I am trying to see phpMyAdmin through localhost and can't really see anything. It comes blind page out.
What I did was change permission for /var/www to write all, made a link to phpmyadmin folder in /etc directory and ....nothing not even a thing.
I do not remember how but I brought out log in screen once.](*,)

Like the other guys in here are saying, the easiest way on using phpMyAdmin is to download it and untar it in a directory. Now, if your apache installation restricts the use of symlinks you either need to correct the permissions in the /etc/apache2/sites-enable and edit the configuration to allow the use of syminks. Another thing is to make sure that you have your php configuration setup with MySQL or MySQLi. Third - be sure that you have installed MySQL. On an Ubuntu machine the best way to get all of this working is to install MySQL first, Apache2 Second and php5 3rd and install these using apt-get from the command line.

---

### Post by Kellemora on 2010-04-27
I guess I lucked out again!
I just installed Apache2 MySql and PHP from Synaptic and the default setting, whatever and wherever they are, works perfect for my present needs.

The ONE symlink Vivek40 suggested works PERFECTLY!
Took me a while to figure out I had to go to Root Terminal, then to /var/www and perform the link from there to /home/webbie/
Now all the folders in /home/webbie are recognized by Apache!

I'm using three sub-folders, one is named /html-css and the other /php-js for my experiments and lessons and a final one for my completed work named /website  

That's what I love about Ubuntu, it just WORKS, once you figure out HOW to do something!

And for those of you reading this, I ran across a little trick, solely by accident that can save HOURS of work in finding an error.

At the top of your html page where you have the DOCTYPE statement.
Highlight these two lines OUT....
And your page will be filled with RED BLOCKS......
The first red block is usually where the error is!
Fix it and the rest all go away.

I'm sure using a generator would stop errors, however, I want to hand code my pages this time as a learning experience.  And a learning experience it is turning into also!  Especially when the Lesson works and your nearly identical code does not.  But that's how we learn, by making changes to things and seeing what happens.
Different tutorials teach different ways and often they can't be interchanged and achieve the same results.

The only drawback to css is you can't VIEW other web sites to see HOW they did that, as you have no idea WHAT they did in that css file you don't see.

Again, thanks all!

TTUL
Gary

---

