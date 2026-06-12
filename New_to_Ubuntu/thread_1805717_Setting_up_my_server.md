---
title: "Setting up my server"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by hookitup on 2011-07-16
So ppl i decided to set up a file server last night, couple issues arose with graphics then i got them fixed, i dont know very much at all about terminal so i had to install the ubuntu GUI for it, it now is up and running and looks just like ubuntu , now how do i go about turniing this baby into a server, i want to be able to store all my movies files pictues ect: on it and be able to access these no matter where i am and it needs to be secure...  some great step by step help would be awesome sence i am still a noobie, 

Thanks in advance.

---

### Post by hobbit1983 on 2011-07-16
hookitup

Sounds like you have plans for your machine - cool!!!

First thing you need to do is work out exactly what you want your server to do.  I will list a few of the most common and give you pointers of what to look for.

Network Drive.  If you want to share a folder of your music, files etc then try installing SAMBA.  This will allow you to securely share files and folders using the SMB protocol (the same one windows uses) over a network including the internet.  However you may need to configure your local network to allow inbound requests through.

Web Server - if you want to create a webs server start searching for Apache.  This is the most common webserver and for my opinion the best.  This will allow you to host your own website from your server.  If you would like to add scripting capability then add php and mysql to your configuration.

Good luck in setting your server up.  Have fun.

---

### Post by Dangertux on 2011-07-16
> **hobbit1983 said:**
> 
***SNIP***
If you want to share a folder of your music, files etc then try installing SAMBA.  This will allow you to **securely** share files and folders using the SMB protocol (the same one windows uses) over a network including the internet.  
***SNIP***


I am not so sure that I agree that samba is the best choice if you want to share files remotely (ie: outside of your local network).

Sharing files over the Internet with samba presents two issues up front. One, samba is not really all that secure. Regardless of if it is running on Windows or Linux, the nature of the server is relatively weak. Two, samba is really designed for local sharing, thus not over the Internet.

You might consider SSH for remote sharing via SFTP.  

Whenever you say you want to be able to access your server from anywhere, security is always going to come into play heavily. You will not be the only one able to access the system. The trick is making it so you are the only one able to access the data.  I would highly recommend shying away from Samba for remote sharing (ie: outside your LAN), I really can't stress that enough.

---

### Post by hobbit1983 on 2011-07-16
Stands corrected!

---

### Post by timmans on 2011-07-16
If you are planning to access your server from a linux box (or laptop), I would recommend SSH and SFTP. Make sure you use keys and not passwords for authentication. Have a look at [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

For remote server admin, I use Webmin, although apparently there are some issues with Webmin updating system packages, so I would just use the command line for that.

---

### Post by hookitup on 2011-07-18
thanks everyone, when i was installing it i got a screen asking what kind of server it is going to be and i saw samba file server as an option so i picked it because it said file server, which is what i want. was this wrong ,, should i pick something else ?

 SSH sounds like its the way to go, any information on how to set this up ?
 
i remember there being an openSSH option when asked to chose what kid of server it will be ,, should i have chose this one ? i can reinstall if this will make the process easer.

---

### Post by hookitup on 2011-07-19
anybody ?^^^^^^^^^^

---

### Post by skatinjj on 2011-07-19
You may not have to reinstall.  Just download openssh and start with that.

---

### Post by skatinjj on 2011-07-19
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html")

Well here is the tutorial.....google works magic

---

### Post by Dangertux on 2011-07-19
If you are trying to remove samba server you can try the following

```
sudo apt-get remove samba smbfs
```

---

### Post by hookitup on 2011-07-19
the negative about the tutorial is that i dont know how to do some of it ,i guess i can just mess around with it and see how far i get.

---

### Post by skatinjj on 2011-07-19
If you have questions or get stuck, just ask =)

---

### Post by amjjawad on 2011-07-19
If I want to setup a server, my first step would be "**google search**". 
I must learn and understand what's a server? what kind of servers are exist? how can I use them? etc etc. Then, I'll start setting it up myself. In case I'll face some problems, then will go back to Google (which in most cases will refer me back to here) and finally I would start a new thread here.

That's how one should start doing this :)

Now, you need to start reading some useful links:

