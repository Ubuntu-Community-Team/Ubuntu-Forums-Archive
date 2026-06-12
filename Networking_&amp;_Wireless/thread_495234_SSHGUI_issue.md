---
title: "SSH/GUI issue"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by purpzey on 2007-07-07
Hey all,

I have two machines setup running Ubuntu, one desktop, one laptop.

I setup my desktop as an ssh server so that I could access my files from my laptop. 

I can successfully connect to the server via CLI. However, if I add it using "Connect to server"
I am completely unable. 

I've tried using it with login name, with path, with one or the other...etc. Nothing...When I click on the folder
or select it from places I get nothing or a notification saying "Opening <ip>" which never goes away so I have
to hit cancel. I have left it for several minutes.

I've also tried using the location bar in nautilus to no avail. I have no idea what could be causing this.

There is no confusion with IPs since I am on a local network and the IP is 192.168.1.x so, it's easy enough
not to mess up. 

I would love some insight on this issue.

Thanks,
PurpZeY

---

### Post by ceargle on 2007-07-07
First off, if I'm misunderstanding your problem, please correct me. :)

You're trying to access files on your desktop from your laptop via SSH?

The easiest way to remotely access files on an SSH server is using SFTP. The command (to be executed from your laptop) will be as follows:

```
sftp <desktop_ip>
```

This will open up a command line that accepts similar commands as ftp: get <filename> to download files and put <filename> to upload.  I like to use a GUI sftp program like gFTP for accessing sftp shares.  

If you want to be able to mount the SSH share like a regular folder, you might want to take a look at this: [http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")

Please let us know if this helps or completely misses your question altogether :)

---

### Post by purpzey on 2007-07-07
Hey,

I looked that sshsf site and I'm not sure it will accomplish what I am looking to do. Let me explain in one sentence what I want to do, and then perhaps this can be alleviated much easier.

All of my mp3s are on my desktop. I want to be able to open XMMS (or whichever) on my laptop and create a playlist of these files so I can listen to them on my laptop as well as my desktop.

As I said, it's a local network, so the desktop is located at 192.168.1.10x and easy to find the ip. Someone in #ubuntu suggested I use ssh for this. If there is some simpler way, I'm OK with that. But I imagine that I have to mount the files to a folder on my desktop or somehow in my gui so I can drag the files in or use "Add." 

It seems to me that sshsf is going to get me access to the dir as a folder in CLI. I am not a total newb to Linux, but, I've never set anything like this up. If you think ssh isn't the right way to do this, that's fine or if you think it'd be better to use ssh then I need it to work via GUI -- I think.

I hope that clears up what I wanted to do, and how I was trying to do it. I am open to any direction.

Thanks!
--PurpZeY

---

### Post by ceargle on 2007-07-08
Following the sshfs guide will mount the files in a folder that you specify on your laptop, so that you can access them via CLI, Nautilus, XMMS, etc. - all over the ssh protocol. I think this would be exactly what you are looking for.

---

### Post by finer recliner on 2007-07-08
samba lets you mount partitions over a network, though its usually used in conjuction with windows boxes, it is easy for linux as well.

---

### Post by kevdog on 2007-07-08
samba or nfs is your answer.  For what you want to do, since you are working on a LAN, ssh is far too complex.

---

### Post by Herman on 2007-07-08
You probably just need to delete your .ssh directory in your /home/username folder.

In your /home/username folder click 'View'-->'Show hidden files', and delete your .ssh directory to the garbage bin, then open your  garbage bin and delete .ssh from your computer.
Don't worry, your computer will autonmatically regenerate a nice new fresh .ssh directory for you as soon as you make your connections again.

These two links should explain it,  [First Time Connection to an SSH Server]("http://users.bigpond.net.au/hermanzone/p11.htm#First_Time_Connection_to_An_SSH_server")    |     [If SSH refuses to connect]("http://users.bigpond.net.au/hermanzone/p11.htm#When_SSH_refuses_to_connect").

Regards, Herman :)

---

