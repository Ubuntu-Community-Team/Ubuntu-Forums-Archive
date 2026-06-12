---
title: "SSH no-password"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by Aikon- on 2007-12-11
**[COLOR="Red"]SOLVED:[/COLOR]** AGH why do I always solve these things immediately after posting the questions =/

Anyway, for anyone with similar issues here's what I had to do. The problem was: PERMISSIONS!!

After I made the permissions change to sarmitage's .ssh folder and contents so I could copy them to starbuck, I found that the auto-login no longer worked for sarmitage either. It appears your .ssh directory and its contents can't have too high of permissions, or they won't work.

So, I set the following folders to have the following permissions:  u:rw- g:--- o:--- (sorry, I don't know the number for this):

[LIST]
[*]/home/starbuck/.ssh/
[*]/home/starbuck/.ssh/authorized_keys
[*]/home/sarmitage/.ssh/
[*]home/sarmitage/.ssh/authorized_keys
[/LIST]

Now all works well; I can auto-login with both accounts ^^

**ORIGINAL PROBLEM:**

So here's the deal:

I have a webhost which allows SSH access. I can have as many users as I want; I am primarily interested in two: "sarmitage" and "starbuck". My username on my local Gutsy machine is "sarmitage".

I'm trying to setup SSH keys so that I don't have to enter my password to login via SSH (and subsequently, SCP and SSHFS).

So I followed the standard instructions: "ssh-keygen -t dsa", then copy id_dsa.pub to the remoter server's /home/sarmitage/.ssh directory and cat it into "authorized_keys". I did this with the "sarmitage" user first; logged back out of SSH and tried to log in again; Great! Logged right in without having to use a password (actually, I've been doing this for some time.. its only recently that I added the "starbuck" user).

So, now I'm trying to do the same thing with "starbuck"; can I use the same id_dsa.pub? I figured I could, so I started with the SCP step and copied the file to remote server's /home/starbuck/.ssh directory and cat'd it into "authorized_keys". Logged out to give it a try, but I'm still asked for my password.

I tried several times but couldn't get it to work. So, I made "starbuck" and "sarmitage" part of the same group, and made .ssh group-readable, and copied the files from /home/sarmitage/.ssh directly to /home/starbuck/.ssh (this is on the remote machine). I figured "the files are identical, so it should work now!"

NO JOY! I am still asked for my password for "starbuck" :(

The only difference I can tell between the two is that in one case, my username is the same on my local box as on the remote server, and in another case that username is different. (i.e. I use  "ssh myhost.com" for "sarmitage", while I have to use "ssh [email]starbuck@myhost.com[/email]" for "starbuck").

Any help would be greatly appreciated!

Thanks,

-Aikon

---

