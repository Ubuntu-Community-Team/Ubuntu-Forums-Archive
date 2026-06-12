---
title: "System wont remember ssh keys"
date: 2016-04-25
forum: Networking &amp; Wireless
---

### Post by arun32 on 2016-04-25
Ubuntu 14.04 wont remember added private keys. On the remote server i generated the private and public key, added the public key to authorized_keys and copied the private key to my local machine and added it with the command ssh-add. It asked me if i want to connect or not and i said yes ofc. Upon loging out/rebooting it it wont let me ssh into the server unless i do the ssh-add again and add the private key into the system. 

Im wondering into which directory i add the ssh private key so i wont have to enter the path to the key all the time. the key is without a passphrase. I forgot how i added the previous keys becuase for those i dont have to re-add them again. I know i could put a command into .profile to add it everytime i start a shell but that's not the solution im looking for.

The error is "Permission denied: publickey"

ty

---

### Post by ajgreeny on 2016-04-25
The ssh help wiki may help you to figure out what, if anything you have not got quite right.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by arun32 on 2016-04-25
> **ajgreeny said:**
> The ssh help wiki may help you to figure out what, if anything you have not got quite right.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Hi, thanks for the reply. I have checked the wiki, googled for quite some time and have not found a solution. Usually this kind of problem is easily solved but i'm running at a brick wall. I have no idea what to do.

edit: ok added priv key to id_dsa and pub key to id_dsa.pub and it works, but how do i do this for several keys? append to file?

---

### Post by May_Masters on 2016-04-26
yes

---

### Post by ajgreeny on 2016-04-26
If this is now solved for you please mark this thread as SOLVED from the Thread Tools menu up-top.

---

### Post by arun32 on 2016-05-03
> **ajgreeny said:**
> If this is now solved for you please mark this thread as SOLVED from the Thread Tools menu up-top.

oh, forgot to reply with the solution i got. i just added the public key and the private key in the ~/.ssh folder and that was it. i named the key for example, "potato" and "potato.pub", which are the private and public keys. not sure why the public one is added, i thought those only go on the server. Applied the correct permissions and that was it!. The naming doesnt matter afaik, it just matters that the private key is the same as the public key(the public key having the .pub extension ofc).

---

