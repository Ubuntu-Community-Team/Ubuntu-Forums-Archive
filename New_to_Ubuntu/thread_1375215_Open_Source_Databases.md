---
title: "Open Source Databases"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by edempco on 2010-01-07
Hi,

I am attempting to make the transition from W to Ubuntu. One confusion regards databases. I have lots of questions, but the overarching question has to do with connecting databases on an Apache server to a Ubuntu desktop. Open Office Base (OOBase) goes gray-screen while operating, which does not make me confident that I can use it on the desktop. It appears that the desktop system is slowed, possibly because the desktop resources are being completely used.

Here is the essence of my question. What open source database can be used on the desktop and what open source database can be used on an Apache server that will be easy to integrate?

My need is to have a database on the server that will capture registraion information for members of an association using web input and reporting screens. This information must be easily ported to the desktop, used, modified, and sent back to the server.

Please help me clarify this question, if necessary, to assist with obtaining sugestions.:confused:

---

### Post by ibuclaw on 2010-01-07
The two most popular database engines are MySQL and PostgreSQL.

MySQL is the default with the lamp-server package.

Regards
Iain

---

### Post by bodhi.zazen on 2010-01-07
LAMP 

Linux
Apache
MySQL
PHP

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by edempco on 2010-01-07
Okay, it looks like MySQL. I hope the learning curve is not too steep. I know Access, but do not program. I've been to the MySQL site. I don't know what "lamp" means. I checked the "applications" drop-down on the Ubuntu desktop for "lamp" or "MySQL" and only found OOBase. Where do I start?

Yes, I am asking someone to take me by the hand :redface:

---

### Post by ibuclaw on 2010-01-07
> **edempco said:**
> Okay, it looks like MySQL. I hope the learning curve is not too steep. I know Access, but do not program. I've been to the MySQL site. I don't know what "lamp" means. I checked the "applications" drop-down on the Ubuntu desktop for "lamp" or "MySQL" and only found OOBase. Where do I start?

Yes, I am asking someone to take me by the hand :redface:

Bodhi has already explained what LAMP means.
It's an integration of 4 applications to make suitably generic webserver.

**L**inux, **A**pache, **M**ySQL, **P**HP

The way you would go about it is installing the lamp-server task/package.

```
sudo tasksel install lamp-server
```
Then setup + enable **ufw** (Uncomplicated FireWall).
```

sudo ufw default deny
sudo ufw allow http
sudo ufw enable

```
And then open a browser and browse to [http://localhost]("http://localhost")
To see your WebServer in action =)

Don't worry, no one from the outside world can see it. In order to do that - you must enable **port forwarding** on your Router.

Regards
Iain

---

### Post by edempco on 2010-01-07
I appreciate the help and I am following your instructions. I am assuming that there is no "package" that can be added by the "applications" section of Ubuntu; thus the reason to use terminal window and the command:sudo tasksel install lamp-server
Assuming what was done is that the lamp-server was polled to download and install the "package."

Then, the firewall had a hole poked in it to send and receive data to the database - just guessing.
sudo ufw default deny
sudo ufw allow http
sudo ufw enable

All of this seemed to go well enough. The last line reported that it was enabled.

