---
title: "Unison - Lost connection with the server"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by mabox on 2011-04-19
Hello Ubuntu Community,
this is my first time with ubuntu. Currently I try the change from windows to linux. A very important part for me is the backup from my personal data's from a local folder to a folder on my QNAP NAS. For this I want a synchronization tool.
I found "unison" but I have big problems with this tool.

- I start unison and create a new profil. 
- Then I enter the first (local) directory.
- I check the "SSH" option, enter a host name and a username and at last the remote directory path
- Now I click on "Ok", then I see a pop up with the question for my user password
- After this I recieve the error "Fatal Error - Lost connection with the server"

In the config file in the folder ".unison" in the home folder are this entries:

root = /home/username/personal
root = ssh://admin@192.168.1.33/Personal

In the shell I can connect with ssh to my NAS, but only with this command:
ssh admin@192.168.1.33

With this command:
ssh admin@192.168.1.33/Personal
I recieve this error message:
ssh: Could not resolve hostname 192.168.1.33/Personal: Name or service not known

Any idea?

Greetings
mabox

---

### Post by mynameisnotbob on 2011-04-19
I'm not certain about this at all, but it could be that the terminal doesn't accept backslashes until you put a port number on the address. Try that.

Oh! Try just remote username/password connection, not SSH.

---

### Post by mabox on 2011-04-20
With remote connection I recieve the same failure. The commentary with the backslashes and port number I not understand. I need backslashes??

---

### Post by mynameisnotbob on 2011-04-20
Do you know if that's the exact location of the file on the server? type, once you are ssh'ed to the server like you said you can, type ls. No capitals. Pray Tell what it says.
I think your problem is that you have to connect to the server in a terminal, and then access the file from that terminal.

---

### Post by mabox on 2011-04-23
Hi notbob,
I still have no access with unison about ssh. But I found a other solution. I just mount the folder from the NAS with a fstab entry. After this I can configure in unison two "local" folders. It works :)
Thanks a lot for your answers and time.

---

### Post by mynameisnotbob on 2011-04-24
You&#341;e welcome.

---

### Post by mozkill on 2011-12-10
Im using Ubuntu 11.10 and Unison-2.32.52-gtk  and when I try to make a SSH connection to my Dlink-DNS-323 device (which is serving SSHD via funplug 0.5)  I get this error:

> Unison Conacting server...
Fatal error
Lost connection with the server

This is my .prf config file for Unison:

> root = /mnt/disk-BACKUP
root = ssh://root@backup//usr/share/ftp_server/Volume_1/disk_BACKUP/

I have no problems connecting to this Dlink SSHD server with this command:   ssh root@backup

Furthermore, using GAdmin-rsync GUI, that application is able to make the ssh connection.  I prefer Unison though...

So, I am at a loss as to why Unison would behave like this.

The unison log says simply:

> Lost connection with the server

???

---

### Post by amac777 on 2012-01-08
I got this error as well. The solution was to simply install unison on the remote server as well.

---

### Post by scholarmed on 2012-02-28
@amac777

how make my day! Works greatly...

---

### Post by lpanebr on 2012-04-12
@amac777

THANKS!

I then had another issue due to different versions installed on my notebook and server but that got solved by downloading and installing the same version as suggested here: [http://ubuntuforums.org/showthread.php?t=1449670](http://ubuntuforums.org/showthread.php?t=1449670)

:-)

---

### Post by obstacle on 2012-12-26
@amac777
Duuuuuh... so easy yet soooo....  Thanks!

---

