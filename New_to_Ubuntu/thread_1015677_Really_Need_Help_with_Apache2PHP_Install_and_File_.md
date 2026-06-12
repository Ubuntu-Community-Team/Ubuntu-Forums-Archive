---
title: "Really Need Help with Apache2/PHP Install and File Parsing"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Avenue on 2008-12-19
Hello Everyone,

I'm not sure if this thread belongs in this particular forum, but I thought i'd post here as a start. I would like to point out that I consider myself to be a Linux newbie even though i've been running the OS for a couple years now - I rarely, if ever, have had to get in and get my hands dirty simply because I run Ubuntu on a secondary machine. I read a few tutorials and did a search of this forum but nothing seems to work.  I'm frustrated to the point of being extremely irritated at how complicated this OS can be.

With that stated, here's my scenario:

_**PROBLEM 1**_

Yesterday I installed Apache2, MySQL and PHP 5. Apache is running and I was able to access a sample HTML page from /var/www via my localhost in a browser. However, for some odd reason I am NOT able to parse PHP files. Rather, instead I get the option to download the file whenever I attempt to display the page in my browser.

To troubleshoot and resolve the problem, I followed the instructions in a couple of books which did not help. Additionally, I went out and read some tutorials online which helped to clarify some things but yet still my PHP files would not parse. The tutorial I found most helpful is here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I do indeed have the ***libapache2-mod-php5*** file installed and it's configured properly after running the following:

```
sudo a2enmod php5
```

Followed by

```
sudo /etc/init.d/apache2 restart
```

I have cleared the cache in my browser and went to my localhost but my PHP files still do not parse.


**_PROBLEM 2_**

I have changed the location of where my sites will be accessed from /var/www to a new location in my Home folder - /home/username/Websites. I did so by doing the following:

1) copying the default file within the /etc/apache2/sites-available directory. I then saved the new file as Mysite.

2) Edited the Mysite file and changed the DocumentRoot to point to the /home/user/Websites. In addition, I also changed the Directory directive, replacing <Directory /var/www/> to <Directory /home/user/Websites/

3) I then ran the following command to disable the Default file and enable the Mysite file:

```
sudo a2dissite default && sudo a2ensite mysite
```

4) Restarted Apache2:

```
sudo /etc/init.d/apache2 restart
```

Unfortunately, after doing the above I get an error when I try and access localhost in the browser -

"Forbidden

You don't have permission to access /Sample.html on this server."

Now, common computer sense tells me that I need to grant permission somewhere but I have no idea where - in the Mysites file? On the actual folder located at /home/username/Websites?

Please help!

Seriously here, I have to admit that I am a bit irritated over this whole experience. What I need is someone who might be able to chat with me via Messenger or Skype and walk me through this. Look guys, I'm done with reading tutorials on this subject for now. I've spent all last night and a good chunk of tonight working on a resolution for this and nothing's freakin' working. For whatever reason I am not smart enough to figure this out on my own and although i've learned quite a bit from this experience, in the end my PHP files aren't parsing so i've failed.

Can somebody please help me? 

I still have yet to get MySQL up and running and I absolutely do not want to tackle that until my web server is working properly.

Feel free to e-mail me directly or reply to this thread. I certainly do appreciate the help.

Thanks!!

[email]AvenueStuart@comcast.net[/email]

---

### Post by hyper_ch on 2008-12-19
what do you get if you create a phpinfo.php file in /var/www with this content:
```
<?php phpinfo(); ?>
```

And then call it in your browser with [http://localhost/phpinfo.php](http://localhost/phpinfo.php)  ?

---

### Post by Avenue on 2008-12-19
That's a great question, Hyper.  

I actually have a PHP file which I created yesterday called Test.php.  I placed this file in the /var/www directory and then opened up a browser and called the file via [http://localhost/Test.php](http://localhost/Test.php).

What I get when I do that is a pop-up window asking me what I want to do with the file - save it or open it.  I know from poking around that this means there is something wrong with the configuration of PHP with Apache, but after reading too many tutorials and selected chapters in books, I cannot seem to resolve this.  

Frustrating.  

Can you recommending something else that I can try other than what i've tried in my post above?

Thanks!!

I'm trying to include a screenshot of the image i'm seeing, but for some odd reason I am not able to upload it to this forum.  It says that the image was uploaded, but it doesn't show up in my post. 

Why do things have to be so damned complicated?

---

### Post by Avenue on 2008-12-21
I finally found resolution to this problem.  I removed the following mod:

```
libapache2-mod-php5
```

Then I re-installed it.  After the re-installation, I then ran the following:

```
a2enmod php5
```

For some reason this worked, though i'm not sure why.  My PHP files are now displaying correctly in the web browser rather than displaying a window asking if i'd like to download the file.

---

