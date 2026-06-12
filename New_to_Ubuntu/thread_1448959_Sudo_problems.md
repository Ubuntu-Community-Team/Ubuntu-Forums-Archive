---
title: "Sudo problems"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by Dadjitsu on 2010-04-07
I have been trying to follow a howto on installing lamp on ubuntu 9.10, from here 
[http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/](http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/)

I had my first problem with 
sudo /etc/init.d/apache2 restart
it said it didnt exsist, so I assumed that is a pathing problem

so I used sudo su and changed to the root directory and re issued the command, I then got an error saying the the system couldnt determin the host, which I presumed was todo with the config file httpd.conf, when I try to create this file it will not let me do so, even as root

what am I doing thats wrong.

I have done 2 fresh installs and im just getting frustrated now

---

### Post by ytecle on 2010-04-07
Please, can you give an instruction on how I can post a new threat?
thanks!

---

### Post by new_tolinux on 2010-04-07
> **ytecle said:**
> Please, can you give an instruction on how I can post a new threat?
thanks!
There's a button called "New thread" at the top-left of every subforum.
Click it and you'll go to another page where you can start a thread.

---

### Post by tekkidd on 2010-04-07
you could always do it one step at a time

```
sudo su
```

then 

```
cd /
```

then 

```
cd etc
```

then 

```
cd init.d
```

then type in ```
ls
``` and see if apache2 is listed

it it is then do 

```
apache2 restart
```

---

### Post by undecim on 2010-04-07
> **Dadjitsu said:**
> I had my first problem with 
sudo /etc/init.d/apache2 restart
it said it didnt exsist, so I assumed that is a pathing problem

Do you have apache installed?

---

### Post by philinux on 2010-04-07
> **ytecle said:**
> Please, can you give an instruction on how I can post a new threat?
thanks!

Here you go.

---

### Post by PhilMize on 2010-04-07
Though I don't know how to fix your issue I can recommend some awesome guides for getting lamp on ubuntu server. I checked out the website you posted and didn't look like the guy really explained much.

[http://www.howtoforge.com/ubuntu_lamp_for_newbies]("http://www.howtoforge.com/ubuntu_lamp_for_newbies")

Or just open up terminal and type "**sudo tasksel**". Prepare to be amazed. :)

Hope that helps!

---

### Post by sisco311 on 2010-04-07
> **Dadjitsu said:**
> I have been trying to follow a howto on installing lamp on ubuntu 9.10, from here 
[http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/](http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/)

I had my first problem with 
sudo /etc/init.d/apache2 restart
it said it didnt exsist, so I assumed that is a pathing problem

so I used sudo su and changed to the root directory and re issued the command, I then got an error saying the the system couldnt determin the host, which I presumed was todo with the config file httpd.conf, when I try to create this file it will not let me do so, even as root

what am I doing thats wrong.

I have done 2 fresh installs and im just getting frustrated now

Please post the output of:
```
cat /etc/hostname
cat /etc/hosts
```

Are you sure that lamp is installed?
```
sudo tasksel install lamp-server
```

[uhelp]community/ApacheMySQLPHP[/uhelp]

> **ytecle said:**
> Please, can you give an instruction on how I can post a new threat?
thanks!

Go to the sub-forum where you want to start the thread, i.e. [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326"), and click the New Thread button at the top (or bottom) left of the page.

Check out the [thread=1006656]Guide to Forum features[/thread].

---

### Post by Dadjitsu on 2010-04-07
> **tekkidd said:**
> you could always do it one step at a time

```
sudo su
```then 

```
cd /
```then 

```
cd etc
```then 

```
cd init.d
```then type in ```
ls
``` and see if apache2 is listed

it it is then do 

```
apache2 restart
```

sorry I havent made myself clear, I have managed to execute 
sudo /etc/init.d/apache2 restart ... once I had used sudo su command

the problem now is it says I dont have permission to create httpd.conf, even tho I am doing this from root

this is a clean install, I havent changed anything yet Im haveing pathing & permission problems, I have installed twice now and the same thing happens both times, I presume its me doing something wrong, tho I havent altered anything since the installation

---

### Post by undecim on 2010-04-07
The howto looks a little outdated. You shouldn't be creating httpd.conf, just put a new line in /etc/apache2/apache2.conf.

I just tested it on my server and it works fine.

Also, how are you trying to create httpd.conf? If you are root you shouldn't have those errors.

---

### Post by Dadjitsu on 2010-04-07
> **undecim said:**
> Do you have apache installed?
yes , I had the IT WORKS! from localhost

---

### Post by Dadjitsu on 2010-04-07
> **PhilMize said:**
> Though I don't know how to fix your issue I can recommend some awesome guides for getting lamp on ubuntu server. I checked out the website you posted and didn't look like the guy really explained much.

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

Or just open up terminal and type "**sudo tasksel**". Prepare to be amazed. :)

