---
title: "installed ubuntu 10.04 lucid lynx server LTS...HOW to setup local test server"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by richyrage on 2011-08-29
Hello again all.
I have just installed ubuntu 10.04 server LTS edition and selected the LAMP components, and everything went smoothly.

I completed the recommented update, and now Im currently wondering three main questions:

1.how to connect this ubuntu server to my windows computers (network) at home

2.how to make this ubuntu box a** local test server **to put my webpages and files on this box to access and test from one of the windows boxes (through a web browser like firefox)

3.what tools like webmin etc to learn,study and would be used in the maintenance and work to this server in the future.

Thanks for any tips/links to more info. with regards to these very noob questions....

Regards,
RichyRage

---

### Post by alphacrucis2 on 2011-08-29
> **richyrage said:**
> Hello again all.
I have just installed ubuntu 10.04 server LTS edition and selected the LAMP components, and everything went smoothly.

I completed the recommented update, and now Im currently wondering three main questions:

1.how to connect this ubuntu server to my windows computers (network) at home

2.how to make this ubuntu box a** local test server **to put my webpages and files on this box to access and test from one of the windows boxes (through a web browser like firefox)

3.what tools like webmin etc to learn,study and would be used in the maintenance and work to this server in the future.

Thanks for any tips/links to more info. with regards to these very noob questions....

Regards,
RichyRage


If you have LAMP installed and running, you should be able to browse to http://<the ip address of your server> from a web browser on the windows boxes. It should display a message saying something like "IT WORKS", which I recall is the contents of the default index.html file in /var/www. You just replace the default index.html file with your own home page and add other files for apache in /var/www. You can also configure apache to have virtual sites, or several sites bound to different ip addresses that you add as secondaries. You basically set it up however you want. If you want it to act as a Windows file server then you will want to make sure samba is installed. There are various guides for configuring in the ubuntu community docs as a starting place.

---

### Post by sandyd on 2011-08-29
> **richyrage said:**
> Hello again all.
I have just installed ubuntu 10.04 server LTS edition and selected the LAMP components, and everything went smoothly.

I completed the recommented update, and now Im currently wondering three main questions:

1.how to connect this ubuntu server to my windows computers (network) at home

2.how to make this ubuntu box a** local test server **to put my webpages and files on this box to access and test from one of the windows boxes (through a web browser like firefox)

3.what tools like webmin etc to learn,study and would be used in the maintenance and work to this server in the future.

Thanks for any tips/links to more info. with regards to these very noob questions....

Regards,
RichyRage

1. Plug it into the router via an ethernet cord. Unless you know how to manually configure wpa_supplicant, wireless is a bad idea.

2. Files served by apache2 are stored in /var/www 
I used to recomend using sftp on openssh, but vsftp is easy enough.
```

sudo apt-get install vsftpd
gksudo gedit /etc/vsftpd.conf

```
Remove the comment (pound) from in front of write_enable.
enable_anonymous should be uncommented and set to NO.

save it, close it, run
```

sudo service vsftpd restart

```

Aim the ftp client at your computer's ip address, and ill work.

p.s. You might wanna create a user in the www-data group that has a home folder of /var/www. Ill be easier since you don't have to transfer files around.

3. Don't use webmin. In the end, its always easier to look at configuration that you wrote yourself, rather than going huh? at automatically generated config.

HINT: install openssh. (sudo apt-get install openssh), and control your computer from somewhere else using PuTTY

---

### Post by richyrage on 2011-08-29
Hello guys!

Thanks for the quick responses,

I typed the ip address of the ubuntu box in a browser on the windows machine and all is good..thanks alphacrusis2

I will try out the vsftpd for the future ftp needs..thanks for that one sandyd.

this segueways into another situation, and that is I would like the ubuntu server to be seen from a windows explorer on a windows computer (also being able to read/write to the ubuntu box)
 I come across this posting 
[http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows)

which is titled '[B]HOWTO: Setup Samba peer-to-peer with Windows' 
and is this the tree I should be barking up?

Please inform when u have the chance.thanks
RR
[/B]

---

### Post by Wim Sturkenboom on 2011-08-29
Samba is for file sharing. Is that what you want?

If not, leave it. I develop webpages straight on the server; saves me the hassle of ftp'ing ;) I ssh into the server (e.g. with putty from a windows box) and use my favorite (linux) editor to create the webpages.

---

### Post by richyrage on 2011-09-02
Hello,
Thanks for the responses.

I have a question for sandyd, or anyone that has knowledge that they would like to share

`p.s. You might wanna create a user in the www-data group that has a home  folder of /var/www. Ill be easier since you don't have to transfer  files around.`

How would i go about getting this done, and if possible, can someone point me to a resource for learning how to add users, groups, etc, (basic nix workings) so I can get a 
handle on the basic tasks/commands  etc for ubuntu.

Thanks again,

RR

---

### Post by Wim Sturkenboom on 2011-09-03
man adduser
man groupadd

And check the 'see also' at the bottom of the man pages for related commands to modify and remove.

In my opinion /var/www is not the correct place for websites. Reason is that /var is intended for semi-permanent files. But that's just my opinion.

It's easier to change the document root of the website to somewhere in your home directory. Only disadvantage is that, without precautions, apache can not write there. That is not always ncecessary but e.g. for storing of generated reports or uploads of images it is. I use ACL to allow apache to write in a dedicated directory, but you can change the group of the files directory below to www-data and set the group permissions to rwx.

Below my setup as used in an intranet environment. I'm the developer, database and system administrator etc. 

```

/home/wim
  |
  +-- site 1
  |     +-- inc        --> common/secure stuff; apache can read
  |     +-- web        --> document root; apache can read
  |          +-- files --> apache can write here
  |          +-- index.php
  |
  +-- site 2
  |     +-- inc        --> common/secure stuff; apache can read
  |     +-- web        --> document root; apache can read
  |          +-- files --> apache can write here
  |          +-- index.php
  |

```
The document root for each site is 'web'. 'inc' is the directory where I place common stuff and stuff that should not be revealed (e.g. mysql connection functions that contain usernames and passwords); apache can read it but as it's outside the document root, visitors can't get it.

PS for one website, you can simply change the document root in /etc/httpd.conf

---

