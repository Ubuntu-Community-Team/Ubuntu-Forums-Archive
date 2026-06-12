---
title: "ubuntu as a server for absloute begginer"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by 720iD on 2009-05-28
i am about to take the plunge into ubuntu again. i keep coming back to ubuntu everytime i try to get out of my windows box. i have still not managed to make the full transition,  yet here i am again. 

this time i would like to use (or test) ubuntu as a server. obviously it is not ubuntu that is trial here it is me and my ability to manage the system.

so i am looking for advice, guidance opinions on my plans before i take the plunge again. 

here is my plan, i want to set up a web server on my home computer this server shoudl be able to host a website which i can manage from anywhere on the web, just like any shared host or vps. now before people start giving me advice about the benefits of paid for hosting this is not really to host my websites, this is more for my learning purposes than to actually host any site.  

eventually i would like to have learnt enough to be able to manage my own server or vps out there in the real world of data-centres.

so this is what i would like advice and guidance on. 

i am not proficient in unix/ linux command lines. and often the first thing i  look for is a gui way of doing things. however i am not scared of the command line if know what i am doing. (mostly i dont know what i am doing)or i am following good instruction.

i am not sure whether i should install ubuntu server edition and persevere with command line, then install gui if needed. or to install ubuntu desktop and install all server packages that i need.

i dont know which would be most appropriate for my needs. i would like to learn to manage my server myself. 

i did have a few more questions but i cannot remember right now. thanks everyone.

---

### Post by Hospadar on 2009-05-28
Not to be harsh, but step one is get comfortable on the command line, especially for a server.

You really can do a lot in a GUI, but especially for a server, there will be some things you absolutely have to do in the command line, and some other things that are just so much faster and easier in the command line, you'd be a fool to avoid it.  I use the mysql-admin (gui) to manage my database all the time, because I don't do enough of it to remember the mysql admin commands.  But for a lot of other stuff, I do it all the time, and I'd really be going out of my way to *not* do it CLI-style.

Note also, you can still use graphical programs on a server, you just need an X server running on the machine you're logging in from.  From my example above, I run a headless (no monitor, no desktop environment) server, but I still have some of the more convienient graphical tools installed (mysql-admin, brasero because I sometimes burn cd's from the server, etc)

I won't go into all the details of setting up a web server, you can find a lot of info on google and the community docs link in my sig, but most importantly, you will want an ssh server installed on the server. (I think it comes installed in server by default, but if not, "sudo apt-get install ssh").

I really suggest that you go for a server installation, if you find you really need the gui, you can install "ubuntu-desktop" later.  But you'll get some nice extra speed from not having that baggage around.

Another note, some commands you should really look into:
apt-get (of course, install packages from the command line)
apt-file (allows you to find the package a file or program belongs to, whether the package is installed or not)
apt-cache search (search packages and their description from the command line)
top (or htop, command line resource monitoring)
kill (also killall, kill processes)
grep (filter output)
the list goes on.

If you google around, you'll find tons of great linux command line tutorials.  There is soooo much you can do on the command line (i.e. everything), in surprisingly easy and efficient ways.

Edit:
Also I forgot, the most important thing to getting your web server working from outside your house is to forward the needed ports to your server on your router (if you have a router)
22 for ssh
80 for http
etc.
google around if you need more info on that.

---

### Post by 720iD on 2009-05-28
> **Hospadar said:**
> Not to be harsh, but step one is get comfortable on the command line, especially for a server.

You really can do a lot in a GUI, but especially for a server, there will be some things you absolutely have to do in the command line, and some other things that are just so much faster and easier in the command line, you'd be a fool to avoid it.  I use the mysql-admin (gui) to manage my database all the time, because I don't do enough of it to remember the mysql admin commands.  But for a lot of other stuff, I do it all the time, and I'd really be going out of my way to *not* do it CLI-style.

Note also, you can still use graphical programs on a server, you just need an X server running on the machine you're logging in from.  From my example above, I run a headless (no monitor, no desktop environment) server, but I still have some of the more convienient graphical tools installed (mysql-admin, brasero because I sometimes burn cd's from the server, etc)

I won't go into all the details of setting up a web server, you can find a lot of info on google and the community docs link in my sig, but most importantly, you will want an ssh server installed on the server. (I think it comes installed in server by default, but if not, "sudo apt-get install ssh").

I really suggest that you go for a server installation, if you find you really need the gui, you can install "ubuntu-desktop" later.  But you'll get some nice extra speed from not having that baggage around.

Another note, some commands you should really look into:
apt-get (of course, install packages from the command line)
apt-file (allows you to find the package a file or program belongs to, whether the package is installed or not)
apt-cache search (search packages and their description from the command line)
top (or htop, command line resource monitoring)
kill (also killall, kill processes)
grep (filter output)
the list goes on.

If you google around, you'll find tons of great linux command line tutorials.  There is soooo much you can do on the command line (i.e. everything), in surprisingly easy and efficient ways.

Edit:
Also I forgot, the most important thing to getting your web server working from outside your house is to forward the needed ports to your server on your router (if you have a router)
22 for ssh
80 for http
etc.
google around if you need more info on that.

thanks for all that, it was  a big help and mostly supported what i was already thinking. plus a few extra tips, and i will definitely check out the signature links. 

well i decided to go for the server install and have run into a problem. 

