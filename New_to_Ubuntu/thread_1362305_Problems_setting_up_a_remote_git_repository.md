---
title: "Problems setting up a remote git repository"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by ZeppelinJ0 on 2009-12-23
Hey everyone, looking for a little help as I've become pretty frustrated installing a remote git repository on my ubuntu server 9.10.

I'm following the directions posted here: [http://scie.nti.st/2007/11/14/hosting-git-repositories-the-easy-and-secure-way](http://scie.nti.st/2007/11/14/hosting-git-repositories-the-easy-and-secure-way)

The steps I've taken to get where I'm finding trouble are as follows:

1) I log in to my admin account (jdaily) on my "server" system where the remote git repositories will be held.

2) I create a folder called "src" in my home directory

3) I used git clone git://eagain.net/gitosis.git to download gitosis then use the python tools to install it

4) Next I create a user called 'git' by entering:
```
sudo adduser --system --shell /bin/sh --gecos 'git version control' --group --disabled-password --home /home/git git
```

5) Then I use "ssh-keygen -t rsa" to create a private and public key in /home/jdaily/.ssh/id_rsa[.pub]

6) From there I run the command 
```
sudo -H -u git gitosis-init < /home/jdaily/.ssh/id_rsa
```
This works fine

7) Here's where things go wrong.  At this point the instructions say to input ```
git clone git@MYHOSTNAME:gitosis-admin.git
```.

If I run this command from the server system (logged in as jdaily) I'm told to input a password for 'git.'  However no password is supplied nor required so I'm just given a "Permission Denied(publickey, password)" error.  If I try this from another machine, I'm given the same issue.


Sorry for the long-winded post, but does anyone have more detailed instructions on setting up and understanding a remote git repository? Or at least how to properly authenticate my SSH keys?

---

### Post by ZeppelinJ0 on 2009-12-23
Still having issues, so bumping

---

### Post by ZeppelinJ0 on 2009-12-23
One more bump.

---

### Post by matcram on 2010-01-11
bumping too :-D

i tried gitosis and gitolite and no chance with any of them despite the fact that gitosis is in the repos.

I guess that something differs in karmic ](*,)

---