When I browse to [http://localhost]("http://localhost/") the browser gives me a "page load" error. Is there something I missed?

---

### Post by bodhi.zazen on 2010-01-07
In general , server applications are not graphical, and thus you will not see apache, mysql, or php in your menu.

For installing applications, if you want a graphical tool, there are several:

[InstallingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingSoftware") 

Personally I prefer apt-get and synaptic.

If you want a graphical tool for managing your servers, again there are several, from webmin to phpmyadmin

[http://www.webmin.com/intro.html](http://www.webmin.com/intro.html)
[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

I already linked you to a good page to get you started on LAMP

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Not sure why it is not working, try

```
sudo service apache2 restart
```

and post any errors.

In terms of mysql, what is you are trying to do ? Most web applications (Wordpress, Moodle, etc) have detailed instructions on how to set up a mysql data base.

---

### Post by edempco on 2010-01-07
Thanks for the explanation regarding graphical installations - you can already tell I lean that way. Don't know what apt-get and synaptic are yet. I'll look them up.

Attempted the restart, but got the following:

ed@Ubuntu:~$ sudo service apache2 restart
sudo: unable to resolve host Ubuntu
[sudo] password for ed: 
sudo: service: command not found
ed@Ubuntu:~$ 



Regarding my application of the database; as I mentioned in the first post, I need to have a database on the server that will capture registration information for members of an association using web input and reporting screens. This information must be easily ported to the desktop, used, modified, and sent back to the server.

---

### Post by bodhi.zazen on 2010-01-07
> **edempco said:**
> Thanks for the explanation regarding graphical installations - you can already tell I lean that way. Don't know what apt-get and synaptic are yet. I'll look them up.

Attempted the restart, but got the following:

ed@Ubuntu:~$ sudo service apache2 restart
sudo: unable to resolve host Ubuntu
[sudo] password for ed: 
sudo: service: command not found
ed@Ubuntu:~$ 

What version of Ubuntu are you using ?

Try ```
sudo /etc/init.d/apache2 restart
```

The error "sudo: unable to resolve host Ubuntu" suggests you have a problem with either your /etc/hostname or /etc/hosts file, you need your hostname to be the same in those files.

> Regarding my application of the database; as I mentioned in the first post, I need to have a database on the server that will capture registration information for members of an association using web input and reporting screens. This information must be easily ported to the desktop, used, modified, and sent back to the server.

mysql will do this for you, but the question is who is developing the web pages and does that person know how to use php and mysql ?

---

### Post by edempco on 2010-01-07
Still no luck with restarting using:
sudo /etc/init.d/apache2 restart

My Ubuntu version is 8.04 LTS. 


Regarding web page development - I do that, but do not, at this time, know how to use MySQL and I would rather not have to learn a programing or scripting language like PHP - didn't have to do that for Access and would not expect to have to learn that for any other full-featured database. I have used all W-based programs to build web pages, develop databases, upload and download, etc., etc. I use a local web service that has decided not to renew W-licenses and when the W-server goes down, that is the end of FrontPage and the whole thing. I have access to both the W-server and the Apache2 server where I am redeveloping the new webpages. When finished, I will have the ISP switch servers for me. 

Until then, I am attempting to make a complete conversion to Ubuntu in the office. I am okay with Open Office, with the exception of Base. I can get around in Base well enough, but it goes gray-screen and hangs too much. Will probably resort to using Kompozer for webpage development along with BlueFish, Kommander, and hand tweaking - nothing seems to handle webpages in Ubuntu like FrontPage. I need to learn MySQL (it seems). I have allready attempted to load and use "Webmin", as suggested, because I need a program to manage membership access - currently using SpookyLogin on the W-server for this purpose. I have had no luck with Webmin either. It loaded using a debian package automatically, but I can't find it and do not know enough to find it and load it.

I'm learning, but I ain't there yet.

---

### Post by bodhi.zazen on 2010-01-07
> **edempco said:**
> Still no luck with restarting using:
sudo /etc/init.d/apache2 restart.

What error message did that command give you ? It is not sufficient to state it did not work.

---

### Post by edempco on 2010-01-07
As suggested, I read a lot of stuff. I went to the installation pages for Ubuntu, selected the right version, found the LAMP (Linux, Apache, MySQL and Perl/Python/PHP) page and replicated the installation using the same terminal command: 

**sudo apt-get install apache2**

This time it echoed:
ed@Ubuntu:~$ sudo tasksel install lamp-server
sudo: unable to resolve host Ubuntu
ed@Ubuntu:~$ 

Any ideas?
:confused:

---

### Post by JKyleOKC on 2010-01-07
> **edempco said:**
> I need to learn MySQL (it seems). I have allready attempted to load and use "Webmin", as suggested, because I need a program to manage membership access - currently using SpookyLogin on the W-server for this purpose. I have had no luck with Webmin either. It loaded using a debian package automatically, but I can't find it and do not know enough to find it and load it.

I'm learning, but I ain't there yet.To run Webmin, open your browser (Firefox?) and in the address line type
```
http://127.0.0.1:10000

```which should launch the main screen of Webmin. It will give you graphical interfacing to almost anything you want to configure, but you may need to google for help pages to get the most out of it.

A first step to learning MySQL is by way of MSAccess in Windows. If you use any queries in Access, load one up and then from the menu click "View SQL" to see what Access generates for you behind the scenes. Copy that result down verbatim, including all punctuation, and use it in MySQL. "SQL" stands for "Structured Query Language" and it's a standardized database programming language. Not all versions of it are identical, but they should all be close enough to get you in the ballpark.

The PHP part of the LAMP package is the equivalent of the VBA feature that Access uses behind the scenes to design forms and reports. You can google for "PHP tutorial" to find several rather easy sets of examples and instructions to create your forms.

That error message "unable to resolve host Ubuntu" indicates that you have some kind of problem not necessarily related to installing LAMP. Your prompt indicates that your system's host name is "Ubuntu" and it's not at all clear to me why sudo is unable to resolve it...

Hope this helps!

---

### Post by bodhi.zazen on 2010-01-07
> **edempco said:**
> As suggested, I read a lot of stuff. I went to the installation pages for Ubuntu, selected the right version, found the LAMP (Linux, Apache, MySQL and Perl/Python/PHP) page and replicated the installation using the same terminal command: 

**sudo apt-get install apache2**

This time it echoed:
ed@Ubuntu:~$ sudo tasksel install lamp-server
sudo: unable to resolve host Ubuntu
ed@Ubuntu:~$ 

Any ideas?
:confused:

As I indicated the last time you posted this message, your hostname needs to be the same in /etc/hosts and /etc/hostname

Post the contents of the two files you do  not know how to fix that (if the names do not match, you can not use sudo, and in that event you will need to fix it with a live CD or booting to recovery mode).

---

### Post by edempco on 2010-01-08
JKyleOKC: As you suggested, I used 
[http://127.0.0.1:10000](http://127.0.0.1:10000)
in Firefox (I've used this for years) and got:
**[COLOR=Sienna]Error - Bad Request[/COLOR]**

 [COLOR=Sienna]This web server is running in SSL mode. Try the URL [https://ip6-localhost:10000/](https://ip6-localhost:10000/) instead.[/COLOR]

Used the suggested URL and got a security warning, that I over road and was rewarded with a login screen for Webmin. Guessed that the login might be the Ubuntu login for this desktop and again was rewarded with the full menu! [FONT=Century Gothic][SIZE=4][COLOR=Navy]**THANK YOU!**[/COLOR][/SIZE][/FONT]

AND ... thank you again for the great transitional information about the connection between Access and MySql. Your instruction makes eminent sense and allows me to use my previous knowledge to make the transition. May I suggest that you could have your own thread or pages using this same technique to help other, bagage-dragging, W-users make the transition to Ubuntu? Your instructions have already been saved for future reference.

Bodhi.zazen: I am unsure of what exactly to do. You said:

> As I indicated the last time you posted this message, your hostname needs to be the same in /etc/hosts and /etc/hostname

Post the contents of the two files you do not know how to fix that (if the names do not match, you can not use sudo, and in that event you will need to fix it with a live CD or booting to recovery mode).I understand that I have a hostname problem, but do not know how to address it. I am not sure I am asking the right question, but where will I find "/etc/hosts and /etc/hostname" or the two files I don't know how to fix? Sometime, I try to follow the words written to the letter and sometimes I am a little dense, sorry.:confused:

---

### Post by JKyleOKC on 2010-01-08
> **edempco said:**
> I understand that I have a hostname problem, but do not know how to address it. I am not sure I am asking the right question, but where will I find "/etc/hosts and /etc/hostname" or the two files I don't know how to fix?Here's how to find those files, first via the command line and then using your browser.
From the command line:
```
less /etc/hosts
```
which will display the file's content. Press "q" to return to the command line. Then do
```
less /etc/hostname
```
and compare the two listings. The hosts file will have several lines while hostname will have only one. There should be one in "hosts" that matches the one in "hostname" including the capitalization.
From the graphical interface, browse to "File System" and from there to the "etc" directory (folder). Its display should include both files; select each in turn and view it.
Unfortunately the procedure for fixing a problem using the live CD is a bit complex so I'll leave the step-by-step instruction for that to others... Hope this helps get you started though.

---

### Post by edempco on 2010-01-08
JKyleOKC: Again, your instructions are very intuitive to my needs. I knew right where to go using the File Browser. I've been there several times to look at folders and files - just like File Explorer. I also used the terminal window and came up with the same file contents shown below:

# The following lines are desirable for IPv6 capable hosts 
 ::1 ip6-localhost ip6-loopback 
 fe00::0 ip6-localnet 
 ff00::0 ip6-mcastprefix 
 ff02::1 ip6-allnodes 
 ff02::2 ip6-allrouters 
 ff02::3 ip6-allhosts 
 192.168.0.21 localhost 
 192.168.0.22 ed-desktop.Workgroup 
 /etc/hosts (END)  
  
 

 Ubuntu 
 /etc/hostname (END)


Okay, I see it,it is not right, how can I fix it? Can I open the file using a text word processor and make the change?

---

### Post by bodhi.zazen on 2010-01-08
You will need to become root.

normally one uses sudo 

```
sudo -i
```to open a root shell. But you may not be able to do this. Did you by chance set a root password ?

```
su -
```If not, then you need to either boot to recovery mode or boot a live CD.

If you boot to recovery mode, you will not have a gui, you can start one with 

Use Nano

```
nano /etc/hostname
```Add any hostname you want, example "ubuntu"

> UbuntuSave and close nano (ctrl-X , choose yes to save changes).

Now open /etc/hosts and add two lines (anywhere)

( nano /etc/hosts )

> 127.0.0.1 localhost Ubuntu
127.0.1.1 Ubuntu

Again save and exit nano

Reboot and you should be able to use sudo again, test it with

```
sudo -i
```

---

### Post by JKyleOKC on 2010-01-08
Try this:
Reboot your machine and get to the Grub menu right at the start of boot-up. You may have to press ESC (for *buntu versions before 9.10) or SHIFT (9.10 and later). Arrow down to the "recovery" line and press Enter. This should get you to another menu; select the "boot to shell" item from it. This will log you in with root privileges, so be very careful about changing things!
Now navigate to /etc/hosts and open it in your text editor of choice. Add these two lines to the end of the file (be sure to match the capitalization):
```
127.0.0.1 localhost
127.0.1.1 Ubuntu
```
then save the file and reboot normally.
You should now be able to use "sudo" with no error messages.

---

### Post by edempco on 2010-01-08
Bodhi.zazen: I followed your suggestion and opened a terminal window; used the command "sudo -i" and obtained root privileges. Nano worked fine and reminded me of an old DOS text editor. I rebooted and then opened the browser to [http://localhost/](http://localhost/) and was greeted with "It Works!" - the screen promised in the Apache2 setup instructions.

I am not sure that I am over the hurtle yet. I feel like I'm closer, but do not see how to get to MySql from this point. 

BTW: I have been learning Webmin and have found a login for MySql. It suggests the root login, but the root login does not work. I don't know if this helps or confuses.

Thank you both for your continued patience.

---

### Post by bodhi.zazen on 2010-01-08
If you use webmin, you need to at least temporarily set a root password.

```
sudo passwd
```

Then log in to webmin with that password.

If possible, I can not recall, create a new user in Webmin with Administrative rights (hint I always do this with web interfaces, make a new user rather then the default).

If you can log in as an alternate user, and perform sys admin, then lock the root account

```
sudo usermod -p ! root
```

---

### Post by edempco on 2010-01-08
bodhi.zazen: I can do all of that, but I already have root control. Could I do that later? I can see Root with Webmin and can create a new user. All of that seems straighforward.

What I am really interested in is MySql. Can you suggest anything else I an do to get this program working?

---

### Post by bodhi.zazen on 2010-01-08
I would secure the root account, whatever that means to you (I wouldlock it) and move directly to MySQL

You might like phpmyadmin , a web interface for Mysql.

[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

:twisted:

---

