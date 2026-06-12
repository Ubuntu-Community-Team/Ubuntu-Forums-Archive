---
title: "Prevent ssh- and ftp Bruteforce hacking"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by perixx on 2008-02-17
Hello!

I'd like to know how to change my ssh- and ftp ports to non-standard ports and how to set the standard delay time between login attempts on these ports, as well as how to limit the overall number of access/login attempts there... 
who can help?

I found this thread here, but it didn't quite answer my questions:
[http://ubuntuforums.org/showthread.php?t=159047]("http://ubuntuforums.org/showthread.php?t=159047")

perixx

---

### Post by jhetrick62 on 2008-02-17
Changing the port that the services listen on is easy.  If using openssh server, edit the /etc/ssh/ssh.conf file and change the port number then restart the service.

Depending on ftp you are using, if vsftp then /etc/vsftpd/vsftpd.conf file and do the same.

I would seriously explore using denyhosts and getting that set up properly.  It does a nice job of locking out un-wanted log-ins and blocking their IP addresses.

Jeff

---

### Post by perixx on 2008-02-21
Thanks, Jeff... I'm gonna try this out... is it self-explanatory or does it need any setup?

perixx

---

### Post by perixx on 2008-02-25
Well, jhetrick62, 

I've changed my gftp and ssh ports now and installed 'denyhosts'; will the program detect several login requests from the internet automatically and react accordingly? Or do I have to set up sth. first?

I thought there's an option to deny incoming connection requests to that services completely... would that be a good method to ban bruteforcing attacks in general?

perixx

---

### Post by SpaceTeddy on 2008-02-25
changeing ports does NOT protect you against anything, it just obscures a little. But > security by obscurity does not work

i would suggest either the deny host, or an iptables setup that only allows a certain amount  of connection initiations per second (say one ?). bruteforce does then not work anymore, since even one second per guess is way to slow to be able to do a bruteforce attack on anything.

this article describes more about it
[http://www.debian-administration.org/articles/187]("http://www.debian-administration.org/articles/187")

hope that helps...

---

### Post by jhetrick62 on 2008-02-25
Perixx,

There is a config file for denyhosts.  In Fedora core it is located in the /etc directory and it's denyhosts.conf.  Somewhat self explanatory and I set mine up 3 years ago so you may want to google a howto on it if you need added assistance.

Yes you can block entire services in the hosts.allow and hosts.deny file.  In the hosts.deny file, I keep vsftpd: ALL and then only add in specific ip addresses into hosts.allow.  This blocks all ftp except for the ones that I specifically allow.

I also have denyhosts set up to automatically add ssh users who fail their login 3 times within 5 mintues, to the hosts.deny file which effectively blocks them until the reset period is over, which I have set for 25 days.

Make sure you keep a backup account for yourself, as if you log in improperly 3 times in 5 mintues, you won't get access either from where ever you are.

Goodluck,
Jeff

---

### Post by perixx on 2008-02-25
Hey, thanks for that :)

> Yes you can block entire services in the hosts.allow and hosts.deny file. In the hosts.deny file, I keep vsftpd: ALL and then only add in specific ip addresses into hosts.allow. This blocks all ftp except for the ones that I specifically allow.

Will this mean, that every time I want to download from an ftp server, I'll have to allow it's ip-address first? That would be odd! Too unpracticable...

Isn't there some sort of good frontend for denyhosts? I don't like having to tinker around in config files manually all the time :) 

perixx

---

### Post by jhetrick62 on 2008-02-25
Perixx,

It depends on your habits.  I don't ftp very frequently, so for me, I just ssh into the box, open the ip I'm coming from and then exit out and send the ftp.  It stays open indefinitely if your user has a static ip address.

You could just leave it open and leave it to block anyone with (3) bad attempts, BUT, I choose not to as ftp requests are plain text requests, meaning your username and password can be seen.  SSH requests are encrypted requests so they are much safer.

