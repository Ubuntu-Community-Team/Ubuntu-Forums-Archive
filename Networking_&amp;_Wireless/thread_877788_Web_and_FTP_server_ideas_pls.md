---
title: "Web and FTP server ideas pls"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by skozzy on 2008-08-02
Ok, before jumping to installing software or messing about with config etc. I figure to ask some questions and get some ideas where to start or what I im in for.

I have a spare computer doing nothing and a friend that wants to try and learn html, on the same hand I want to improve my skills on html and learn more about what I can do with html and scripts etc.. And since linux has a bunch of nice free software to play with I figured I would look in to setting up apache2 and anything else needed for use two to use this spare computer for just that.

I have a decent high speed adsl2+ package with a fixed IP address, I am behind my router (192.168.1.x) and my friend is on the outside of the router (dynamic internet ip address). If I want to have apache2 running for us to play with and be able to remotely access our own site served off it, what would be the prefered apache2 setup and what would be the prefered way for us both to access our own web pages (websites) from it and also then be able to view our sites from the internet. I don't want to bother with registering a domain name so I want to stick with a format like [http://123.123.123.123/my_website](http://123.123.123.123/my_website) and [http://123.123.123.123/my_mates_website](http://123.123.123.123/my_mates_website)

My spare computer is set up with a fixed IP of 192.168.1.150 and the router is configured to forward port 80 to 192.168.1.150 I also configured port 17171 for FTP to that computer as well. The current default apache2 config is visable via the web so I know that is working.

It's now down to what method to choose to config apache2, and what method to allow us both access from remote computers. And ultimatly I prefer a set up that allows instant viewing of our uploaded content without have to chmod or chown files and folders. So I guess you call it a stand alone config that just works on it's own.

I looked at the UserDir option in apache2 and find the file/folder permisions a problem with many people, even if they upload content from ftp they must be there at the webserver to chmod or chown.

I would like to stick to apache2 for the web server and if FTP is the prefered method to upload content to the server then what is my best choice for a ftp server for it.

Well, I look forward to comments and ideas from you more experienced lot. Also to add to the info supplied, I am fairly new to linux and the terminal, I have been brainwashed with MS Windows for too long, so keep that in mind.

---

### Post by Victormd on 2008-08-02
I have a similar but simpler question. I just want to setup an FTP server. I've read a few threads (not completely - too many posts). Skozzy, these might help you:
[http://ubuntuforums.org/showpost.php?p=680702&postcount=81](http://ubuntuforums.org/showpost.php?p=680702&postcount=81)
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

The threads discuss the use of proftpd but I'm not 100% sure about this and don't want to risk compromising security. Any suggestions for a simple method for creating a secure FTP server??

---

### Post by skozzy on 2008-08-02
I have read both of these links you show here during the last week.

 Problems extending from this which I have also read is file permisions on uploaded files to the websites is not compatable with allowing anyone but the logged in account from viewing the files in a web browser (on the server machine) unless you are logged in on that account and chmod the uploaded files.

---

### Post by Victormd on 2008-08-02
I tried using it and I'm sure I set something up wrong because even though I could access my ftp server, I could not see any of the files! Ultimately I just installed removed the package and I'm trying to see if I can find an alternative!

---

### Post by disabled.user.profile.asdf on 2010-02-25
:-(

---

### Post by BigRichOfYork on 2010-03-18
Hi, I am in the same position as you were 18 months ago. I am setting up a development server for my students to build a web site and I want them to be able to upload pages with ftp. I can chmod on the server to make the uploaded files available via the apache server, but newly uploaded files have the wrong permissions. Even if I set group and other permissions on the /var/www folder the uploaded files don't inherit the permissions. Did you ever manage to find a solution?

-Rich

---

