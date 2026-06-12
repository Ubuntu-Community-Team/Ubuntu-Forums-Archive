---
title: "problem installing skype 2.1 beta in karmic"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by jelafu on 2009-12-28
Hello everyone,
I need advice. I have uninstalled the old skype, and downloaded the new 2.1 beta version, but the WDebi won't open it. If I try to install in terminal I get this
jelena@jelena-laptop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate

I have also tried by adding medibuntu repository (as suggested by some users), but the same thing happens, can't install it. I have checked in synaptic, but there's only skytooles package there, nothing more.
If anyone has any idea, please, share it. 
Thanks!
Jela

---

### Post by MelDJ on 2009-12-28
skype is no longer in the medibuntu repo.
get the .deb here: [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

---

### Post by jelafu on 2009-12-28
Thanks MelDJ,
I've downloaded deb. from the skype website, but can't install it anyway. Double-click does nothing, can't do it in terminal either.
My friend installed it and it works fine. I don't understand what's wrong with mine...
Jela

---

### Post by MelDJ on 2009-12-28
try dragging the package into terminal and press enter. it should install then. if it doesn't what does terminal say or do?

---

### Post by jelafu on 2009-12-28
The terminal says:
jelena@jelena-laptop:~$ '/home/jelena/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb' 
bash: /home/jelena/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb: Permission denied
???

---

### Post by MelDJ on 2009-12-28
you need to install programs as root (super user). so we use the sudo command.
so the command should be: sudo '/home/jelena/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb'
it will then prompt you for your password. when you type it in, it will be invisible (no ***). after typing, just press enter.

---

### Post by jelafu on 2009-12-28
I'm getting:
jelena@jelena-laptop:~$ sudo '/home/jelena/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb'
[sudo] password for jelena: 
sudo: /home/jelena/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb: command not found
:-(

---

### Post by SymenTimmermans on 2009-12-29
sudo aptitude install /home/jelena/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb

---

### Post by gradinaruvasile on 2009-12-29
The correct syntax for installing the standalone .deb file is:

[COLOR="Red"]sudo dpkg -i /home/jelena/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb[/COLOR]

apt-get/aptitude install are used for packages from the repositories.

---

### Post by jelafu on 2009-12-29
> **gradinaruvasile said:**
> The correct syntax for installing the standalone .deb file is:

[COLOR=Red]sudo dpkg -i /home/jelena/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb[/COLOR]

apt-get/aptitude install are used for packages from the repositories.

This worked! All other commands in terminal couldn't unpack deb.

Thank you so much!

---

### Post by abhiroopb on 2009-12-29
> **MelDJ said:**
> skype is no longer in the medibuntu repo.
get the .deb here: [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

Why was it removed from the medibuntu repository?
Will it ever return to the medibuntu repository?
Is there any other repository which has skype?

---

### Post by MelDJ on 2009-12-29
> **abhiroopb said:**
> Why was it removed from the medibuntu repository?
Will it ever return to the medibuntu repository?
Is there any other repository which has skype?

i remember reading bout it here: [http://ubuntuforums.org/showthread.php?t=1352648&page=6](http://ubuntuforums.org/showthread.php?t=1352648&page=6)

i may have missed the later parts of the thread so correct me if i was wrong:)

---

### Post by abhiroopb on 2009-12-29
Thanks for the link!

---

### Post by paddyjoe on 2010-02-12
When I tried to open the file in Package Install
er I got the following message:

Software index is broken
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I am an absolute beginner in Linux and have no idea how to proceed based on the above.
Can anyone help.

I upgraded to karmic 9.10 today. The version number is Linux 2.6.31-19-generic

---

### Post by tollex on 2010-02-14
hi, I downloaded the last skype package installer from their site. and in procces of installing I recieved this message :
**Failed to install package 'skype-ubuntu-interpid_2.1.0.81-1_amd.64.deb'**
In terminal:
(Reading database ... 196601 files and directories currently installed.)
Unpacking skype (from .../skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb) ...
dpkg: error processing /home/sk/Desktop/skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb (--install):
 trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)

what can I do to finish installing skype ?
thx.

---

### Post by fofftorrent on 2010-02-14
is the skype repo at "deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free" still available? i get

Err [http://download.skype.com](http://download.skype.com) stable/non-free Packages
  404 Not Found [IP: 212.72.53.130 80]

---

### Post by CuriousChris on 2010-05-07
Help
I'm having the same problem. I've never installed anything on Ubuntu before 
I've managed to put in the "[COLOR=Red]sudo dpkg -i /home/christine/Desktop/skype-ubuntu-intrepid_2.1.0.81-1_i386.deb[/COLOR]"

(modified my name and the name 81 )

I get an error message " Package libqt4-dbus is not installed."

any suggestions would be appreciated.
Christine

---

