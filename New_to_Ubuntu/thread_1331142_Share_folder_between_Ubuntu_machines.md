---
title: "Share folder between Ubuntu machines"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Dapilot1 on 2009-11-19
So I have a laptop and a desktop and I'm trying to share the external on the desktop, but I cant get either to even open the other computer. They are connected to the same switch which connects them to the building's network and internet. They are both set to the same workgroup in samba and they appear straight in the network folder sometimes. I can't seem to open the workgroup in the windows shares folder nor the computers themselves straight from the network folder. I've created test shares in my home folders and shared them through nautilus and using samba. Any way to fix?

---

### Post by ukripper on 2009-11-19
add yourself as a samba user:
```
sudo smbpasswd -L -a **your_username**

```

and then 
```
sudo smbpasswd -L -e **your_username**

```


```
sudo /etc/init.d/samba restart
```
Now access the samba share from windows/ubuntu machine putting in your username and password.


if samba is not installed then run this command:

```
sudo apt-get install samba
```



and now run all the above steps.

---

### Post by k3lt01 on 2009-11-19
Samba is for sharing between Linux and Windows machines.

If you just want to share between Ubuntu machines you can [ssh]("https://help.ubuntu.com/9.10/serverguide/C/openssh-server.html"). Follow the Ubuntu Server Guides instructions in the link and you should be ok, its not difficult.

---

### Post by Dapilot1 on 2009-11-30
I went and added myself on both of the ubuntu machines, but I still get the error. It says "Unable to mount location: fail to retrieve share list from server" whenever I try to connect to the computer the rare times it is right in the network folder or if I go to Windows Network/Workgroup. Also I do want windows machines to be able to access it.

---

### Post by k3lt01 on 2009-11-30
Did you follow the instructions in the link I gave you?

---

### Post by Dapilot1 on 2009-12-08
This step eludes me.
>  By default the public key is saved in the file ~/.ssh/id_dsa.pub, while ~/.ssh/id_dsa is the private key. Now copy the id_dsa.pub file to the remote host and append it to ~/.ssh/authorized_keys by entering:

ssh-copy-id username@remotehost

Finally, double check the permissions on the authorized_keys file, only the authenticated user should have read and write permissions. If the permissions are not correct change them by: 

I have the id_dsa.pub in my home folder, but it gives me this when I run that.
> /usr/bin/ssh-copy-id: ERROR: No identities found


---

