---
title: "script for setting proxy environment variables"
date: 2005-09-01
forum: Networking &amp; Wireless
---

### Post by wylie348 on 2005-09-01
Can anyone tell me now to automate the process (using the click of a script or somesuch) of setting the http_ and ftp_proxy variables?  I am getting tired of having to open a terminal and type in the export commands everytime I am behind my work proxy server?
Thanks!
 O:)

---

### Post by cwaldbieser on 2005-09-01
[QUOTE=wylie348]Can anyone tell me now to automate the process (using the click of a script or somesuch) of setting the http_ and ftp_proxy variables?  I am getting tired of having to open a terminal and type in the export commands everytime I am behind my work proxy server?
Thanks!
 O:)[/QUOTE]
Open up an editor and edit your ~/.bashrc file.  Add the lines:
```

export http_proxy=http://proxy-addr
export ftp_proxy=http://proxy-addr

``` 
for good measure, you might want to set "HTTP_PROXY" and "FTP_PROXY" as well-- I seem to recall some programs look for the uppercased versions.  Make sure you don't put spaces around the equal sign!

Now whenever you open a new shell, those variables will automatically be exported to and sub-shells.  You may have to restart your GUI (if you are using one) to get this to work from the menus.  The reason being that your desktop started up initially without these variables, so it won't pass them on to its child shells until it is restarted.

---

### Post by wylie348 on 2005-09-03
Thanks for the help - I actually got off my butt and looked around concerning making scripts.  I just did pretty much what you said (including chmod'ing the script), but made it a seperate file that I only run when at work (and need to use a proxy).  Thanks again!

---

