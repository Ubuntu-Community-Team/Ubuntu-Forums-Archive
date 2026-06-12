---
title: "SSH to shared hosting environment?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2009-02-19
Hello, I am trying to use SSH to connect to my shared hosting server.  I am able to log in without issue, but scp doesn't seem to be working, nor does sftp (both return the message: "bash: <command> command not found").

I would like to connect via public/private key authentication.  Is there any way to upload my public key to the server without using scp or sftp?  

Is there perhaps a GUI SSH client that will allow me to manage files and such in a window environment?

If scp and sftp do not exist on the shared host, what options do I have for secure file transfer?

Thanks!

---

### Post by Vadi on 2009-02-19
The file manager is able to work with sites remotely. Just use *Places - Connect to Server...* to connect, and you're good to go.

---

### Post by Dj Melik on 2009-02-19
You can also use sshfs.

```
sudo apt-get install sshfs
```

then proceed by

```
sshfs REMOTE SERVER:FILEPATH MOUNT
```

so for example it would look something like

```
sshfs 55.55.55.55:/home/test/ ~/ftp/
```

---

### Post by Dr Small on 2009-02-19
And you can just create the .ssh/id_dsa.pub file and put your key contents in there via the SSH session. I've had to do it that way before. Apparently the shared server has disabled sftp subsystem (you should be able to tell from the /etc/ssh/sshd_config file).

---

### Post by Ocxic on 2009-02-19
in order for scp to work, both computer need to have an ssh server installed and running.

---

### Post by Dr Small on 2009-02-19
> **Ocxic said:**
> in order for scp to work, both computer need to have an ssh server installed and running.
I did not think so. I thought that all that was needed was client to server communication, but then again, maybe I am wrong. I always install openssh-server :D

---

### Post by Nixie Pixel on 2009-02-20
Wow, thanks for all the responses, I will try them out!

I did have OpenSSH server installed, and scp still didn't work.

> **Dr Small said:**
> And you can just create the .ssh/id_dsa.pub file and put your key contents in there via the SSH session. I've had to do it that way before. Apparently the shared server has disabled sftp subsystem (you should be able to tell from the /etc/ssh/sshd_config file).

What would the command be to do this?

Thanks!

---