i get to a certain point in the installation and i am asked to "insert the disk labeled 'ubuntu-server 9.04' and press enter" 
only the disk is already in the cdrom and i cannot open the cdrom at this point. 

i am given two options on the screen [go back] and [continue] i cannnot select either. 

i found another thread with this problem but there is no definite solution in it. 

i think i will try the desktop install and add the server packages. would i be able to remove some packages from the desktop install to increase the performance to that of the server edition. 

this might be a more sensible way to go for me allowing me to get used to the cli while still having the comfort of the desktop environment for that little bit of security.

---

### Post by chrisod on 2009-05-28
I installed server a couple of months ago - I think I'm on 8.10 though. I even have internal family wiki running on it now, and I've got a USB drive hanging off it that backs up my network drive.

One thing you might look into is Webmin. It's a GUI for a lot of the CLI stuff you need to do on server. It's helpful when you just want to get something done and don't have time for trial and error on the CL.

---

### Post by 720iD on 2009-05-29
> **chrisod said:**
> I installed server a couple of months ago - I think I'm on 8.10 though. I even have internal family wiki running on it now, and I've got a USB drive hanging off it that backs up my network drive.

One thing you might look into is Webmin. It's a GUI for a lot of the CLI stuff you need to do on server. It's helpful when you just want to get something done and don't have time for trial and error on the CL.

i like the look of webmin, when i get this installed i will try it, thanks

---

### Post by paul_anders on 2009-05-29
> i think i will try the desktop install and add the server packages

if your linux level is not all that up to scratch then you have partly 
answered your own question.
if you are serious about learning linux then dedication and practice is
a must. another tip is to buy a good book or two here are my suggestions

1. [http://rute.2038bug.com/rute.html.gz](http://rute.2038bug.com/rute.html.gz) 
(its a free book on line or you can buy it cheep)  its pretty old some may say its outdated but it will give you a strong foundation in linux.

2. [http://oreilly.com/catalog/9780596005283/preview.html](http://oreilly.com/catalog/9780596005283/preview.html)
this book is worth every penny (or kronor here in sweden)
after reading and practicing for a few months, let say 4 months every day 2 to 5 hours with time permitting, then you can at least begin to get your self around the system with ease.

my idea is this. if you want to run your own vpn or hosting server in the future then get it right today by learning and practicing as much as you can. use windows only on a need basis only and chuck your self in linux.

Good luck in the future
PA

---

### Post by madverb on 2009-05-29
I recommend installing Wordpress

---

### Post by 3rdalbum on 2009-05-29
I'm a bit of a lazy-bones. I could administer my home server on the command-line, yes sir. But I can't be bothered to. So I open an SSH connection to my server with the -X flag, and then I can run graphical configuration utilities. The programs run on the server, but communicate with the X server that's running on the computer I'm on.

Very easy.

---

### Post by nothingspecial on 2009-05-29
> **720iD said:**
>  

 would i be able to remove some packages from the desktop install to increase the performance to that of the server edition. 

this might be a more sensible way to go for me allowing me to get used to the cli while still having the comfort of the desktop environment for that little bit of security.

If you don`t want the desktop hogging resources when you`re not using it turn it off

```
sudo /etc/init.d/gdm stop
```

If you want to turn it on again
```

sudo /etc/init.d/gdm start
```

You can still run gui apps on your remote machine over ssh with -X. It might also be an idea to use the -C flag if your running heavy stuff.

I use this to log in to my headless machine

```
ssh -X -C -c blowfish address_of_my_machine
```

To explain 
-X forwards x letting you run guis on your remote
-C compresses it
-c encrypts, blowfish being the sort of encryption.

This was no 1 for me when I first put my machine under the stairs. Some stuff is just easier with the gui and faster in the sense that you don`t have to start reading man pages. But you`re going to have to launch them with a command. But what`s the command that launches the (for example) startup applications gui? In your menu go system > preferences > main menu find startup applications. Click it then click properties. In the window that pops up it tells you the command - gnome-session-properties. Now you can launch that on your server from your remote machine.

---

### Post by 720iD on 2009-05-29
> **madverb said:**
> I recommend installing Wordpress
are you sure this is meant for this thread?

---

### Post by 720iD on 2009-05-29
> **3rdalbum said:**
> I'm a bit of a lazy-bones. I could administer my home server on the command-line, yes sir. But I can't be bothered to. So I open an SSH connection to my server with the -X flag, and then I can run graphical configuration utilities. The programs run on the server, but communicate with the X server that's running on the computer I'm on.

Very easy.
any more information on how to set this up?

---

### Post by cariboo on 2009-05-29
If you just want to install the ALMP stack for learning purposes, you could just as well install it on your desktop system, that way you can have the benefits of both worlds. 

The problem you are having with the installation asking you to insert the cd-rom is usually caused by a bad iso burn. I've been able to bypass the problem by starting the install process again, but it only worked once, so it isn't recommended.

---

### Post by bodhi.zazen on 2009-05-29
If you want to run your server graphically look into things such as webmin ;)

Personally I agree with learning the command line. Most of what you do on servers falls into one of three categories :

1. Installing applications / updates == apt-get

2. Start / stop services == sudo /etc/init.d/apache2 start|stop|restart

3. Editing config files == nano|vim /etc/apache2/sites-available/yoursite.com

4. Transferring files to server == scp or you can use graphical clients, but no need for a graphical application on the server.

So really , X is not required.

See : [https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

---

