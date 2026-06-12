---
title: "Do I need to start all over again"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by macmike on 2010-05-09
Well frustrated. I thought I would have this all going by now. I want to host two Web sites so I understand that will be Name hosting. Right now I have my Domain name wilmingtoncoc.com forwarded to my public IP address and I can see it on the Internet. When I shut the box off I get an error that it can't be found so I know that is working.  I have tried to install vproftpd and can't get anywhere. Also tried to get Webmin. Is it time to blow this install away and start again. I have two website I want to host 1. is Wilmingtoncoc.com and the other will be Mikealrhughes.com plus I need to host my mailing list through mailman called Biblematters.net. So I guess that is three sites. Any way is there a step by step process anywhere of what to do to get this all to gel. I have ordered a couple books from Amazon. I need an Ubuntu guy close to me somewhere that can help me get things running. Any help appreciated. I can even call on my magic jack line to be walked through even. 

Where do I need to go and what do I need to do? I want WordPress on the Wilmingtoncoc.com site and my Mikealrhughes.com site is through Dreamweaver using FTP. 

Thanks for letting me vent my frustrations. Long nites killing me on this thing. 

Mike

---

### Post by Penguin Guy on 2010-05-09
I'm in the same boat as you - can't get anywhere with Apache.

---

### Post by Penguin Guy on 2010-05-15
You could try installing [XChat]("apt:xchat") and ask the guys on the #httpd channel - I found them very helpful while setting up my test server.

---

### Post by hannaman on 2010-05-15
Have you checked the documentation on Apache's site?
Apache supports virtual hosts, so you can easily host multiple domains on a single server.  Some examples of this are at [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html).
You could use different ports for each webserver to listen to.  For example, if Wilmingtoncoc.com listens on port 80; then Mikealrhughes.com could listen on port 8080.
Or you set up virtual interfaces on your network connection and have each webserver listening on port 80 on its own IP address, but use port forwarding on your router to forward port 8080 to port 80 for the second domain for example.

---

### Post by macmike on 2010-05-15
I haven't touched the other two websites yet. I am trying to get the wilmingtoncoc.com going so I can figure out how to get WordPress going and get content back up. I have tried all of that so I can't figure out what is wrong. I wish there was a fresh set of eyes close to me to look at all of this. Problem is I can't get into the forum from the Linux box so I it is hard to copy and past files since I don't know Linux well enough to know out to get a txt file to a flash drive.  I have a ream of paper printed of things I have found online talking about Virtual hosting.  I was hoping it would have been going by now. DOS wasn't this hard. That is why I wish someone could do an iso of their Ubuntu server and I could then be told go into this file this way. Not enough to tell me to go into the file but how do I go into that file. Then make the changes and it work. 
When I get the wilmingtoncoc site going I will tackle the mikealrhughes.com site with the cgi-scripts I have to get and try and get ftp going. Right now I can't get into the linux box except through the box itself. Would love to be able to get into it and manipulate it from one of my other computers even.

They tell you to check config.cf file or some other file, but don't tell you where you will find that file or how to edit the file. 

Thanks for any help and ideas.

Mike Hughes

---

### Post by hannaman on 2010-05-15
Since it looks like you have internet working, have you tried installing an ftp server from the repositories such as proftp?
```
sudo apt-get install proftpd
```
Does the install error out?  Do you have any firewalls running on your server or router that might block the ftp ports - 20 and 21?

Your flash drive should mount under the /media directory.  You can do an ls in the /media directory before you insert the flash drive and again after the falsh drive is inserted to figure out which one it is.  Once you find the flash drive, you can copy a file to by using the cp command:
```
cp *filename.txt* /media/*flash_drive*
```

As for editing files from the command line, I just use vi.  There are tons of vi guides and cheat sheets on the internet if you are not familiar with the syntax.

Finally most config files are located in /etc/*application*.  So to edit config.cf you would type:
```
vi /etc/*application*/config.cf
```
If you can't find the config file under /etc, you can always search your system for it using the find command:
```
find / -iname config.cf
```
Where "/" is the starting path (in this case the root of the filesystem - "." would be current directory, etc.).

Hope this helps.

---

