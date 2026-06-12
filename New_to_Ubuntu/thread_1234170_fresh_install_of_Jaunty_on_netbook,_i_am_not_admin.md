---
title: "fresh install of Jaunty on netbook, i am not administrator?"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by biomedtech on 2009-08-07
Hello, 

I am having a pickle with Jaunty. I installed it on my netbook, and everything seemed normal. However, when trying to use the software update I discover that I am not the admin. I get the following warnings.


Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '35651621' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpzS5XUa' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.



Failed to run /usr/bin/software-properties-gtk '--open-tab' '2' '--toplevel' '35651621' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.



how is it that I am not the administrator when I just installed Jaunty? I answered all the questions prompted to me during the installation, so I do not understand why I am not allowed to do anything.  Please help..

---

### Post by Bölvaður on 2009-08-07
Press : Alt+F2
Type : gksu nautilus /etc

Are you able to edit fstab and save the changes? You don't have to do more than adding a letter to a text that has been commented out.
This is not really a basic thing, but it will be interesting to see if this works or not.

---

### Post by snowpine on 2009-08-07
Ubuntu has a unique approach to root/admin, check out this helpful document: 
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by biomedtech on 2009-08-07
It didn't work. I went to that page, and tried one of their examples, and again was denied. The warning messages was as follows. 

gtw@ubuntu:~$ sudo chown bob:bob /home/bob/*
[sudo] password for gtw: 
gtw is not in the sudoers file.  This incident will be reported.
gtw@ubuntu:~$

This just doesn't make sense, so I tried to add myself as a new user, and got the following:

gtw@ubuntu:~$ sudo adduser gtw admin
[sudo] password for gtw: 
gtw is not in the sudoers file.  This incident will be reported.
gtw@ubuntu:~$ 



I never had this problem with Fiesty or Gutsy (btw, this is a new install, not an upgrade). Any time I need to make a change, I was always prompted for a password, and it was accepted. 

What is the purpose of supplying a user name and password on the Install, if it isn't used? Getting frustrated.

---

### Post by snowpine on 2009-08-07
The first user you created during the initial install process will have sudo privileges. New users may or may not have this priviledge, depending on how you set them up. 

If your sudo got broken somehow, here is a good guide for fixing it in recovery mode: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by biomedtech on 2009-08-08
I gave up on that particular version of Ubuntu, and found the Netbook Remix img. I used Unetbootin to create the usb bootdisk, it installed it on  my Eee PC, and everything seems to be working just fine. No issues with authentication, and the wireless sees other networks, altho I have't been able to make a secure connection yet. thank you for the advice, I really think the version I had wasn't optimized for the netbook. take care

---

