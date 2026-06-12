---
title: "PHP5 problems"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by scristopher on 2010-01-27
Hi, I am trying to learn PHP, ive been having alot of problems and have been trying to find an answer but i cant find anything so far. this is very very basic, ive copied and pasted the first test out of a php ebook and cannot make it work no matter what i do. ive been looking around and cant seem to find an answer to this. here is the code:

<html>
<head>
<title>PHP Test</title>
</head>
<body>
<p>This is an HTML line
<p>
<?php
   echo &#8220;This is a PHP line&#8221;;
   phpinfo();
?>
</body></html>

ive tried a few variations of it as well: 
 <?php echo "<p>Hello World"; ?>

everytime i goto check the url i get this:

Parse error: syntax error, unexpected '>' in  /var/www/domainname/php/phpfile.php on line 1
either .html or .php neither works
this does work though which make me scratch my head:
 <?php phpinfo(); ?>

i wasnt quite sure why the code would not work as i copied out of an few different sources. i checked my apache error.log and see this

HP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/imap.so' - /usr/lib/php5/20060613+lfs/imap.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Wed Jan 27 19:53:27 2010] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.4 with Suhosin-Patch mod_ssl/2.2.12 OpenSSL/0.9.8g configured -- resuming normal operations

not sure if its related or not but im trying to fix thoes as of now as well. Like i said im trying to learn PHP and i may be missing something very very simple as i do not know the language yet.
if anyone can help me i would greatly appreciate it im going to keep googleing

---

### Post by phillw on 2010-01-27
Hi and welcome to the Forums,

can you post the output of

```
 cat /etc/apache2/sites-enabled/000-default | grep www 
```

If you're not familar with the console / Terminal / CLI , to get it  Click on Applications --> Accesrories --> Terminal   You'll get a window come up with a black background and a line that ends in a **$** sign, that is where you type the command in.

Thanks,

Phill.

---

### Post by scristopher on 2010-01-27
scott@mordred:/etc/apt$  cat /etc/apache2/sites-enabled/000-default | grep www
	DocumentRoot /var/www
	<Directory /var/www/>

Also ive found that post ive tried checking for 
php5-ldap is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
and the same for php-common
im checking the versions of php-common now to see what version i have

---

### Post by utnubuuser on 2010-01-27
php info is ususally

<?php
infophp();
?>
saved as info.php

and <p> shouldn't be in the second statement at all.

---

### Post by phillw on 2010-01-27
> **scristopher said:**
> here is the output-
scott@mordred:/etc/apt$ cat /etc/apache2/sites-enabled/000-default | grep www    DocumentRoot /var/www
    <Directory /var/www/>

Also ive found that post ive tried checking for 
php5-ldap is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
and the same for php-common
im checking the versions of php-common now to see what version i have

Is okay ...

