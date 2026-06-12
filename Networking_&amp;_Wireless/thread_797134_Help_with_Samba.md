---
title: "Help with Samba"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by oxsyn on 2008-05-17
... I've been trying to get samba running for a couple weeks now.  I'm really frustrated.  It's a server installation, so there is no GUI, it's all CLI based.

I've been using the following guides to try to get this working:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add.2Fedit.2Fdelete_network_users)

Based, on this, I've modified two parts of my smb.conf file, first:
> 
; security = user

Is modified to:
> 
  security = user
  username map = /etc/samba/smbusers


And I've appended the following lines to the file:
> 
[Library]
path = /mnt/library
writeable = Yes


I've also created the smbusers file, which contains a single line:
> 
system_username = "f4rr4r"


I then created the user account & set the password:
> sudo smbpasswd -a f4rr4r
and then enabled the account:
> sudo smbpasswd -e f4rr4r

Then I restart the server.

Now, from my other box, I type:
> smbclient -l hawking
But the share isn't there!  I can see the default printer share, but library is not there!

If I try to connect, like so:
> smbclient \\\\hawking\\library
I get the error message:
> 
Domain=[HAWKING] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_ACCESS_DENIED


... I'm doing something wrong.  I have no idea what it is.  Please, please, please help.

Thanks.

---

### Post by jetsam on 2008-05-17
I think there's a problem with your username map.  You may have taken the instructions too literally.  

The entries in the smbusers file should follow this format:
```
<server side username> = <client side username>
```

Most commonly, this is used to map invalid Windows usernames with spaces in them to valid Unix usernames on the server.  If your username is the same on the client and server and there aren't any spaces in it, you can just take the **system_username = "f4rr4r"** line out entirely.  

I think what's happening now is that you're trying to connect from the client as user f4rr4r, and Samba is then trying to authenticate on the server as user system_username.  There isn't a user named system_username, though, so you get permission denied.

---

### Post by oxsyn on 2008-05-17
> **jetsam said:**
> I think there's a problem with your username map.  You may have taken the instructions too literally.  

The entries in the smbusers file should follow this format:
```
<server side username> = <client side username>
```

Most commonly, this is used to map invalid Windows usernames with spaces in them to valid Unix usernames on the server.  If your username is the same on the client and server and there aren't any spaces in it, you can just take the **system_username = "f4rr4r"** line out entirely.  

I think what's happening now is that you're trying to connect from the client as user f4rr4r, and Samba is then trying to authenticate on the server as user system_username.  There isn't a user named system_username, though, so you get permission denied.

Holy jesus.  I had no idea, that wasn't specified anywhere, and yes, it's working now - uberthanksman.

An additional question: Obviously, the smb users are not stored in the /etc/passwd file, like other users are.  Where are they stored?  I.E. when I run the *smbpasswd -a username* command, what file(s) does this modify?

---

### Post by jetsam on 2008-05-17
Glad it helped!

...and good question.  I had to Google the answer.  They're stored in /etc/samba/smbpasswd.  I've never looked at the file before; the usernames are plain text, but the passwords aren't.  

I think it's for security reasons that Samba keeps a second password database.  Since users need accounts on the server, having a different password means they only have to be given the samba password.  Admins in professional settings then don't have to give users direct access to the server accounts.  I think it's something like that.  

Those docs you were using are really sparse.  
The classic forum how-to on Samba is this one by Stormbringer:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer+samba]("http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer+samba")

There's also excellent documentation at the Samba website.  It's kind of too much of a good thing, but there's a lot of info there:
[http://us1.samba.org/samba/docs/]("http://us1.samba.org/samba/docs/")

---

