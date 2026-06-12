---
title: "[SOLVED] How to share folders between 2 Ubuntu PCs using live CD on one?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by janmartin on 2008-07-24
Hi,

I have 2 PCs and need to copy 100 GB from first to the second PC using the Ethernet network.

**First PC:**
Running Ubuntu 8.04.1 live CD. 
I cannot install Ubuntu on this PC!

**Second PC:**
Running installed Ubuntu 8.04.

Whenever I try to share a folder on the first PC I get this error: 

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error permission denied. You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.


All I find in this forum is the info that it is a known Samba error and the workaround is to log out and then log in again to work around it.

[http://ubuntuforums.org/showthread.php?t=772706](http://ubuntuforums.org/showthread.php?t=772706)


**How to "logout and then login again" running a live CD?** Restarting the live CD obviously does not work.

So I tried restarted Samba using:
sudo /etc/init.d/samba restart

But it did not help.
What to do now?

Alternative question:
How to move the 100 GB without Samba?

Thanks.





How to share folders between 2 Ubuntu PCs using live CD on one?

---

### Post by janmartin on 2008-07-24
Hi,

I give the answer myself: 
I managed to copy the files 'installing' openssh-server on live CD.

This is how I did it:
**First PC:**
Ubuntu 8.04.1 Desktop live CD running.
Applications, Accessories, Terminal
```
ifconfig
```Write down the data shown at "inet addr:"

```
sudo apt-get install openssh-server
```

```
ssh localhost
```Does not work due to no password for default user 'ubuntu' of the live CD specified.

```
sudo passwd ubuntu
```Enter a password, I used **ubuntu**

**Second PC:**
Menu, Places, Connect to Server...

Service Type: SSH
Server:	 The "inet addr:" you found out using ifconfig.
Klick Connect.

I have been prompted to enter the new password ubuntu twice.
Nautilus will now show the usual list of folders and files of the first PC.

Open a second Nautilus Window in 
Places, Home 
and simply copy and past folders and files between the 2 nautilus windows.


Good luck!

---

### Post by gleble on 2008-07-24
You could try this
In your terminal type nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine..

---

### Post by kajillin on 2008-07-24
should mark this as solved so anyone else with this prblem will know to come here.

---

### Post by farlander762 on 2008-07-25
I couldn't get Samba to work either.  Error 225 about setting up a permission.  

Thanks Jan!!

---

