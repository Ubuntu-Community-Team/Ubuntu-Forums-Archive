---
title: "Simple Nub Question about servers/ftp"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by conviction on 2010-10-12
I installed ubuntu over the weekend and fell in love with it. However, I have a question about servers in general. If I want to host a server from my desktop (I only have one computer, my desktop) and just share movies and other stuff with a few of my close friends, what kind of server client should I use? I've read a ton of things about ftp and sftp and all of that, but I still dont know what I really want/need. I just want to have a client i cant run off my computer that I can easily host movies and have a few friends be able to download them. Thank you in advance :)

---

### Post by HermanAB on 2010-10-12
Howdy,

There are many ways to share data from the sublime to the ridiculous.  In order of increasing complexity:

FTP (Your grandfather's internet)
SSH (Swiss Army knife)
NFS (UNIX networking)
CIFS (Samba, Windows networking)

and you could even use Netcat (nc) or Socat if you feel adventurous.

I would suggest starting with FTP, since you never did anything like this before.  The common FTP servers work out of the box - you install it and it works.  People only have problems once they start to change the defaults.

NFS has a slight problem in that you have to install Services For UNIX on Windows machines (a free download from Microsoft).  A NFS server has ONE line of configuration and is therefore super easy to set up compared to Samba, which has hundreds of lines of configuration which interact with each other in unexpected ways.

---

### Post by Barriehie on 2010-10-12
> **conviction said:**
> I installed ubuntu over the weekend and fell in love with it. However, I have a question about servers in general. If I want to host a server from my desktop (I only have one computer, my desktop) and just share movies and other stuff with a few of my close friends, what kind of server client should I use? I've read a ton of things about ftp and sftp and all of that, but I still dont know what I really want/need. I just want to have a client i cant run off my computer that I can easily host movies and have a few friends be able to download them. Thank you in advance :)

Apache is pretty much the defacto for server software and no-ip, or some place similiar, can forward requests to your machine.  You get to select a domain name from their list and you setup apache/you machine to serve that name.  Here's a start:

[http://help.ubuntu.com/8.04/serverguide/C/httpd.html](http://help.ubuntu.com/8.04/serverguide/C/httpd.html)

---

### Post by conviction on 2010-10-12
My fault for not really specifying, but I didnt buy a server or anything. Im using the same desktop home computer I've had for the last 3 years, I just recently downloaded Ubuntu 10.04 (and 10.10 now) and wanted to try my hand at hosting a server from it. I'm just looking for an ftp client with lots of GUI and just a really simple concept I guess, nothing too complex.

---

### Post by Neezer on 2010-10-12
do you want a web server where your friends can access certain files that you have on your machine via an internet browser? If that is the case I'd recommend LAMP.

If you're just looking for file transfers I'd recommend ssh. with ssh you are much more secure than ftp, and it is still pretty easy to set up. I've set up a few ssh servers over the past 2 years, and there are great guides here on the forums.

So it depends what you are looking to do when you say "server" there are multiple solutions to the problem.

---

### Post by conviction on 2010-10-12
Yeah, LAMP the first thing you said, thats exactly what I'm looking for. Do I need to like pay to host a website for that? Or does the program just make the website like "ftp:198.xx.xx.xx.xx:xxxx" or whatever. But yeah, thats exactly what I'm looking for, people being able to upload files off my machine via a web browser.

---

### Post by HermanAB on 2010-10-12
Check out FileZilla server and Client.  It has GUIs for Linux and Windows. 

On Linux, you could simply use your file manager Nautilus for everything since it supports connections to all kinds of servers, but Windows file managers are usually rather cripple, therefore FileZilla.

---

### Post by Barriehie on 2010-10-12
> **conviction said:**
> Yeah, LAMP the first thing you said, thats exactly what I'm looking for. Do I need to like pay to host a website for that? Or does the program just make the website like "ftp:198.xx.xx.xx.xx:xxxx" or whatever. But yeah, thats exactly what I'm looking for, people being able to upload files off my machine via a web browser.

That's what I'm running. No, you don't need to pay a host, there are free redirectors like I mentioned before.  For an additional, around $10, a year they will mask it; i.e. people will go to yoursite.com and not see xxx.xxx.xxx.xxx:Port# in their browser address bar.  help.ubuntu.com should have LAMP installation instructions for your version.  It's not terribly complicated.  First time I did it I printed them out and checked them off.  Works fine.


HTH,
Barrie

[MySite](http://barriehie.redirectme.net/index.php)

---

### Post by Thrashdance on 2010-10-12
As HermanAB mentioned FileZilla is a pretty good and easy solution if you'd like to share between friends.
 One person (preferably with the most upload speed) sets up the server. Then he makes a folder for the shared files where he can choose whether users can read, write, delete dirs and files. Then your friends with the FileZilla client and the right password can download or upload there.
 That's how i did it in windows with my friends and it was really easy :) 
Shouldn't be harder in Ubuntu.

[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by pricetech on 2010-10-12
FTP is the simplest, and best supported cross platform.  SSH is a lot more secure and you can get an SSH client for windows.  I use WinSCP to securely move files from Linux to Windows boxen across the web.

---