Hope that helps!
  a BIG Kiss :-)

thO id still like to know why I cannot create httpd.conf file from root

---

### Post by sisco311 on 2010-04-07
> **Dadjitsu said:**
> a BIG Kiss :-)

thO id still like to know why I cannot create httpd.conf file from root

How exactly did you try to create the file & what was/is the error message you get?

---

### Post by Dadjitsu on 2010-04-07
> **undecim said:**
> The howto looks a little outdated. You shouldn't be creating httpd.conf, just put a new line in /etc/apache2/apache2.conf.

I just tested it on my server and it works fine.

Also, how are you trying to create httpd.conf? If you are root you shouldn't have those errors.
  I used the command gedit /ect/apache2/httpd.conf

when I tried to save it says I dont have write permission for the file 

I am a total noob to linux so my appoach may be wrong as Im a life long windows ***** :p

---

### Post by sisco311 on 2010-04-07
```
gksu gedit /ect/apache2/httpd.conf
```

Check out [uhelp]community/RootSudo[/uhelp].

Oh, and don't use *sudo su* to start a root shell, if you really need a root shell, then run:
```
sudo -i
```run **exit** or press Ctrl+d to exit from it.

---

### Post by undecim on 2010-04-07
> **Dadjitsu said:**
> I used the command gedit /ect/apache2/httpd.conf

when I tried to save it says I dont have write permission for the file 

I am a total noob to linux so my appoach may be wrong as Im a life long windows ***** :p

The command should work fine as run from root, but I'm guess you aren't still root. If you see a # at the end of your prompt, that means you are root. If you see a $, that means you are a normal user.

as a normal user, try running "sudo gedit /etc/apache2/httpd.conf"

EDIT:

Also, you should understand that if you are root in a terminal, you are still a normal user everywhere else. If you are using the alt+f2 prompt for this, you will need to use "gksu gedit /etc/apache2/httpd.conf" to get a graphical password prompt.

---

### Post by Dadjitsu on 2010-04-07
Thanks to everyone for thier help, I have a lot of reading todo it seems

---

### Post by ytecle on 2010-04-07
Thank you Phil for the proving a nice graphic instruction for posting a new threat.

---

### Post by Dadjitsu on 2010-04-07
[QUOTE=sisco311;9088198]Please post the output of:
```
cat /etc/hostname
cat /etc/hosts
```Are you sure that lamp is installed?
```
sudo tasksel install lamp-server
```[uhelp]community/ApacheMySQLPHP[/uhelp]



when I type  cat /ect/hostname    I get

cat: /ect/hostname: no such file or directory

if I do it after typing sudo -i , I get the same response,

my system seems to not recognise paths and cmds, it has done this after 2 fresh installs


and yes LAMP is now installed and working, just my sudo is driving me nuts

using file browser,  dadjitsu-desktop.. localhost

I have the update manage check the system both times and it reports the system as being up to date

---

### Post by oldos2er on 2010-04-07
It's /etc, not /ect.

---

### Post by Dadjitsu on 2010-04-07
> **oldos2er said:**
> It's /etc, not /ect.

well spotted, one of those blindingly obvious mistakes, I checked my logs and yep I did type ect .... doh

subject resolved

---

### Post by PhilMize on 2010-04-08
> **ytecle said:**
> Thank you Phil for the proving a nice graphic instruction for posting a new threat.

:lolflag:Tthere's two Phil's in this thread. Took me a minute to realize you weren't talking to me. :lolflag:

---

