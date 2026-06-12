---
title: "[SOLVED] PHP - Hello World"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by WASHAD on 2008-12-29
Now that I've nearly completely made the switch to Ubuntu, I'm naturally interested in learning PHP.

I think that I have Apache, mysql, phpadmin, etc.. installed - but I still can't seem to get a simple hello world. 

I've changed the index.html in var/www/index.html to read the following code, but I still don't get a hello world :(. I do get "It works!", though. 

If it helps to know, I've done a bit of programming (C++, assembly, C#, ASP.Net), but never PHP. 

```
<html>

<body>

<h1>It works!</h1>

<?php
	echo "Hello World";
?>

</body>

</html>
```

---

### Post by blueridgedog on 2008-12-29
Any hint if you tail the apache log?

What is in the source if you view source once you view the page?

---

### Post by TomasJancik on 2008-12-29
you talk about index.html, but if the page contains php code, it must have .php extension

---

### Post by linux_tech on 2008-12-29
How about
```

<?php print "Hello World!";
?>

or

<?php
echo "Hello World!";
?>


```

---

### Post by WASHAD on 2008-12-29
Good point, let me try that :)

---

### Post by WASHAD on 2008-12-29
> **blueridgedog said:**
> Any hint if you tail the apache log?


I'm really swimming in the shallow end here, can you translate?

I didn't do anything to Apache, just installed it. 

Stevej

---

### Post by WASHAD on 2008-12-29
Thanks, I got the code right off the internet, though;

[http://www.w3schools.com/PHP/php_syntax.asp](http://www.w3schools.com/PHP/php_syntax.asp)

At any rate - I tried changing it. When I try to browse to the PHP file, Firefox gives me the choice to 'open with' or 'save file' -- I must not have something configured correctly. 

SteveJ

---

### Post by cubenz on 2008-12-29
Try creating a file called "phpinfo.php", and put the following in it:

> <?php
phpinfo();
?>

That's all - nothing else!

Then browse to the file, something like "http://localhost/phpinfo.php"

If Firefox offers to save it, Apache isn't configured with PHP, so you may need to delve in to your 'httpd.conf' file to see if .php files are configured to be pre-processed by the PHP module. 

Let us know what you find....

cubenz

---

### Post by WASHAD on 2008-12-29
Yeah, it still offers to save it. I'm not certain how to edit the apache config files though. 

SteveJ

---

### Post by edd07 on 2008-12-29
> **WASHAD said:**
> Yeah, it still offers to save it. I'm not certain how to edit the apache config files though. 

SteveJ
I think PHP is available in Synaptic, look for it there. You said you installed phpAdmin, but they're not the same thing. PhpAdmin is for managing MySQL databases from the web, and it requires PHP.

I went through all this while configuring Apache on my laptop, but I can't remember every detail, I'm afraid. But after I installed the right packages, PHP pretty much configured itself.

Hope this helps

---

### Post by ibuclaw on 2008-12-29
To get your localhost up and running, install the lamp-server packages.

Open up a terminal and type in:
```
aptitude
```
Scroll down to **Tasks**, press Enter
-> **Unrecognised Tasks**, press Enter
-> -> **lamp-server**, press **+**

Then press **g** a few times to confirm the selection (enter your password), then **g** again to begin the installation.

Once it has finished, press **q** to quit aptitude, and type in the following into a web browser:
```
http://localhost
```
In your browser, and you should get a page saying:
```
**It works!**
```

Next, to setup PHP, run the following:
```
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```
Now, for anything else you wish to test, just drag and drop all files you write into the **/var/www** folder, then type in their names into the firefox web browser:
```
http://localhost/hello.php
```

Though, since you'll probably be wanting to keep your web server private to only you, I recommend that you setup your firewall:
```
sudo ufw default deny
sudo ufw enable

```
And all incoming connections without the ACK bit turned on will be denied (So you can connect to the outside world, but they can't freely connect to you without your permission first).

For an easy to setup GUI frontend for ufw, [check out gufw]("http://gufw.tuxfamily.org/index.html").

Regards
Iain

---

### Post by WASHAD on 2008-12-29
I thought I had installed PHP5, but it looks like I missed it. I just installed PHP5 and PHP5-cli (shotgunning a bit). I still seem to have the same problem, though. 

Thanks, 

SteveJ

---

### Post by jpmelos on 2008-12-29
Quick checklist for you, all right?

1) Have you checked if your file is **.php** extension??

2) Is your file located at the folder your Apache uses as root for the web browsing, or in a sub-folder of it? (I mean, the folder it seeks when you type on your browser **[http://localhost/](http://localhost/)**.)

3) Are you making sure you are **NOT** trying to access it through **File > Open File...** option, or putting it's hard drive address into the browser? You are supposed to access it through **http://localhost/<folder of the file>**, otherwise the PHP processor won't do a thing.

4) Is your Apache with the PHP5 Module activated? You can find aewsome guides in Google typing things like "**install lamp ubuntu intrepid**". I'd suggest you completely uninstall all applications for Apache and Apache itself and follow one of those guides if you are in doubt if anything you already did might be breaking it.

The "Hello World" code of yours should work if your Apache is all set. I hope it helps you. :D

---

### Post by WASHAD on 2008-12-29
> Then press g a few times to confirm the selection (enter your password), then g again to begin the installation.

It says that I have no software packages waiting to install. 



> In your browser, and you should get a page saying:
Code:

It works!

I get that. 



> Next, to setup PHP, run the following:
Code:

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

Yep;



N> ow, for anything else you wish to test, just drag and drop all files you write into the /var/www folder, then type in their names into the firefox web browser:
Code:

[http://localhost/hello.php](http://localhost/hello.php)

This part doesn't work. Says the file doesn't exist. My file is test.php. It is in /var/www

---

### Post by WASHAD on 2008-12-29
> It says that I have no software packages waiting to install.

OK, went back and got the lamp-server to install. 

Now, when I type [http://localhost](http://localhost), I get the file not found error? I verified that index.html is still in var/www, and it does work when I go there via FireFox. 

Thanks, 

SteveJ

---

### Post by WASHAD on 2008-12-29
Heh, what do you know! When I browse to test.php in Firefox, I get my PHP page. It works!

I just wrote my first PHP code in Ubuntu! I'm as giddy as a school girl! Thanks Iain !!!

SteveJ

---

### Post by ibuclaw on 2008-12-29
Try stopping and restarting the apache service:
```

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

```

Have you done anything else that I have not mentioned when you tried to setup the web server ?

Also, you are typing in **[http://localhost/test.php](http://localhost/test.php)** , right ?

[EDIT]
Ah, ok... as long as it is all good, and working fine :)
Enjoy your PHP/SQL experience...

Here's my Hello World:
```

<html>

<body>

<h1>It works!</h1>

<?php
$name = $_GET['x'];
    if(isset($name)) {
        echo "Hello $name";
    }
    else {
        echo "Hello World";
    }
?>

</body>

</html>

```
Now type in : **[http://localhost/test.php?x=SteveJ](http://localhost/test.php?x=SteveJ)** and say hello to input arguments :)

Regards
Iain

---

