---
title: "How do I create my own website?!! Help!"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by jrozo17 on 2010-04-18
Ok so I'm just a teenager (and havent really had a job), but this one dude found out I'm computer savvy and asked if I want to design him a website. I said sure. I havent exactly found out what he wants it for, but all I know is that I needa find out how to do it fast. 

So can anyone guide me through this? Are there any EASY programs out there for Ubuntu Linux to design a webpage? It has to be free.

Please, someone take the time to help me because I honestly need the money :(

Thanks,
J

---

### Post by sandyd on 2010-04-18
> **jrozo17 said:**
> Ok so I'm just a teenager (and havent really had a job), but this one dude found out I'm computer savvy and asked if I want to design him a website. I said sure. I havent exactly found out what he wants it for, but all I know is that I needa find out how to do it fast. 

So can anyone guide me through this? Are there any EASY programs out there for Ubuntu Linux to design a webpage? It has to be free.

Please, someone take the time to help me because I honestly need the money :(

Thanks,
J
```

sudo apt-get install apache2 mysql-server php5 phpmyadmin

```
download wordpress from [http://wordpress.org](http://wordpress.org)
```

gksudo file-roller

```
navigate over to the place where you downloaded wordpress and open the wordpress zip.
extract the contents of the wordpress folder (in the zip) into /var/www
```

sudo /etc/init.d/apache2 restart

```
go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

login using the username "root" and the password you set while setting up mysql.

create a new database.

go to [http://localhost](http://localhost)
type in the root username and the password.
type in the database name.
done.

be sure to create a new user (instead of root) and assign it to the database as this method is not secure at all, but is fast and easy.

---

### Post by NightwishFan on 2010-04-18
I used to use Screem to edit HTML (which is what you are asking I think?). I can not find it in the repos anymore. Try Quanta, it is KDE but I hear good things. You can also use Gedit its preinstalled.

---

### Post by lisati on 2010-04-18
For my own [web site]("http://lisati.myftp.org"), which I host myself on a machine running Ubuntu server edition, I "cheated" and used a Windows program "Web Plus" for most of the site. A free version is available [here]("http://www.freeserifsoftware.com/software/webplus/").

---

### Post by the-penguin on 2010-04-18
lucky for you i just started too look into this subject too.
i suggest you use kompozer to make your html websites 
```
sudo apt-get install kompozer
```

---

### Post by the-penguin on 2010-04-18
sorry for my brief comments, laptop's battery is almost empty :S

---

### Post by jrozo17 on 2010-04-18
> **carlee said:**
> ```

sudo apt-get install apache2 mysql-server php5 phpmyadmin

```download wordpress from [http://wordpress.org](http://wordpress.org)
```

gksudo file-roller

```navigate over to the place where you downloaded wordpress and open the wordpress zip.
extract the contents of the wordpress folder (in the zip) into /var/www
```

sudo /etc/init.d/apache2 restart

```go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

login using the username "root" and the password you set while setting up mysql.

create a new database.

go to [http://localhost](http://localhost)
type in the root username and the password.
type in the database name.
done.

be sure to create a new user (instead of root) and assign it to the database as this method is not secure at all, but is fast and easy.

Thanks carlee :) only thing is that when i go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), it gives me the 404 not found message... i cant get past this part, please help?:)

---

### Post by Paqman on 2010-04-18
> **jrozo17 said:**
> Thanks carlee :) only thing is that when i go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), it gives me the 404 not found message... i cant get past this part, please help?:)

You don't really need a server to learn how to build sites unless you need to use a server-side language like PHP. If you do want to set up a testing server the easiest thing to do is probably to install Virtualbox and just drop a ready-made server from Turnkey Linux into it.

Do you actually know HTML/CSS? Because if you don't then your first job is to buy a book on it and start learning.

---

### Post by sandyd on 2010-04-18
> **jrozo17 said:**
> Thanks carlee :) only thing is that when i go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), it gives me the 404 not found message... i cant get past this part, please help?:)
oops
forgot to give you instructions on that part.
```

sudo dpkg-reconfigure phpmyadmin

```
when you reach the section about choosing web servers (choose no at the first creen) choose apache2. Do this by highlighting apache2 (with your up/down keys on your keyboard) and pressing spacebar. Then press enter, and type in your passwords.

---

### Post by TriBlox6432 on 2010-04-18
Just tell the guy you need money to set up hosting, head over to Arvixe.com and do it the easy way  :guitar:

---

### Post by jrozo17 on 2010-04-18
> **carlee said:**
> oops
forgot to give you instructions on that part.
```

sudo dpkg-reconfigure phpmyadmin

```when you reach the section about choosing web servers (choose no at the first creen) choose apache2. Do this by highlighting apache2 (with your up/down keys on your keyboard) and pressing spacebar. Then press enter, and type in your passwords.

Ok I think I finally nailed everything down :)
The only thing is that i have no idea where to go from here... Like how do I insert a heading, links, posts, pictures, etc to the website? Im a noob :confused:

---

### Post by NightwishFan on 2010-04-18
You can use a WYSIWYG editor such as OpenOffice.org or Quanta. I know there are Windows ones (Dreamweaver?) but I have never used them.

If you really want to learn you will have to purchase a book or guide on HTML. I learned in school so I know no online resources.
[http://en.wikipedia.org/wiki/Html](http://en.wikipedia.org/wiki/Html)

---

### Post by Paqman on 2010-04-18
> **jrozo17 said:**
> Like how do I insert a heading, links, posts, pictures, etc to the website? Im a noob :confused:

Web pages are laid out by a simple language called HTML (Hypertext Markup Language). You can see the HTML code of any page by going to View > Page Source in your browser. These days the HTML defines the content, while page layout and presentation (things like fonts, colours, positioning, etc) are defined by CSS (Cascading Stylesheets)

You'll need to learn HTML/CSS to create sites.

Complex dynamic sites use databases and server-side scripting languages like PHP, but you don't need to worry about that until you've got HTML/CSS licked.

As well as the technical side of learning HTML/CSS, you'll also need to learn how to write effective copy (i'd advise this even if you're desinging for someone else's copy), how search engines work, and how to use images and colour effectively.

Don't worry if this sounds daunting, there's lots of help available. Start inspecting other people's code, and feel free to copy little snippets of code you like. [A List Apart]("http://www.alistapart.com/") has tons of great little tips for CSS layout. I'd recommend the book [Integrated HTML and CSS]("http://www.amazon.com/Integrated-HTML-CSS-Smarter-Faster/dp/0782143784") as a good, fast way to learn both at once.

---

### Post by sandyd on 2010-04-18
> **jrozo17 said:**
> Ok I think I finally nailed everything down :)
The only thing is that i have no idea where to go from here... Like how do I insert a heading, links, posts, pictures, etc to the website? Im a noob :confused:

so youve gotten wordpress setup right? if you have, go to [http://localhost/wp-admin](http://localhost/wp-admin) and login. All the stuff is self explanatory after that. if you havent, go back to my first post in the thread

---

### Post by Zintha on 2010-04-19
You told someone you'd write them a website with no idea what programs to use or how to write one?

Sure you can ask about programs here, but you're best off learning HTML from a site dedicated to that.

Lissa explains is what I grew up (HTML wise) on for the longest time, girly and childish but its laid out really easily and won't go over a beginners head.

---

### Post by Dutch70 on 2011-03-22
Well, as you can see you have many options. 

My opinion... +1 on KompoZer & you can find a tutorial [*[COLOR="Blue"]Here[/COLOR]*]("http://www.thesitewizard.com/gettingstarted/kompozer-tutorial-1.shtml")

---

