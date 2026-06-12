---
title: "Accessing the server"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by p_quarles on 2007-06-09
Caveat: I have no real need for a server of any kind, I'm just trying to figure out how to do, for my own education.

I think I've done everything right so far. I followed a tutorial that led me through the installation and configuration of SSH server, Samba. I've created a public share, added myself as a user, and set my password. The server has a name and a static IP address, both of which will find the machine upon a query.

Here's the thing, though: I can connect through SSH and modify anything I want to, locally. What I can't do is transfer anything between the client and the server. I've used the "scp" command (from both machines and in both directions), and I've mounted the remote drive through various protocols. It even asks for and accepts my password, but then tells me I don't have permission to write to the drive. 

This is the first time I've tried anything like this, and I'm actually quite pleased that I've even managed to establish the SSH connection, but I'd like to get this to work fully.

Other info:
Server specs: Dell w/ Intel Pentium 4, 1.8 GHz, 256KB cache, 384 MB memory
Client: HP w/ 2 Pentium Ds, 2.8 GHz, (unsure about cache, but it's fast) 1 GB memory
Server software: Ubuntu 7.04 server edition, DNS installation
Client software: Ubuntu 7.04, Windows Vista

More information gladly provided upon request. Thanks in advance for any help.

---

### Post by etechship on 2007-06-09
You need to make sure the drive you want to write to is writable, not just read-only. You can check to see if your partition that you want to boot is being mounted writable by opening /etc/fstab and looking for your partition, then under <options> make sure is either has default or rw.

/etc/fstab is the file that Linux reads when it boot and it mounts all those on start up.

---

### Post by croto on 2007-06-09
Can you post the scp command line you issued?

---

### Post by p_quarles on 2007-06-09
etechship: Thanks, that helps. The remote drive isn't on fstab at all. Is there a way to make it read/write upon a manual mount, or do I need to add a line to fstab? (I think I know where to find a template for this line)

croto: I was trying to copy an iptables script to the server. I entered
```
scp [user]@192.168.1.65:/home/[user]/fw-builder_projects/fw1.fw /etc/firewall/fw1.fw
```

This followed an example in the server setup tutorial I'm using.

---

### Post by croto on 2007-06-09
Ok, I see the problem. You're trying to transfer a file from the remote computer to the local directory /etc/firewall/ . You are not being able to write there because only root can write there. The solution would be becoming root first:

```

sudo bash
scp [user]@192.168.1.65:/home/[user]/fw-builder_projects/fw1.fw /etc/firewall/fw1.fw

```

You'll be asked for a password when you run sudo, enter your local password. When you run scp you'll be asked for [user]'s password. To go back to the normal user, type exit.

---

### Post by p_quarles on 2007-06-09
croto: Okay, that worked partly. It copied the file to the server, but now it won't run. My tutorial tells me: "Even though it will have an .fw extension, this file is actually just a shell script that you can run in the normal way." But, when I try to run it, it tells me "command not found."

Also, I tried numerous times to run the same scp command, both with and without sudo. If you've got the time, can you explain the difference between "sudo [command]" and "sudo bash / [command]". I'm trying to understand this stuff. 

Thanks in advance.

EDIT:
1) I realized immediately after I wrote this that "sudo bash" logged me in as "root@192.168.1.5". Got it.
2) But still, how does that work? I edited the SSH config file to disable root login. I feel like I'm missing something.
3) The specific command I used: "sudo /etc/firewall/fw1.fw" | reply "command not found"

---

### Post by croto on 2007-06-09
Yes, when you run sudo bash, you set the current user to be root. But then, when you run ```
scp [user]@192.168.1.65:/home/[user]/fw-builder_projects/fw1.fw /etc/firewall/fw1.fw
```, you are going to log as user [user] on 192.168.1.65 (which means that you'll be able to access only the files that [user] can access on the remote computer), while on the local computer you still are root, so you can write anywhere on the local system. If I understood correctly, [user] is not root, right? So to answer your question, root is not loging onto the remote computer but [user]. You could check that ssh root@192.168.1.65 or scp root@192.168.1.65:..... shouldn't work.

Now, with respect to EDIT 3 (script not running), I think the problem is that the file doesn't have the right permissions. In order to run any file, such file must have executable permissions. You can check that if you type **ls -l /etc/firewall/fw1.fw** it's going to show something like 

 -rw-r--r--  1 root root        24 2007-05-28 03:08 fw1.fw

In this example, the first rw means that the owner of the file (root) can read and write, the second r means that the members of the group root can only read the file, and the third r that any other user has only read permissions. To set executable permissions run:
```

sudo chmod a+x /etc/firewall/fw1.fw

```

This allows all users to run the script.

---

### Post by p_quarles on 2007-06-10
croto: That did the trick. Thank you so much for your help. I still don't quite understand what exactly this did, but now I can go study the mans for bash and chmod.

---

### Post by croto on 2007-06-10
Hey, I'm glad it worked! The man pages are usually quite cryptical... I'd recommend any book on Unix. Good luck!

---

