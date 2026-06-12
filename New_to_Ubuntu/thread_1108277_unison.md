---
title: "unison"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by hellomoto on 2009-03-27
hey 

 I installed unison as I wanted to 2way sync as rsync can't do this. I installed 
          unison2.13.16-gtk

I had a play around with it for a while and then thought i like this I would like to now use the command line version.

I went into synaptic marked unison2.13.16-gtk for complete removal. 
I then went and remove .unison and unison.log from my home directory so that it was completely removed.

Then i installed unison but when i provoke it from the command line it doesn't recognize that the program has been installed.

```

mark@mark-desktop:~$ sudo apt-get install unison2.13.16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  unison2.13.16
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/494kB of archives.
After this operation, 1180kB of additional disk space will be used.
Selecting previously deselected package unison2.13.16.
(Reading database ... 117511 files and directories currently installed.)
Unpacking unison2.13.16 (from .../unison2.13.16_2.13.16-1_i386.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up unison2.13.16 (2.13.16-1) ...

mark@mark-desktop:~$ unison
The program 'unison' can be found in the following packages:
 * unison
 * unison2.13.16
 * unison-gtk
 * unison2.13.16-gtk
Try: sudo apt-get install <selected package>
bash: unison: command not found
mark@mark-desktop:~$ 


```

any ideas?

---

### Post by hellomoto on 2009-03-27
bump

---

### Post by yarri on 2009-04-29
Jaunty: after the upgrade Unison does not connect to the remote server anymore. I checked and ssh works fine as is local synchronization. I have same versions of unison installed on my laptop and workstation, the latter has also openssh-server. 
I am also getting an error message:
bash: unison: command not found
Lost connection with the server
I was trying also to remove .ssh folder and start a new profile to know avail. 
I really need to get unison to work. Any ideas how to solve this?

---

### Post by Marat Galiev on 2009-04-29
In terminal type unison(and press tab).
Look at the right command and press enter.
Or try sudo apt-get install unison.
You need this [http://packages.ubuntu.com/jaunty/unison](http://packages.ubuntu.com/jaunty/unison) package.

---

### Post by yarri on 2009-04-29
Thanks. As I said I have necessary packages installed on both computers. Moreover I was looking up on the Internet and I have found following pieces of information
[https://bugs.launchpad.net/ubuntu/+source/unison/+bug/58134](https://bugs.launchpad.net/ubuntu/+source/unison/+bug/58134)
as well as a topic on ubuntu forums
[http://ubuntuforums.org/showthread.php?p=7051648](http://ubuntuforums.org/showthread.php?p=7051648)
Where gnome-keyring is mentioned. I am not sure if this is important thou.

---

### Post by yarri on 2009-04-29
Hej!

It seems that I figured out what was wrong. For some reasons /usr/bin/unison was a symbolic link pointing to an empty file 
```
/usr/bin/unison -> /etc/alternatives/unison
```

I have deleted the link and created a new one on the server: 
```
sudo ln -s /usr/bin/unison-2.27.57 /usr/bin/unison
```
From now on, the synchronization over ssh works again.

---

### Post by kortas on 2012-01-30
Hm... the same problem. Did not help me:

sudo rm /usr/bin/unison
sudo ln -s /usr/bin/unison-2.32.52 /usr/bin/unison

Okay, this is it:

I get '**bash: unison: command not found**' after entering the SSH password.
Make sure Unison is installed on the host you are trying to connect to.

source: [https://alliance.seas.upenn.edu/~bcpierce/wiki/index.php?n=Main.UnisonFAQTroubleshooting](https://alliance.seas.upenn.edu/~bcpierce/wiki/index.php?n=Main.UnisonFAQTroubleshooting)

---

