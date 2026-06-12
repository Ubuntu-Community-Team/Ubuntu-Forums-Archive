---
title: "help with ftp server"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by frankups1 on 2009-03-22
i have had a webserver up and running for about 6 months. everything worked with out problems, ftp, email, vpn, apache....
last week my hard drive failed, and no nothing was backed up (i know, lesson learned!) well now i am trying to get everything set back up again and i have everything running except for the email and ftp servers. i have tried proftpd and vsftpd, and with both i get the same error when i try to log in from my mac, "some data in [ftp://mydomain.com](ftp://mydomain.com) could not be read or written." and when i try to connect from an ftp program it says "unable to connect to the server [ftp://mydomain.com](ftp://mydomain.com), unable to upload to the server." im guessing that it is something really simple that im overlooking. 
the one thing that is different from when my server was working is that now i am using ubuntu server not desktop, but i dont think that would cause ftp to not work? 
thanks in advance:(

---

### Post by Xiong Chiamiov on 2009-03-23
Follow one of [the guides](http://www.google.com/search?hl=en&q=ftp%20ubuntu&aq=f&oq=) and report back any problems you have.

---

### Post by hyper_ch on 2009-03-23
are you sure you need ftp server? Wouldn't sftp/scp work also? IMHO that's much simpler to setup.

For running a mailserver I'd look at the perfect howtos over at [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by vsiege on 2009-03-27
**hyper_ch**
I too was looking for a way to manage ftp accounts. I would like to find a web based tool for management (other than phpmyadmin, as I don't find that as friendly). Everything at howto for virtual hosting is for regular FTP instead of sftp, plus the administration is done with phpmyadmin. 

1. Do you know where i could find virtual hosting for sftp (im assuming sftp app will also revert to ftp for users who dont have sftp application)? 
2. I have sftp working right now but am not sure which server is running it (its not vsftpd becuase i shut the service off and stopped it using CLI cmd) could you give me a command or a place to look that would let me know which server/app is running it??

I am running 8.10 server edition

---

### Post by hyper_ch on 2009-03-28
well, I'd use mysecureshell and system users to set that up... I don't know what you mean by "administration". How much administration you want. what do you want to achieve?

---

### Post by vsiege on 2009-03-28
> I'd use mysecureshell and system users to set that up
mysecureshell? i've never used that. I really would like to virtual hosting instead of user accounts. This way I can log in over the web (using a web browser) and add, create, delete, edit and set file upload and download privileges.
This gets me on to your second question:
>  I don't know what you mean by "administration"
The administration of the sftp and ftp accounts would be through a web browser. I have seen a bunch for ftp but not sftp.

---

