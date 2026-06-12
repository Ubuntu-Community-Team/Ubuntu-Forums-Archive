---
title: "ssh and xauth problem with encrypted home"
date: 2016-05-16
forum: Networking &amp; Wireless
---

### Post by flucoe2 on 2016-05-16
Hi,
I recently enabled ssh using keys and disabled password authentication. As my /home is encrypted I needed to follow the instructions in  [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) to be able to ssh in. However, I keep getting an xauth problem. I can still ssh in but I can't do anything that requires x11. I get

xauth: timeout in locking authority file /home/user/.Xauthority
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

So, I can ssh in but I can't do anything that requires x11, unless in the remote computer I have already gone into my account. In other words, if I leave my office computer on and logged into my account and then from my house I ssh in, I have no problems at all. The issue is that if I turned off my office desktop before leaving, I am able to turn it on and ssh in, but I get the xauth message back and anything that requires x11 doesn't work.

Any suggestions on how to fix this? Thanks.

* Edit: I'm using Ubuntu 16.04.

---

### Post by steeldriver on 2016-05-16
Is your home directory getting successfully decrypted + mounted when the SSH connection is established? What exactly are you doing that requires X11 (running xclock or xeyes, or something more complicated)?

---

### Post by flucoe2 on 2016-05-16
Thanks steeldrive.

Initially my home directory is not mounted. I need to do ecryptfs-mount-private and use the login passphrase for the home directory to be mounted. That works fine.

I need X11 to use the GUI of two programs. I can do almost everything via terminal but for some things it is good to have the option of "opening" the actual program.

Thanks.

---

### Post by steeldriver on 2016-05-16
Do you still get the xauth error after manually mounting your home directory? 

How are you setting up the X forwarding from the client side (ssh -X? ssh -Y? something else?)

---

### Post by flucoe2 on 2016-05-16
Yes, I get the same error. I can still run things through the terminal but the error still shows up when trying to use GUIs. I'm using ssh -X.

---

### Post by sns4rnr on 2016-08-18
I had the exact same problem. The encrypted home directory is not decrypted and mounted until the user login is complete. The ssh initiated Xauth authentication is tied to the login process and tries to write a new proxy .Xauthority file to the user's home directory  However during the login process, that directory is not yet mounted and so the Xauthentication cannot write this file and fails.

NOTE: xauth writes this file on every SSH session and may delete it when the SSH is done... The Xauthentication key used by an SSH session is a one-time use key that is spoofed at the machine you initiate ssh from.  A new one is created and written for each session.

If I read Xauth manual correctly, it seeks the .Xauthority file according to the following priority.
A. Path/File specified in the xauth command line with '-f' option   (does not apply to xauth invoked automatically by remotely initiated ssh session)
B. Path/File identified by environment variable XAUTHORITY
C. .Xauthority file located in a user's home directory.   (the default that's almost universally used)

A does not apply here, and C does not work for the reason noted.  That leaves B.
We need to set the XAUTHORITY environment variable globally to direct xauth to find the .Xauthority file in a non-encrypted location.

As an example I placed mine at:  /etc/ssh/myuser/.Xauthority
The /etc/ssh/myuser directory and content is owned by myuser.

sudo mkdir /etc/ssh/myuser
sudo chown -R myuser:myuser /etc/ssh/myuser

I don't think you have to actually create/copy/generate the .Xauthority file itself.  The SSH spoofed authentication process is going to write a new one regardless.  The following environment variable is just telling xauth where to do that.

Add the following line to the end of the  /etc/environment  file:
XAUTHORITY=/etc/ssh/myuser/.Xauthority

After rebooting the server, I can now successfully login without the Xauth errors and X forwarding is working.

CAVEATS:
1.  Multi-user - While this works for using SSH with the one user, it may require tweaking if you intend to SSH in multiple user's names.  It should still work, but the unencrypted location of the .Xauthority file may need to be shared and read/writable by every user that you wish to use it.  I have not yet found a way to set a "per-user" environment setting that does not involve being part of the login process or uses a folder in the encrypted home and therefore probably subject to failure on the same basis as the original problem.

2.  SSH server's own local users - This solution works for me with a headless VPS server.  But if your SSH server is a machine complete with multiple users, real display/keyboard/mouse and a desktop environment, this will likely create problems and/or a security whole with the normal "non-ssh" based xauthentications. I don't recommend it for non-headless server applications.

Alternative if the caveats above apply to your setup:

Assuming a standard config (without the above changes), as the OP noted, the ssh session's Xauthentication succeeds if the user account is already locally logged in at the server.  However, this initial "priming" login does not have to be local at the machine itself.  It can also be another ssh session. Before finding the above solution, my workaround was to start one ssh session whose Xauthentication fails, but logs in the user and mounts his home...  Then open a second terminal and start a second ssh connection to the same user@server in parallel.  The second ssh session's Xauthentication succeeds and X Forwarding works fine for me from that point through the second ssh session.  I can even close the first ssh session once the second is established.  The hassle is that you have to do that two-step process everytime you want to ssh in with X forwarding working.  It's not ideal, but works for me for managing a headless VPS server and will also work with multiple user accounts.

---

### Post by flucoe2 on 2016-08-19
This is great. The workaround works for me. At my first attempt, the first solution did not work. I have to put more time on figuring out why. Thanks for the complete post.

---

