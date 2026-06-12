---
title: "[SOLVED] ssh rsa/dsa trouble"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Pflumberg on 2008-12-18
So, I have seen this on a couple of posts and none of the fixes seem to work.  I just upgraded to Ubuntu 8.10 and have now installed openssh-server and am trying to get it to recognize rsa and/or dsa keys.  When I shut down or boot the server, I am getting a message taht says:

Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
 * Restarting OpenBSD Secure Shell server sshd                                  
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key

I have tried going in and deleting the ssh_host_(rsa/dsa)_key files and regenerating them as well as removing them completely and nothing seems to work.  Any suggestions?

Thanks for the help.

Josh

---

### Post by Hospadar on 2008-12-19
What are you trying to do with this?
Passwordless login?

---

### Post by Pflumberg on 2008-12-19
Yeah,

I am just trying to connect with my other computer and instead of having to enter the password, just connect with the rsa or dsa key.

Also, and I don't know if I am wrong here or not, but isn't it a little more secure to use an rsa or dsa key than entering your password?

Josh

---

### Post by MusicMastaMike on 2008-12-19
I'm not sure about security, but here's a link to an excellent HOWTO for setting up an ssh server.  If you follow it along, it will tell you how to do key-based authentication.

[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

---

### Post by Pflumberg on 2008-12-19
Thanks for the info.  I will try that tomorrow.

---

### Post by Pflumberg on 2008-12-21
I tried using 
sudo apt-get autormove openssh-server
to uninstall openssh and it seemed to remove it.  I then used
sudo apt-get install openssh-server
to reinstall the software.  I didn't make any changes from there and tried starting the service and I am still getting the error.  Do you think there may be something wrong with my /etc/ssh/sshd_config file?  Not real sure where to go from here.

---

### Post by Pflumberg on 2008-12-21
Also, when I try typing 
ssh localhost
I get
Read from socet failed:  Connection reset by peer.

Any ideas?

---

### Post by Pflumberg on 2008-12-21
One more thing.  When I type ssh -vvv localhost, here is what I get.
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/.ssh/identity type -1
debug1: identity file /home/.ssh/id_rsa type -1
debug1: identity file /home/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

---

### Post by Pflumberg on 2008-12-21
I finally figured it out.  For some reason the host keys needed to be reset.  I had to log in as user and type:
dpkg-reconfigure openssh-server
That seemed to take care of the issue.  Thanks for the help everyone.

---

### Post by marcio123 on 2010-11-24
Didn't work for me :/
damn... it's gonna be a long night

---

