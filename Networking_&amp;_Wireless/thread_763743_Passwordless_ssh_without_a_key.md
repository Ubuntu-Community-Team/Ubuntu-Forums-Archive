---
title: "Passwordless ssh without a key"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by Dooley on 2008-04-23
Hi there,

I was wondering if anyone might know how to create an automated passwordless ssh connection, without using keys.  The server I'm connecting to doesn't allow the use of ssh keys because they aren't entirely secure. So I'm looking for a way around this.

Thanks!

---

### Post by DrCoolSanta on 2008-04-23
isn't the command
ssh *server*
enough?

---

### Post by Dooley on 2008-04-23
You still need to put in a password, which isn't much use when I want to automate the ssh connection. 
I want it to run in a cron job.

---

### Post by DrCoolSanta on 2008-04-24
Its not safe anymore, but if you have access to the server physically, you could set up RSh and create a file ~/.rhosts with the host and the user and his password fo paswordless access.

---

### Post by kevdog on 2008-04-24
There is a way to run a script that actually answers questions (if you know the questions beforehand) at the command line. For example, it would be possible to write a ftp or ssh login script, where the script could pass the username and password to the login prompt since it would only send these parameters after being prompted.  There was a post about this about 3 months ago.  For the life of me I can't find the post and I dont remember the bash scripting command that you type in the script that enables this feature.  Perhaps a thorough search of the forums or asking LaRoza since he is really good at scripting would help.  This way ssh would be much more secure than running it wide open.

---

### Post by DrCoolSanta on 2008-04-25
if you can do that, you just have to write
> 
#!/bin/sh
ssh **server** -l **login**
**password**

in a file with executable permissions like 755

---

### Post by Wim Sturkenboom on 2008-04-25
> **Dooley said:**
> ...
The server I'm connecting to doesn't allow the use of ssh keys because they aren't entirely secure.

Just out of curiosity:
Do you have any reasoning or explanation for that?

---

### Post by Patsoe on 2008-04-25
Uhm, passwordless without a key = no authentication at all!
Or am I missing something?

---

### Post by DrCoolSanta on 2008-04-26
You are not, that's what I tried to tell him earlier.

---

### Post by encompass on 2008-04-26
ssh is pretty dang secure.  And there is no way to really do an ssh connection without  keys. (They are used to encrypt your conversation)  With out them, you might as when tell the whole world your password and ever peice of information to eager crackers.
If your IT department tells you ssh keys are not secure, they are nuts.
I won't tell you a solution for something like that even if I knew it.  It's not morally right to let someone do so. sorry

---

### Post by Zack McCool on 2008-04-26
> **Dooley said:**
> The server I'm connecting to doesn't allow the use of ssh keys because they aren't entirely secure. 

Huh?

---

### Post by Patsoe on 2008-04-26
> **encompass said:**
> If your IT department tells you ssh keys are not secure, they are nuts.

Hehe, actually the computing information pages where I work also say something like this: "We do not support RSA-only as this is equivalent to having a password stored in a file."

...which is true if you don't trust your users' home machines. But then, really why would you trust them with remote login if you don't trust their machines?

---

### Post by Dooley on 2008-04-26
Sorry the admin of the unix server im running stated that using public-private keys to access the server without using a password. 

I however disagree but what can you do.

I was looking for an alternative to this, i'll give what was suggested a go. 

Thanks!

---

### Post by Dooley on 2008-04-26
> **DrCoolSanta said:**
> if you can do that, you just have to write

in a file with executable permissions like 755

I don't think this approach would work, ssh doesn't take arguments through STDIN.

---

### Post by Monicker on 2008-04-26
Hrmm.  I'm still confused.  RSA keys can be secure or insecure.  I know people who have used key authentication without any password on the keys.

With a strong password on the keys, I don't see how you can say RSA key authentication is not secure.  Somebody would have to have the appropriate key and also know the password to use that key.

Oh well.......

---

### Post by Dooley on 2008-04-26
To be honest, I'm sure most would know more about this than myself.
If there no real solution to this I'll try bug the admin a bit more. 
:D

---

### Post by Patsoe on 2008-04-26
> **Dooley said:**
> To be honest, I'm sure most would know more about this than myself.
If there no real solution to this I'll try bug the admin a bit more. 
:D

Sounds like the most secure solution :)
You could ask him to configure ssh so that the shell only allows the commands that your scripts need to run, and nothing else.

---

### Post by DrCoolSanta on 2008-04-27
> **Dooley said:**
> I don't think this approach would work, ssh doesn't take arguments through STDIN.
Well I had the idea that it wouldn't work but since the one above me said that earlier, I just gave you the script.
Did you think about SSHing into that machine and logging into it and then install RSH, I know how to configure RSH to allow passwordless login, But then RSH is even less secure than SSH but if you accomplish what you want, then you'd get something equivalent to passwordless RSH connection.

---