Any scripts you write and save are to be saved in the directory **/var/www** that is where your **[http://localhost](http://localhost)** is looking

```
 cd /var/www
gksudo gedit here.html

```

It will ask for your password, then open a window - Into that window put this ..

```
<html><body><h1>It works!  Hello Christopher !!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>

```

Then save and exit.

From your browser type in ```
http://localhost/here.html
```

And let me know what it says ..

Regards,

Phill.

---

### Post by scristopher on 2010-01-27
Ive tried a few other statements as well with <?php echo "<p>Hello World"; ?> just does not seem to work for me the <?php phpinfo(); ?> does work though

---

### Post by scristopher on 2010-01-27
yes that works, i dont seem to be having a preoble with any of my domains just php is it possible that i have a component missing or something unconfigured in apache?

---

### Post by phillw on 2010-01-27
> **scristopher said:**
> yes that works, i dont seem to be having a preoble with any of my domains just php is it possible that i have a component missing or something unconfigured in apache?


Yes, what works ?

Phill.

---

### Post by scristopher on 2010-01-27
i get to here.html sorry for being vague about that

---

### Post by phillw on 2010-01-27
> **scristopher said:**
> i get to here.html sorry for being vague about that

Do you have MSN / AIM (AOL) / Yahoo chat ?

When you type in [http://localhost/here.html](http://localhost/here.html) into your browser it will give you a screen saying something - can you tell me what it says.

regards,

Phill.

---

### Post by scristopher on 2010-01-27
it gotes to-
<html><body><h1>It works!  Hello Christopher !!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html> 
{withouth the html coding}
I also sent u a PM

---

### Post by phillw on 2010-01-27
>  {withouth the html coding} 	

I'm still unsure what you mean.. Do you see it on the screen as 

> <html><body><h1>It works!  Hello Christopher  !!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been  added, yet.</p>
</body></html> 


Or as something different ?

Phill.

---

### Post by scristopher on 2010-01-27
sorry im really not good at explaining things sometimes
[IMG]http://scottfertig.net/source.png[/IMG]

---

### Post by phillw on 2010-01-27
Kewl !!! - It works !!

Right ....

very, very quick lesson ...

html code ends in whatever.html, such as that example

php code ends in whatever.php

So,

<?php
phpinfo();
?>

is saved with a .php at then end.

If you want to have php WITHIN html, then you can either use <?php ....... ?> on one line or, you can simply wrap it in php tags ...

So...

php.html  would be ..

> <html><body>
<h1>about to start php</h1>
<?php
echo 'at start of php';
phpinfo();
echo 'at end of php';
?>
<h1>end of php</h1>
</body></html> 
Do you understand that ?

Phill.

---

### Post by scristopher on 2010-01-27
yes my pages are named with .php and start correctly i am still getting erros when i rename them to a .html file i do see the text in the file but the php functions dont work and are nonexistant when they are .php files i get syntax errors, i am correctly starting and ending the documents with <?php and ?> as well. i tred running the code you posed within html both as a .html file and a .php file (though i knew the php file would do nothing just for laughs :) ) and got nothing really {edit} i changed infophp to phpinfo and that worked as in the other example i had that worked
[IMG]http://scottfertig.net/mordred.png[/IMG]

---

### Post by phillw on 2010-01-27
Don't despair ... it is still new enough for me to remember my 'pulling out the hair' bit !!

I've just been going through my archived stuff.... this is a good place to start .... As done by myself - lol

[http://www.elated.com/articles/first-php-script/](http://www.elated.com/articles/first-php-script/)

and the real one, from the people of php ...

[http://uk3.php.net/tut.php](http://uk3.php.net/tut.php)

you have my AIM name, you're welcome to IM me and i can point you to some other stuff i still have.

Regards,

Phill.

---

### Post by phillw on 2010-01-27
You know, i thought that was wrong when i typed it ...

it should be ....

**[COLOR=#000000][COLOR=#0000bb]phpinfo[/COLOR][COLOR=#007700]();[/COLOR][/COLOR]**

Soz,  :-(

Phill.

/edit - i've corrected it - but you can see that it echo'd the 1st php line, then errorred out - which tells you the error was on the next line

---

### Post by phillw on 2010-01-27
As way of an apology ... go and get Bluefish as the editor to use for your html and php coding. There are others, but I really like it as it is intelligent enough to pick out php code and colour it one way, when it is mixed with html code, and colour that a different way and can even handle MySQL code and colour that differently ... it's a nice editor.

It even 'complains' when you miss out a semi-colon or single apostrophe at the and of a statement - believe you me ... you'll get to hate those little *&^$$£##'s  ;)

Regards,

Phill.

---

### Post by scristopher on 2010-01-28
Alright it seems ive halfway solved my problems, in messing around with the code given in the books i find that some of it works after adjusting some things and trying different charactors than the book i was using gave. This I'm assuming means that the books examples for php5 dont work with the version im running which is 5.2.10? If this is so what should i be looking at to learn php if i cant rely on a book thats not a year old plus a few other ebooks that dont seem to have the correct syntax?

---

### Post by lordawesome on 2010-01-28
This whole thread is a big lesson in PHP. The lesson is that no matter where you go to learn it, everyone is a complete retard. Starting out making sure that PHP is working correctly was a good idea. However, nobody seems to be able to produce code correctly. Considering this and the fact that 90% of the world is overpopulated with retards, I recommend stealing webpages and copying the code from them until you can learn to type it out yourself. Sure, you could get bluefish, but why not code the first couple webpages by hand so you know what the hell you are doing. Or, you can take apologies all day from some guy offering you open source software as an token of his gheyness. It would be different if he gave you something that actually had cash value. Until then HAIL SATAN!!!

:evil:  :evil:  :evil:  :evil:  :evil:  :evil:  :evil:  :evil:

---

### Post by scristopher on 2010-01-28
Ive noticed that every php tutorial starts with the basic hello world, it seems to me that all these tutorials are coded with now invalid syntax... example i googled- php hello world then i clicked on the first link on google the code shown is always <?php
Echo "Hello, World!"; ?> {with the exception of php.net website}
  which is wrong (apparently) it will work for me if i change the " to ' example- <?php echo 'hello world!'; ?> 

My question is this: Since ive been looking at php5 books and the syntax is semi invalid in them what books should i be looking at to correct code php by example. I want to be able to learn from the book by example, not try to learn and have to spend hours on one page because it is using (now) incorrect syntax.
btw i use a virety of programs to code, i like nano the best, its effecient and no extra garbage great to use over ssh, the only reason i would be using a program that points out bad syntax for me would when i am having problems with syntax which then i would use screem. Whats frustrating to me is from the begining of my post i was treated like a retard with no knolage people telling me how to get to the terminal and such.... checking my apache install etc when it was the code the whole time that was bad syntax because of a new php version. Well if anyone has any info on what i could use as a up-to-date php learning guide - something i can study and learn by example. Thanx

---