[http://en.wikipedia.org/wiki/Server_%28computing%29](http://en.wikipedia.org/wiki/Server_%28computing%29)

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

You need few seconds to find the above on Google or here: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Good luck!

---

### Post by hookitup on 2011-07-20
thanks everyone, shes alive now, i can access it from my home network, have yet to find out how to access it while away

---

### Post by skatinjj on 2011-07-20
> **skatinjj said:**
> [https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html")

Well here is the tutorial.....google works magic

Have you gone through this yet to setup openssh on both client and server?

---

### Post by androssofer on 2011-07-20
also if u want to access it from the interwebz its easiest to hav a dynamic host name. (assuming u dnt already have 1) dyndns.org is the best option (in my opinion) as its free etc etc... to get an account, go here (pick the free option :) ):

[http://www.dyndns.com/](http://www.dyndns.com/)

then follow this tutorial on how to link it to your computer

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

then you'll want to set up port forwarding on your router/local network. tht will be specifc to your network tho, so will need more info on it to find a tutorial/explain how to for ya...

---

### Post by hookitup on 2011-07-20
oh ok ,,, i am going to be useing a ubuntu laptop to access my server and the files, video , music on it....

---

### Post by androssofer on 2011-07-20
> **hookitup said:**
> oh ok ,,, i am going to be useing a ubuntu laptop to access my server and the files, video , music on it....

on ur network? or internet aswell?

when you get ssh set up (and dyndns), to access it on ur laptop on the internet all u will need to do is:

```
ssh username@hostname.dyndns.org
```

or if ur own network:

```
ssh username@networkip
```

and to transfer files you wud use:

```
sftp username@hostname.dyndns.org
```

---

### Post by hookitup on 2011-07-21
hello folks, so on this page [https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)
if u go to the bottem where SSH key is , is this done on the server or the computer thats going to be remoteing into the server ?????



oh and also i am trying to edit something in etc/ssh/sshd_config ,,, 
how do i get into the folder? 

if i do gedit ~/etc/ssh/sshd_config 
or      gedit /etc/ssh/sshd_config
or      gedit ~/.etc/ssh/sshd_config

they open a blank file ,,

if i go to my hold folder in the gui form and then go to etc then ssh, then open the sshd_config file i can view whats in it but its read only .. i am looking to edit this to set a banner and disable password and all that good stuff

---

### Post by skatinjj on 2011-07-21
I am  not 100% certain on which PC to run the command for the keys.

As for not being able to get to /etc/ssh/sshd_config, I usually cd to the directory where the file is:

```
cd /etc/ssh/sshd_config
```

then

```
sudo gedit sshd_config
```

Be sure you make a back up of it first though

```
 cp ssh_config ssh_config.backup
```

---

### Post by skatinjj on 2011-07-21
I am pretty sure you generate the keys on the client PC though.  I just have never done it before.

---

### Post by hookitup on 2011-07-21
oh that worked , thanks, um oh ok , i do it from the client pc when i am ssh'ed into the server or just on the client machine in a clean terminal ?

---

### Post by skatinjj on 2011-07-21
Just on the client machine in the terminal.

---

### Post by androssofer on 2011-07-22
this is prob the best ssh tutorial i've found for ssh public key:

[http://www.petefreitag.com/item/532.cfm](http://www.petefreitag.com/item/532.cfm)

---

### Post by hookitup on 2011-07-22
hahah thanks ,, these guides are so confusing,  although they have alot of information they dont have the fine details like if it is done on the server or the other machine. i have not yet done the keys because i am still looking for a guide that i fully understand

---

### Post by skatinjj on 2011-07-22
Ok, the above guide tells you how to do the key.

Run this on the your laptop:

```
ssh-keygen -t dsa
```

then run this on your server (if it does not have a .ssh directory in the home folder):

```
ssh-keygen
```

then copy the public key from the laptop to the server:

```
scp ~/.ssh/id_dsa.pub remote.server.com:.ssh/authorized_keys2
```

Of course replace remote.server.com with your own domain name or IP address of the server

---

### Post by hookitup on 2011-07-27
oh ok thats helpfull. i havent had time in a few days, been super busy but i will try this today and get back.. what do you mean by : > then run this on your server (if it does not have a .ssh directory in the home folder):
 how do i know if it has a ssh directory in the home folder ?

oh and how do it preform this ?```
scp ~/.ssh/id_dsa.pub remote.server.com:.ssh/authorized_keys2
```

i just enter it on the laptop terminal correct ?

sorry i am still a noobie with the terminal. hahaha

---

### Post by skatinjj on 2011-07-27
To check to see if you have a .ssh in your home folder on the server run this from your home directory:
```
ls -as
```

If .ssh is listed you have it.  If not run this:

```
ssh-keygen
```

and yes the command I gave you to run on the laptop is from a terminal.

---

### Post by nothingspecial on 2011-07-27
```
scp ~/.ssh/id_dsa.pub [COLOR="Red"]remote.server.com[/COLOR]:.ssh/authorized_keys2
```

You change the bit in red to the address of the server

---

### Post by skatinjj on 2011-07-27
> **nothingspecial said:**
> ```
scp ~/.ssh/id_dsa.pub [COLOR="Red"]remote.server.com[/COLOR]:.ssh/authorized_keys2
```

You change the bit in red to the address of the server

Thanks for the clarification nothingspecial.  I overlooked part of his post in my haste :/

---

### Post by hookitup on 2011-07-28
so i fallowed the exact steps you gave me ,, and it worked fine , then i disabled password authentication and now i cant get into my server, i get a permission denied (publickey)


Good thing im sitting right next to it,,,
now what did i do wrong here . im assuming it isn't reading my code ????

---

### Post by androssofer on 2011-07-28
> **hookitup said:**
> so i fallowed the exact steps you gave me ,, and it worked fine , then i disabled password authentication and now i cant get into my server, i get a permission denied (publickey)


Good thing im sitting right next to it,,,
now what did i do wrong here . im assuming it isn't reading my code ????
humm... wen u created the pub key file, did u add a password to it?
if so, wen you tried to log in, it should have asked you for the pub key password. if u didnt set a password it shuda just logged u in...  did it work like tht b4 u turned off passwords?

---

### Post by skatinjj on 2011-07-28
Did the server already have a .ssh directory or did you have to run ssh-keygen to create it?

---

### Post by hookitup on 2011-07-28
> humm... wen u created the pub key file, did u add a password to it?
if so, wen you tried to log in, it should have asked you for the pub key password. if u didnt set a password it shuda just logged u in... did it work like tht b4 u turned off passwords?

i did not make a password, it generated my key and that ranomart picture, but befor i disabeled password authentication it asked for the password and i put it in and it worked but after i disabeled the password i got the error. 

> Did the server already have a .ssh directory or did you have to run ssh-keygen to create it?

it did not have one so i did the code u gave me and i did the same process as i did on the laptop which was when prompted for a place to store it i hit enter so it goes into default then it asked if i want a password i just hit enter then enter again then it showed me my key and the randomart.

---

### Post by skatinjj on 2011-07-28
Let's do this step by step.

1:  You ran this on the client (laptop)?

```
ssh-keygen -t dsa
```

You accepted the defaults?

2:  You then ran this on the server:

```
ssh-keygen
```

Accepting all the defaults to create your .ssh dir in your home folder?

3: Then you ran this on the client(laptop)?

```
scp ~/.ssh/id_dsa.pub remote.server.com:.ssh/authoriz
```

Replaced "remote.server.com" with your server's domain or ip address?


If all that went well, make sure the pub key copied properly to the server from the laptop.

---

### Post by hookitup on 2011-07-28
yeah thats the exact process i did, hummm but when i did the code  ```
scp ~/.ssh/id_dsa.pub remote.server.com:.ssh/authoriz
```
the outcome looked as if i was just remoting in like useing the command ```
 ssh user@serverIP
```
i know this is not the command to be remoting it,, its the command to copy the key which is y i expecting to see something like "pub key copied successful" or something of that nature. 
know what i mean ? could i have done this wrong ?

---

### Post by hookitup on 2011-07-28
hummm so i didnt notice yesterday but i found out that my server made 

id_rsa
id_rsa.pub

under /home/username/.ssh/

and my laptop made

id_dsa
id_dsa.pub
known_hosts

under /home/username/.ssh/


..... so why did the server make rsa and the laptop make dsa ,,, only reason i can think is that when i did keygen command on laptop it was ssh_keygen -t dsa
and on server it was just ssh_keygen ,,,, does it make rsa by default unless u specify ?

anybody know how to fix ?

---

### Post by skatinjj on 2011-07-28
Just delete the rsa info from the server and copy over the laptop's dsa info.

---

### Post by hookitup on 2011-07-28
lil help on how to :) i dont remember all the commands hahaha

---

### Post by skatinjj on 2011-07-28
All you have to do is cd to the ~/.ssh directory.

Then run:

```
rm id_rsa
```
and
```
rm id_rsa.pub
```

then run this again:

```
scp ~/.ssh/id_dsa.pub remote.server.com:.ssh/authoriz
```

After that, make sure id_dsa.pub is in the .ssh/authoriz folder on the server.

It will look like an ssh session because the command scp(secure copy) uses the ssh protocol.

---

### Post by hookitup on 2011-07-28
this just doesnt want to work for me ,,, i can jump into the server when doing ```
 ssh user@serverIP
```

but when i do ```
scp ~/.ssh/id_dsa.pub remote.server.com:.ssh/authoriz
```
 i get permission denied when entering my password ,,


lol makes no sence

---

### Post by androssofer on 2011-07-29
> **hookitup said:**
> this just doesnt want to work for me ,,, i can jump into the server when doing ```
 ssh user@serverIP
```

but when i do ```
scp ~/.ssh/id_dsa.pub remote.server.com:.ssh/authoriz
```
 i get permission denied when entering my password ,,


lol makes no sence

hav u turned on password authentication again? cus scp might need it to run... a few post ago u said u disabled it:

> so i fallowed the exact steps you gave me ,, and it worked fine , then i disabled password authentication

so allow password access again and i will go thru the steps again from the start to make sure it was all done right:

on the client:

```
ssh-keygen -t rsa
```

it will ask the file to add it to... just hit enter.

then cus u made 1 earlier it will ask:

```
/home/username/.ssh/id_rsa already exists.
Overwrite (y/n)? 
``` 

type 'y' and hit enter.
then it will ask for a password. this is optional. on my own network i wouldnt use 1, but over interwebz i def would. 

then again on the client run:

```
scp ~/.ssh/id_rsa.pub username@remote.server.com:.ssh/authorized_keys2
```

replacing username with your username (on the server) and remote.server.com with your server ip/host name and it will copy the key across for u. then do your standard ssh:

```
ssh username@remote.server.com
```

and it will connect with public key authentication. if you added a password to your public key it will ask for it, if not, it will log you straight in.. 

then u can disable password authentication again on the server. and try again, and it should work :-)

---

### Post by skatinjj on 2011-07-29
+1

I seemed to have missed a step while reading :/

My apologizes.

---

### Post by egrovesystems on 2011-07-29
Just u read out this, u can have more info and also could find out a way to shot out your problems

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by hookitup on 2011-07-29
i restored my defaults so yes the password auth is back on and ok i will attempt this again

---

### Post by hookitup on 2011-08-02
> **androssofer said:**
> hav u turned on password authentication again? cus scp might need it to run... a few post ago u said u disabled it:



so allow password access again and i will go thru the steps again from the start to make sure it was all done right:

on the client:

```
ssh-keygen -t rsa
```it will ask the file to add it to... just hit enter.

then cus u made 1 earlier it will ask:

```
/home/username/.ssh/id_rsa already exists.
Overwrite (y/n)? 
```type 'y' and hit enter.
then it will ask for a password. this is optional. on my own network i wouldnt use 1, but over interwebz i def would. 

then again on the client run:

```
scp ~/.ssh/id_rsa.pub username@remote.server.com:.ssh/authorized_keys2
```replacing username with your username (on the server) and remote.server.com with your server ip/host name and it will copy the key across for u. then do your standard ssh:

```
ssh username@remote.server.com
```and it will connect with public key authentication. if you added a password to your public key it will ask for it, if not, it will log you straight in.. 

then u can disable password authentication again on the server. and try again, and it should work :-)



it just worked ,,, thanks everybody for all your help ,,, i am going to be setting it up now so i can access it on the web ... wish me luck ,,, if i have troubles ill post back

---