If you do want to leave it open, I suggest that your ftp server be chrooted (mine is) and that you use a login that has no shell access.  That way if your user / password are scanned and compromised, they at least don't have a shell to log into to via ssh into your box.  Then only use this non-shell user for open ftp access.

There may be other solutions, but this one works for my purposes.

Goodluck,
Jeff

---

### Post by perixx on 2008-02-25
Hello Jeff,

> I just ssh into the box, open the ip I'm coming from and then exit out and send the ftp. It stays open indefinitely if your user has a static ip address. To clarify: you open a ssh tunnel TO a server somewhere (using the password it requires) and then request that server to send you the file?

> You could just leave it open and leave it to block anyone with (3) bad attempts, BUT, I choose not to as ftp requests are plain text requests, meaning your username and password can be seen. SSH requests are encrypted requests so they are much safer. Do you want to tell by this, that every time I do some ftp download (even without any login procedure required), my ROOT password is transmitted?! Or do you mean the login password for a specific ftp server, to which I have a password for?

> f you do want to leave it open, I suggest that your ftp server be chrooted (mine is) and that you use a login that has no shell access. That way if your user / password are scanned and compromised, they at least don't have a shell to log into to via ssh into your box. Then only use this non-shell user for open ftp access. I'm not perfectly sure if I understand what you mean by chrooted. I wouldn't know how to do this or to restrict shell access for ftp logins, too. Could you maybe give an example?

Basically, I only download sometimes from ftp - via simple links - (alternate to http), because it's faster or the only option availible - especially for large files....

perixx

---

### Post by jhetrick62 on 2008-02-25
Perixx,

If you are remotely accessing YOUR server via ssh or ftp, this is where you need denyhosts to block other un-wanted attempts to access your system.  I assume that is what you wanted as you asked about changing your ports to non-standard ports.

> To clarify: you open a ssh tunnel TO a server somewhere (using the password it requires) and then request that server to send you the file?

No, I open an ssh tunnel so that I can modify the hosts.allow file with Vi or Nano.  I then add the ip address that I would like to grant ftp access to my server.  Usually the one I'm accessing from but occasionally I allow others.  I then save the changes, exit out of the ssh shell and then I  can initiate the ftp session and get or put what I wanted to.

> Do you want to tell by this, that every time I do some ftp download (even without any login procedure required), my ROOT password is transmitted?! Or do you mean the login password for a specific ftp server, to which I have a password for?

I mean that ANY password and/or username that you use with a standard ftp command is transmitted in plain text.  Usually not your root password as most ftp servers are set up to not allow a root login.  BUT, if you did allow root and used it, yes that would also be plain text.  I would not allow root login via ssh just to be safe.
> 
I'm not perfectly sure if I understand what you mean by chrooted. I wouldn't know how to do this or to restrict shell access for ftp logins, too. Could you maybe give an example?

Chroot is an option on most ftp server config files.  It allows you to make the user's directory the "root" directory for that session which means that they can't go backwards into your file structure.  If your ftp directory for the login jeff was /mnt/jeff and it was set to chroot, then the user could not move "up" into /mnt or any other diretory above /mnt/jeff, only directories below /mnt/jeff/somedirectory.

Restricting shell access mean creating a user such as "remotejh" in which when you define the user, you assign /bin/null or /bin/false to be their shell, rather than /bin/bash.  As  null and false are not valid shells, they can't actually log-in to a terminal session, only something like ftp and possibly an http session (I don't have experience with the http sessions).  When accessed with ssh or telnet, it will fail.

It sounds to me like you are working on your box and requesting ftp downloads from other individuals, is that correct?

I hope this has shed some light on this for you.

Jeff

---

### Post by perixx on 2008-02-28
Hello Jeff!

> I hope this has shed some light on this for you.
Er... partly. Your answers seem to tell about how to secure 'some fileserver' of mine somewhere in the net, where I share some files with the public to download, right?

Well, I'm not having such a thing yet. All I want to do is to secure my own PC, which I'm working here. Since Ubuntu has ssh and ftp server and client installed - that's what I want to protect from bruteforce attacks...

perixx

---

