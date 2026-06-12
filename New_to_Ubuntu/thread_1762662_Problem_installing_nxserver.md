---
title: "Problem installing nxserver"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by svankaya on 2011-05-19
Hello All, I am trying to install nxnode, nxclient and nxserver onto my ubuntu 11.04 with KDE environment. Everytime i keep getting some error message and the recent one is given below. Your help is greatly appreciated. Thanks.


Setting up nxserver (3.5.0-4) ...
NX> 704 ERROR: Cannot add user: nx.
NX> 704 ERROR: User: nx already exists.
NX> 704 To fix the problem, you may try to completely uninstall NX
NX> 704 Server and install it from scratch. If this is not enough,
NX> 704 please delete the nx user by using the system commands and
NX> 704 proceed with a new installation of NX Server.
dpkg: error processing nxserver (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver

Regards,
Sai

---

### Post by compmodder26 on 2011-05-19
You have a user called nx already on the system.  My guess is from a previous installation attempt.  It appears that the installer requires you to delete this user from your system before you can continue.

Edit:  On second look, that error is from a post-installation script.  Meaning that nxserver has been installed but a script that is triggered to run after the installation failed.  Now I'm not sure what else that script is supposed to do that may not have run.  But you could try to run nxserver and see if all is well.

---

### Post by crispy_420 on 2011-05-19
Did you install from the .deb packages provided on their website?

If so try re-downloading them to get a "clean" copy. You will need all three packages for the machine: server, client and node.

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

Since it looks like you may have had a bad install, using synaptic try to "completely" uninstall them from before. Then install the newly downloaded version, I'm not 100% on the order but the server is last.

Also is there a user called nx on your system?

---

### Post by svankaya on 2011-05-19
THanks for your interest in the problem. I uninstalled all the client, node and server using synaptic manager and then reinstalled again and got the following error message,

NX> 704 ERROR: Cannot add user: nx.
NX> 704 ERROR: User: nx already exists.
NX> 704 To fix the problem, you may try to completely uninstall NX
NX> 704 Server and install it from scratch. If this is not enough,
NX> 704 please delete the nx user by using the system commands and
NX> 704 proceed with a new installation of NX Server.
dpkg: error processing nxserver (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
nxserver
E: Sub-process /usr/bin/dpkg returned an error code (1)


then i removed the usr by,
sudo deluser --remove-all-files nx in /usr folder. Then reinstalled all the three packages and everything got installed. THanks all for your help. 

Regards,
Sai

---

### Post by crispy_420 on 2011-05-21
sudo userdel nx

Worth a shot right?

---

