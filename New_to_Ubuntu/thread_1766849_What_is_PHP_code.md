---
title: "What is PHP code??"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-24
What is it?

---

### Post by tgalati4 on 2011-05-24
Personal Home Page or Programmers Hate Programming, or one of several other acronymns.  It's a language that is used to serve up web pages.  Any webpage that has index.php as a home page is running PHP code.  Major web-building frameworks are written in PHP such as drupal ([http://drupal.org](http://drupal.org)) and business applications like sugarcrm ([http://sugarcrm.org](http://sugarcrm.org)).  It's easy to program and there is a lot of code out there to look at.  You can take an existing web application, modify it's PHP code and customize it--making a new web application.  

Learn what's happening in PHP at [http://php5.org](http://php5.org)

Oh, and what PHP really stands for:

[http://php5.org/intro-whatis.php](http://php5.org/intro-whatis.php)

---

### Post by decoherence on 2011-05-24
> **TAspr said:**
> What is it?

PHP is a scripting language like Python or Perl. The main feature that distinguishes PHP is that it is designed to be embedded in HTML source documents.

For instance, if you look at the source for a PHP page, you might see something like
```

<html>

<?php
print('hello world')
?>

</html>

```

which would be analogous to

```

<html>

hello world

</html>

```

Obviously people tend to use PHP for more useful things that straight HTML can't do on its own.

If you were to do this in python, it would be more like

```

print("""
<html>

hello world

</html>""")

```

the difference being that the HTML is embedded in the python, rather than the python being embedded in the HTML.

Two things to note: 

1. it IS possible to embed python or perl or anything else inside of HTML using server side includes... it's just that the PHP language was designed to do this from the get-go and so may be easier to work with in some cases.

2. if you go to a web page that ends with .php and view the source, you won't actually see any php. That's because it gets converted to straight HTML before it gets to your browser.

The most basic reason to use PHP is to put conditional statements in your web pages (If some condition is true then write so-and-so html. If it isn't true, write different html)

---

### Post by TAspr on 2011-05-25
Oh I see.   Well the reason I ask, is that it's referenced on this page.

[http://ubuntuforums.org/showthread.php?t=1766117&page=3](http://ubuntuforums.org/showthread.php?t=1766117&page=3)

---

### Post by Paqman on 2011-05-25
> **TAspr said:**
> Oh I see.   Well the reason I ask, is that it's referenced on this page.

[http://ubuntuforums.org/showthread.php?t=1766117&page=3](http://ubuntuforums.org/showthread.php?t=1766117&page=3)

Yeah, they just hit the wrong button on the text editor when they posted. That's not PHP.

---

### Post by alphacrucis2 on 2011-05-25
A point of interest is that the ubuntu forums is run by a php based system called vBulletin. You could install vBulletin on your own PC and set up your own forums. However VBulletin is not a free product, you have to buy it. There is however a free open source bulletin board software available called phpbb which is in the Ubuntu repos. It requires the apache2 web server, php interpreter and Mysql database (all are in the repos). If you are interested it's quite instructive going through the process of getting phpbb up and running.

---

