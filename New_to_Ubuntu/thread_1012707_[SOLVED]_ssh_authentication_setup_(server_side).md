---
title: "[SOLVED] ssh authentication setup (server side)"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-16
I have been following some tuts on doing this but I am having trouble creating the authorized_keys_file

1 attempt

[email]user@host:/.ssh[/email]$ cat ~/.ssh/id_dsa.pub > ~/.ssh/authorized_keys
-bash: /home/pshootr/.ssh/authorized_keys: No such file or directory

2nd attempt

[email]user@host:/.ssh[/email]$ cp id_rsa.pub authorized_keys
cp: cannot stat `id_rsa.pub': No such file or directory

user@host:/home$ cd /.ssh
[email]user@host:/.ssh[/email]$

This shows I have the directories no? :confused:

This is the tut I want to follow. [http://dinamis.com/support/a-secure-replacement-for-ftp](http://dinamis.com/support/a-secure-replacement-for-ftp)

And this is the instuctions I am trying to for doing the server part

Generate an rsa key on the host that will be initiating the connection
$ ssh-keygen -t rsa
(just accept the defaults for the questions it asks)

You should either enter nothing as the pass-phrase or see the section
at the bottom of this document on ssh-agent.

Copy the public part of the key from the host where the keypair was generated
over to the destination host.

Create the authorized_keys file on the host where we will be logging into
$ cd .ssh
$ cp id_rsa.pub authorized_keys

Permissions must be restrictive enough
$ chmod 755 $HOME $HOME/.ssh

-rw-r--r--    1 abarclay wheel         224 Dec  8 23:35 authorized_keys
-rw-------    1 abarclay users         668 Feb 13 21:06 id_rsa
-rw-r--r--    1 abarclay users         606 Feb 13 21:06 id_rsa.pub

---

### Post by albinootje on 2008-12-16
> **pshootr said:**
> I have been following some tuts on doing this but I am having trouble creating the authorized_keys_file

1 attempt

[email]user@host:/.ssh[/email]$ cat ~/.ssh/id_dsa.pub > ~/.ssh/authorized_keys
-bash: /home/pshootr/.ssh/authorized_keys: No such file or directory

2nd attempt

[email]user@host:/.ssh[/email]$ cp id_rsa.pub authorized_keys
cp: cannot stat `id_rsa.pub': No such file or directory

user@host:/home$ cd /.ssh
[email]user@host:/.ssh[/email]$

This shows I have the directories no? :confused:

You made an interesting mistake.

~/.ssh and /.ssh are not the same.

~/ equals /home/your_user 

(and /.ssh is a directory which shouldn't be there, unless you're inside a VPS where the VPS software does use / as the home-dir because the working directory isn't really set like it normally is [OpenVZ does that])

It is possible that your user doesn't have the .ssh directory yet.
Try : mkdir ~/.ssh first.

---

### Post by pshootr on 2008-12-16
> **albinootje said:**
> You made an interesting mistake.

~/.ssh and /.ssh are not the same.

~/ equals /home/your_user 

(and /.ssh is a directory which shouldn't be there, unless you're inside a VPS where the VPS software does use / as the home-dir because the working directory isn't really set like it normally is [OpenVZ does that])

It is possible that your user doesn't have the .ssh directory yet.
Try : mkdir ~/.ssh first.

Hmm. Here is the instructions I am following.

Now login to the remote system here and make sure in your home directory there is a subdirectory named: .ssh (include the period '.' before the 'ssh'). You may need to create this directory. To see the file, you will need to type:
ls -al
The .ssh directory should be chmod 700, which looks like this in the first column of a detailed file listing:
-rwx------

If those are not the permissions on the .ssh dir, then set them by typing:
chmod 700 .ssh

May be there is a better tut some where..

---

### Post by pshootr on 2008-12-16
Ok I did mkdir ~/.ssh  Reading now to try and get my head wrapped around the next step lol

---

### Post by pshootr on 2008-12-16
Also says to do this, but here is what happens.

[email]user@host :~/.ssh[/email]$ chmod 700 .ssh
chmod: cannot access `.ssh': No such file or directory

---

### Post by mister_pink on 2008-12-16
You've given it a relative path to .ssh which is incorrect. What you've put is asking it to do the command on 
/home/user/.ssh/.ssh

which doesn't exist. Go up one directory (cd ..) or use an absolute path.

---

### Post by albinootje on 2008-12-16
> **pshootr said:**
> Also says to do this, but here is what happens.

[email]user@host :~/.ssh[/email]$ chmod 700 .ssh
chmod: cannot access `.ssh': No such file or directory

Try : chmod 700 ~/.ssh/

---

### Post by pshootr on 2008-12-16
> **mister_pink said:**
> You've given it a relative path to .ssh which is incorrect. What you've put is asking it to do the command on 
/home/user/.ssh/.ssh

which doesn't exist. Go up one directory (cd ..) or use an absolute path.

I do not appear to have a /home/user folder. And the instructions I have actually say to make .ssh in the home directory.

As far as chmod 700 .ssh  If I do this from /home  I still get chmod: cannot access `.ssh': No such file or directory

---

### Post by pshootr on 2008-12-16
> **albinootje said:**
> Try : chmod 700 ~/.ssh/

No error that time. Cool thats a start lol. Thanks

---

### Post by albinootje on 2008-12-16
> **pshootr said:**
> I do not appear to have a /home/user folder. And the instructions I have actually say to make .ssh in the home directory.

As far as chmod 700 .ssh  If I do this from /home  I still get chmod: cannot access `.ssh': No such file or directory

You can try this to find out whether you have a home directory :
echo $HOME

or also : 

cd ; pwd

---

### Post by pshootr on 2008-12-16
> **albinootje said:**
> You can try this to find out whether you have a home directory :
echo $HOME

or also : 

cd ; pwd

echo $HOME result


pshootr@LinuxFS:/home$ echo $HOME
/home/pshootr

---

### Post by albinootje on 2008-12-16
> **pshootr said:**
> 
pshootr@LinuxFS:/home$ echo $HOME
/home/pshootr

Okay, good then you should be able to use that.

---

### Post by pshootr on 2008-12-16
> **albinootje said:**
> Okay, good then you should be able to use that.

Thanks for your help. I need to go to bed finish this stuff tomorrow hehe. Thanks again for your help guys.

---

### Post by pshootr on 2008-12-17
How can I make sure that I have the correct directory structure? Every time I I try to make the authentication key file I get no such file or directory. 

Apparently I am supposed to have a .ssh dir in my home dir. And the keyfile is suposed to go there. I just can not seem to get it rite.

---

### Post by pshootr on 2008-12-17
Thanks goes out to all who helped me.

I finally got this straitened out. Here is a link to the tut i used, it is a great page. [http://www.unixwiz.net/techtips/putty-openssh.html#install](http://www.unixwiz.net/techtips/putty-openssh.html#install)

---

