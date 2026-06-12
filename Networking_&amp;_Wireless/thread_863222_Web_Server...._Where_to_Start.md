---
title: "Web Server.... Where to Start?"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by mtgmutton on 2008-07-18
I want to set up a web server on my Ubuntu 8.04 desktop so I can share files with some of my friends, who live several miles away. I've been reading google search results, and I've gotten that I should use either Samba or Apache. But I'm not sure what to do next. I don't know much about how the internet works, so I'm a little lost...Any advice on this (or a link to a tutorial, or even a tutorial) would be greatly appreciated!

---

### Post by NullHead on 2008-07-18
Well I'd start with installing a server. You can use apache2 or an ftp server like vsftpd. I'd use ftp. Actually the easiest way to do file transfers is with sftp, but the problem is if you're not familiar with the command line and working with securing ssh, then it's not the best way to do it. 

Also, you need a level of knowledge about your system to get things working in a secure fashion. 

In my opinion, the best way for someone like yourself is to use a web file hosting site like [http://www.mediafire.com](http://www.mediafire.com) to host your files. 

If you wish, I can also try to walk you through installing apache2 for webhosting, but I know very little about making it secure or changing the configuration. 

Sftp is another issue harder for me to explain to you. 

FTP is also a difficult thing for me to explain, as per I hardly know much about these things either ...

---

### Post by mtgmutton on 2008-07-18
Thanks for the link, but I have a lot more files than 10 :(. I have somewhere around 180 files that I'd like to share, adding up to about 30 GB if I host all of them... But that's probably too many. I could just host about 20 at a time, which would make about 4 GB. If it isn't too much trouble, could you try to walk me through apache2? I can always google security and configuration and stuff later :)

---

### Post by NullHead on 2008-07-18
Sure I'd be glad to give it a shot!

Well we should start by opening the port for internet through your router's configuration. 

Go to [http://portforward.com](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm) and search by brand and model and then look for apache in the list of programs. Follow what it instructs you to do.

Next you want to install apache2. Run this from a terminal to install and start your apache server. ```
sudo apt-get install apache2
```That should install and start your apache server, but it might not start the server automagically. Lets make sure it's started. Run this from your terminal to make sure the server is started: ```
sudo /etc/init.d/apache2 start
```

Your server should now be started. This is the most configuration I know how to do to apache. I do know where to put your files and html docs though ;)

You need to put your docs in /var/www/

Now you should know that all I've used apache2 for is just intraweb stuff on my lan ... I don't know how to get apache2 to talk to the internet. Someone else will have to chime in on that, but this is as good as I can do for you.

---

### Post by NullHead on 2008-07-18
I just had another thought ...

You can make a torrent for the 40 or so files you have to share. 

It sounds like the BEST way to do it, but it might not work out for you; let me know. ;)

---

### Post by mtgmutton on 2008-07-18
Thanks, and if I can get them to use a bittorrent client, then it just might work... it would just be slow. How can they access the files from their computers? will the folder show up automatically or something? They are running windows...

---

### Post by Dr_Deadmeat on 2008-07-18
I would recommend Sftp, as it works with no configuration at all... 

To do this you have to install ssh on your file-server (execute this in a command line):
```
sudo aptitude install ssh
```

After ssh is installed, you need to connect to the server from a client...

With Ubuntu you click on 'Places', and 'Connect to service' (I am not sure about that, because I am on a non-english instalation).
If you fill out the forms like in this screenshot, it should work
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78190&stc=1&d=1216418188[/IMG]

When you hit connect, you will be asked for a password, and that is your standard password

In Windows you download [WinScp](http://winscp.net/eng/download.php), and you connect to the server with the IP, or the domain name to the server, but I haven't used this program in a while, so I cant explain how to use it...

You might want to add a new user to the server, to avoid giving away your password: To do this, you enter 'System'&#8594;'Administration'&#8594;'Users and groups'. From here you hit Unlock, and enter your root password, before you create a new user, with another password... After you do this, you create a shortcut to the files you want to transfer in the home folder of the new user, and you give the new user rights to copy those files (right click on the folder, and give Everybody rights to read and execute the files).

I hope this helps you a bit... If you want to create an apache server (or ftp) it is too complicated for me to explain to you.

---

### Post by NullHead on 2008-07-18
> **mtgmutton said:**
> Thanks, and if I can get them to use a bittorrent client, then it just might work... it would just be slow. How can they access the files from their computers? will the folder show up automatically or something? They are running windows...

As long as you put the files you're trying to share in the torrent file, they will receive them just as they are on your machine. 

The speeds will be as fast as your upload speed is. If you're unfamiliar with torrents, you can try Transmission or Deluge on you linux box and they can use µtorrent, all of which are free.

---

### Post by mtgmutton on 2008-07-18
This could work. But nonetheless, I would have to send them the torrent file, and they would have to download the files. Seeing as these files are mostly videos (thus the large size) i was hoping to save some time by just having them access the server and watching the videos off of that. Is this possible?

---

### Post by NullHead on 2008-07-18
OH that's why you want this ... you're right, a web server would be best. 

Just install it as I said and try it out. I'm no expert with apache, but give it a try.

---

### Post by mtgmutton on 2008-07-18
I set it up (with one file for starters), but how would they access the files? will it be listed as a network drive on their windows boxes?

---

### Post by RavUn on 2008-07-18
In my opinion, setting up the previously mentioned sftp server would be best.  If you want to have them be able to watch streaming videos on a website then use apache and embed the videos... but that could take a while embedding each video on a webpage and could use bandwidth if a few of them are streaming at once.  If you just want to have some "web storage" for your friends to be able to access your videos then i'd go the sftp route.  It's relatively simple to setup if you follow the instructions a few posts back.

---

### Post by mtgmutton on 2008-07-18
I set up the ssh... it WAS simple... am i not allowed to access it from the same computer it's hosted on? (yes I know this is probably a stupid question.) I tried and it said it couldn't connect because "connection refused by server".

---

### Post by mtgmutton on 2008-07-18
I tried this with WinSCP as well (on another computer). It gave me the error message "connection refused". Can I fix this?

---

### Post by RavUn on 2008-07-18
if you're sshing into the same computer then you could try ssh username@localhost.

if you're doing it from another computer on the network then do username@internal-ip and i you're doing it over the internet do username@external-ip... If you're doing it over the internet and your computer is behind a router you may need to forward port 22 from the external-ip to your computer's IP address.

Also, I had to install the openssh server before it'd work for me... just installing ssh didn't work, I don't think.  I could be wrong, though
```
sudo apt-get openssh-server

```

---

### Post by mtgmutton on 2008-07-18
I am behind a router. I tried forwarding port 22, like you said, but the connection times out (on the other computer). I'm not sure how to fix that...I also tried installing OpenSSH-Server, but it was already installed. When I forward the port (it's a lynksis), does the "application" field make a big difference?

---

### Post by RavUn on 2008-07-19
The application field does not matter.  Just make sure you put range 22 for the port range and have it forward to your computer's IP.  One mistake I made was I didn't check the box to enable the port forwarding... it's on the right side.  It took me 3 days to realize that.  I kept getting "connection timed out" until I checked that box.  If the box is checked then I imagine it's not forwarding right or there's a firewall issue.  Make sure your IP address hasn't changed or you're using something like dyndns.com if it does.

---

### Post by mtgmutton on 2008-07-19
OK. Does Linux have a built-in firewall or something? Because I haven't installed one...

---

### Post by mtgmutton on 2008-07-19
Hooray! i got it to work! Apparently, it doesn't allow SSH access without the application name being "SSH1". A bit weird, but that's ok because I can now access it from the other computer :D  Now my only question (warning: it may be silly) is this: will this run on startup? or do I have to run the "ssh" stuff manually?

---

### Post by NullHead on 2008-07-19
Don't worry, It ***should*** run on startup. When the machine is booted, it should load up on default. If you find it **not** loaded and you cannot connect next boot up, you can run this command: ```
sudo /etc/init.d/sshd start
``` and even if the ssh server IS loaded up, it'll make sure it's loaded anyways.

---

### Post by mtgmutton on 2008-07-20
thanks for all your help :D

---

