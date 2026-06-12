---
title: "xampp installation redirecting to splash.php"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by dawemmy on 2010-04-11
NEW to Ubuntu, New to Xampp 
Brand new dual install of windows 7 and  ubuntu 9.1
Followed an installation guide ([http://ubuntuforums.org/archive/index.php/t-223410.html](http://ubuntuforums.org/archive/index.php/t-223410.html))

that installs by tarball then creates the xampp control panel entry via a gedit file in applications on desktop for a ubuntu 9.1 installation.

Before the menu file the xampp localhost page was fine but after adding this gedit file.  I get a persistent redirect to [http://localhost/xampp/slpah.php](http://localhost/xampp/slpah.php).

The control panel application **DOES** start/stop lampp but in firefox the localhost just parks on splash.php file.  I click on english but nothing happens. (nothing happens on the other language choices too)
Cleared cache, rebooted.  searched around google and apacheforum then finally broke down signed up for this forum to ask this question.
How do I get the localhost xampp running properly?

I just want to use xampp so that I can install joomla 1.5 and use on a localhost.
Can you suggest a good tutorial to install joomla running on xampp?

---

### Post by dawemmy on 2010-04-11
Really need help!!
Uninstalled xampp 1.7.3a, downloaded it again, installed again, same thing can't get past the splash page, 
( I do do all the security stuff)

downloaded a different version 1.7.2 installed that same result
this time I did not do a reboot but just stopped and restarted lampp
same thing stuck on the splash page
should I delete it??  change the index.php file??
many thanks if someone can throw something at me!!

---

### Post by JoeyF on 2010-04-15
Same thing here.

Glad it's not just my computer. I had a stressful time getting this far : P

---

### Post by s_ø on 2010-04-15
Look in apaches error.log
in terminal
```
 nano /var/log/apache2/error.log
``````

```
or use the gnome-system-log. **Alt+F2** then enter **gnome-system-log**

---

### Post by indytim on 2010-04-15
Post the contents of your index.php file.  Not sure what directory structure XAMP uses.  If you had used the conventional LAMP installation, the file would be in /var/www.

IndyTim

---

### Post by JoeyF on 2010-04-16
Here's my Index.php:
```
<?php
	if (!empty($_SERVER['HTTPS']) && ('on' == $_SERVER['HTTPS'])) {
		$uri = 'https://';
	} else {
		$uri = 'http://';
	}
	$uri .= $_SERVER['HTTP_HOST'];
	header('Location: '.$uri.'/xampp/');
	exit;
?>
Something is wrong with the XAMPP installation :-(
```

This was on a fresh install btw. And does it on both my Computers.

Thanks.

---

### Post by fenstrat on 2010-05-05
The redirect to splash.php relates to the fact that xampp can't write to the lang.tmp file where it stores your language selection - /opt/lampp/htdocs/xampp/lang.tmp

My issue was related to the fact that I'd changed the user:group that apache runs as and therefore it couldn't write to the file.

By default apache runs as the nobody user so try changing the ownership of lang.tmp to nobody.

---

### Post by Atallcostsky on 2010-05-13
> **fenstrat said:**
> The redirect to splash.php relates to the fact that xampp can't write to the lang.tmp file where it stores your language selection - /opt/lampp/htdocs/xampp/lang.tmp

My issue was related to the fact that I'd changed the user:group that apache runs as and therefore it couldn't write to the file.

By default apache runs as the nobody user so try changing the ownership of lang.tmp to nobody.

I had the same problem as the OP - I'm confirming that your solution worked for me, thanks a bunch.

---

### Post by laurentq45 on 2010-06-30
Hello Post
> **fenstrat said:**
> The redirect to splash.php relates to the fact that xampp can't write to the lang.tmp file where it stores your language selection - /opt/lampp/htdocs/xampp/lang.tmp.

I have a similar problem, purpose in my case, I did not file /opt/lampp/htdocs/xampp/lang.tmp !! :confused:

I edit /opt/lampp/htdocs/index.php :
[PHP]<?php
    if (!empty($_SERVER['HTTPS']) && ('on' == $_SERVER['HTTPS'])) {
        $uri = 'https://';
    } else {
        $uri = 'http://';
    }
    $uri .= $_SERVER['HTTP_HOST'];
    header('Location: '.$uri.'/xampp/');
    exit;
?>
Something is wrong with the XAMPP installation :-([/PHP]

Should I uninstall to re-install?

I run with Xamp-linux-1.7.3a

---

### Post by pankajsisodiya on 2010-09-29
Yes, the Solution worked for me as well. I was running with same problem & i just changed the ownership of /opt/lampp/htdocs/xampp/lang.tmp & it works. Thanks a lot

---

