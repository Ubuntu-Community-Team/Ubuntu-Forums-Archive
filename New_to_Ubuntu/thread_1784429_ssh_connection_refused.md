---
title: "ssh connection refused"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by nitstorm on 2011-06-16
I followed [this]("http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229") guide and added the following lines according to it to my ***/etc/ssh/sshd_config***

```
Subsystem sftp internal-sftp
Match Group sftpgang
        ChrootDirectory %h
        ForceCommand /usr/lib/openssh/sftp-server
        AllowTcpForwarding no

```
And did the following to set the permissions:
```

  sudo usermod -s /bin/false sftptrial1
  sudo usermod -s /bin/false sftptrial2
  sudo chown nits:nits /home/sftptrial1
  sudo chown nits:nits /home/sftptrial2
  sudo chmod 0755 /home/sftptrial1
  sudo chmod 0755 /home/sftptrial2

```

My main account is not added to the *sftpgang *group but *sftptrial1 *and *sftptrial2 *are.
I restarted my ssh service with
```
sudo service ssh restart
```

And then tried sshing into my own account. And it spits the following error. (It was working fine before I touched the sshd_config file)
```
nits@nits-workstation:~$ ssh nits@localhost -p 435
ssh: connect to host localhost port 435: Connection refused

```


What do I do?

---

### Post by manzdagratiano on 2011-06-17
In sshd_config, did you enable port 435?

"Port 435", right near the beginning of the file.

Your ssh options seem much more complicated than what I use... I just allow a specific port, and grant access to only a specific user:

Port <port_number>
AllowUsers <username>

and that works well!

---

### Post by nitstorm on 2011-06-17
Yes the port is 435 but there is never touched the AllowUser parameters. Just until before I edited the /etc/ssh/sshd_config file ssh was working perfectly fine.

---

### Post by nitstorm on 2011-06-17
I fixed it by moving the Match Group rules to the bottom of /etc/ssh/sshd_config file.
Now when I try to login with one of the *sftpgang *group then I get the following error:
```

nits@nits-workstation:~$ sftp -P 435 sftptrial1@localhost
sftptrial1@localhost's password: 
Write failed: Broken pipe
Couldn't read packet: Connection reset by peer

```

---

### Post by nitstorm on 2011-06-18
Apparently, had to change the permissions on the user's home directory to
```
sudo chown root:sftpgang /home/sftptrial1
```

Also had to disable PAM Authentication in ***/etc/ssh/sshd_config***
```
#UsePam yes
```


This was solved thanks to Lekensteyn @AU [here]("http://askubuntu.com/questions/49271/how-to-setup-a-sftp-server-with-users-chrooted-in-their-homedirectories/49284#49284")

---

