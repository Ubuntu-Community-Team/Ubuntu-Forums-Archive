---
title: "BLUEFISH editor"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by fluteofliar on 2010-07-08
HI,ALL OF OF YOU

I were trying to run my php script on bluefish
Initally i wasted a heap of my time because "view in browser "button aint working.
Now my problem is ,whenever i create a php file and press the "view in browser button" its jump to address(for file name hi) 
file:///var/www/hi.php
and dispalying a dialogue box to ask wheather to open a file or save it?.i am just sick even after utilizing so much time(though html file with the same name and address format running fine)..plz help me sir

---

### Post by bodhi.zazen on 2010-07-08
First, please use the default font. If you are having problems reading, adjust your browser.

Personally I open the file directly with my browser.

A simple search yielded this thread :

[http://ubuntuforums.org/showthread.php?t=485246](http://ubuntuforums.org/showthread.php?t=485246)

---

### Post by cariboo on 2010-07-08
Have you got libapache2-mod-php5 installed, as not having that module installed causes the problem you are describing. Libapache2-mod-php5 is in the repositories.

---

### Post by darolu on 2010-07-08
This issue has been solved in Bluefish 2.0, I strongly suggest you to install it: [http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.2_.28current_stable.29](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.2_.28current_stable.29)

The sources lines say "jaunty" leave it that way, it will work just fine in Lucid.

---

### Post by fluteofliar on 2010-07-08
@bodhi.zazen
Sir,i will take care of this
@cariboo907
yeah,have checked no problem
@darolu
getting same problem even with bluefish2.0

---

### Post by fluteofliar on 2010-07-08
@cariboo907
there aint any error related with any package since when i am typing on address bar "http://localhost/hi.php"
the php script running fine,hope this ll help you to resolve my problem:)
and the entry for firefox in preference is given as
firefox -remote 'openURL(%p)' || firefox '%p'&
considered i am saving my php file as /var/www/x.php

---

### Post by bodhi.zazen on 2010-07-08
> **fluteofliar said:**
> @bodhi.zazen
Sir,i will take care of this

Thank you very much. Those who are visually impaired thank you.

---

### Post by fluteofliar on 2010-07-08
> Originally Posted by [B]bodhi.zazen 
[/B]Thank you very much. Those who are visually impaired thank you.now,i am also a part of this community...if i wouldn,t be able to do something good
then ll surely try best to maintain consistency of this great comm

---

### Post by darolu on 2010-07-09
> **fluteofliar said:**
> considered i am saving my php file as /var/www/x.php
It may be a permissions issue, check that all permissions are right.

What I usually do is create a virtualhost with a directory within my /home/<user> so I don't have to be checking/changing permissions constantly at /var/www; the files you may want to check/edit to do this are at /etc/apache2/sites-available/ and /etc/apache2/sites-enabled/

Examples: [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

---

### Post by fluteofliar on 2010-07-09
@darolu
i am beginner,i am not getting the content related to virtual host
though i checked /etc/apache2/sites-available and found a folder name default
i dnt knw wht to do with it
now i am really feeling why linux can never replace window:(

---

### Post by fluteofliar on 2010-07-09
i found one implememtation in other thread as
> 3. This is the best method. Create a new Virtual Host.
Open /etc/apache2/sites-available/default using the Alt+f2 method. At  the last add

 	Quote:
 	 	 		 			 				[SIZE=2]<VirtualHost *:80>
    DocumentRoot /home/manish/www/
    ServerName altserver
</VirtualHost> 			 		[/SIZE] 	 	 
Now open /etc/hosts using the same Alt+F2 method  and add the line
 	Code:
 	127.0.0.1 altserver 
Now restart the server using 
 	Code:
 	sudo /etc/init.d/apache2 restart 
You may get some errors, ignore them
Now open altserver in browser and its voila. Done! Put your code in  /home/manish/www directory.


but still the problem persist while running on browser by typing address as(for file hi)
altserver/hi.php its running fine but when i am running this file by pressing view in browser button of bluefish ,browser getting address as /home/user/hi.php and asking me wheather to open a file or save it?

---

### Post by fluteofliar on 2010-07-09
now i use netbeans ,its running fine no problem
actually when i am trying netbeans there is option of project url....
which direct the project to url /localhost/x.php
is there any project option in bluefish....??plz reply if you know

---

### Post by fluteofliar on 2010-07-09
plz help.i want to be confort with linux but.ubuntu just frustrating me please..,well i tried one more thing
with this name in external command
firefox -new-window `echo "http://localhost/%n" | sed s/"home\/tarun\/www\/"/""/`
i am able to open php file save in /home/tarun/www/ but i aint able to open a file
contain in directry of above folder
for instance a file name please.php in, /home/tarun/www/helpme/please.php

---

### Post by darolu on 2010-07-09
> getting address as /home/user/hi.php and asking me wheather to open a file or save it?
PHP won't compile your code if you open that address in your browser as it's not being loaded from your web-server but as a file, you should open with an URL like "http://localhost/hi.php"
> @darolu
i am beginner,i am not getting the content related to virtual host
though i checked /etc/apache2/sites-available and found a folder name default
i dnt knw wht to do with it
Well, configuring a web server is not precisely for the beginner, although is not that hard, it is not as trivial as other tasks a "beginner" would do. Anyways the "default" directory (folder) is not an actual directory but a file with the default virtualhost information, uhmmm changing the "/var/www" for your web-files directory should do the trick for you to run your php files, read the documentation in the link I gave you in my other post, you'll learn a lot from there, here is the link for all apache docs: [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

> now i am really feeling why linux can never replace window
lol good luck configuring a windows-web-server :p

---

### Post by fluteofliar on 2010-07-10
@darolu
you should have seen the current status of user before taking pain to pen your thought

---

### Post by fluteofliar on 2010-07-10
can,t you see what did i wrote in my last post,i have created virtual host
> plz help.i want to be confort with linux but.ubuntu just frustrating me  please..,well i tried one more thing
with this name in external command
firefox -new-window `echo "http://localhost/%n" | sed  s/"home\/tarun\/www\/"/""/`
i am able to open php file save in /home/tarun/www/ but i aint able to  open a file
contain in directry of above folder
for instance a file name please.php in,  /home/tarun/www/helpme/please.phpdo you have any idea to edit this "firefox -new-window `echo "http://localhost/%n" | sed  s/"home\/tarun\/www\/"/""/"so that even php file with in the folder also run?
if you know tell me but stop your spritiual speech

---

### Post by fluteofliar on 2010-07-10
well problem solve...thankz for everything

---

