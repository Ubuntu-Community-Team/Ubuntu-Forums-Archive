---
title: "Apache: Could Not Bind to Address"
date: 2005-06-30
forum: Networking &amp; Wireless
---

### Post by pace_tua on 2005-06-30
Everything that was running fine an hour ago is still running fine, but when I went to add a new folder to my directory, it did not show up. I then remember to chmod it, and did so, but with no luck.

So I tried to restart apache, and was met with a surprise:
 ```
 * Forcing reload of web server  (Apache2)...
httpd (pid 8162?) not running
```
I then tried to start apache:
 ```
 * Starting web server (Apache2)...
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
 *able to open logs
```

I have tried a few things, such as only including the port number in the ports.conf file, but nothing seems to work. As I said, the files and directories I had in place previously still work.

Help.

---

### Post by pace_tua on 2005-07-01
Okay, I have it working now- forgot to use "sudo".

However, I still recieve a 500 Error when trying to access new files and directories.

So I still need help :)

[edit]
Found the problem. I did what I should have done, check the logs. Well, it looks like folders won't display if your .htaccess files are using an unsupported command- the Rewrite Engine in this case.
[/edit]

:-\"

---

### Post by brownrl on 2006-10-30
Actually,

I get this problem too... However, for me its not .htaccess files. I turned off all of the SSL and I still get the same error but on port 80 instead of 443.

Someone mentioned that I should create a directory /var/www/log however that does not seem to work unless it needs to be owner by somone other than root?

The odd thing is if I let the apache run for more than an hour or so then it will happen that I can't restart it. If I only let it run for 5 minutes or so no problem...

What I do see when I try to restart apache is a left over apache process running like mad using 95% CPU and I have to kill -9 it.

Then I can start apache.

I think that i has to deal with log files and shutting down too slowly or getting hung while closing the logs.

Any suggestions?

---

