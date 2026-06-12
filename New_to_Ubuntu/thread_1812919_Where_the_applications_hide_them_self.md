---
title: "Where the applications hide them self"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by kent69 on 2011-07-27
I have download the some applications from download center but I can not find them not by search no by run application!!

would you please advise.

More over I have installed ubuntu and Kubuntu in 2 different laptops inside windows via VM box and I found problem with ubuntu download center when I googled the issue and 2 answers I found for my problems one is to remove the lock and the list (dont remember the terminal command)any how when start updating ubuntu by sudo apt-get update the update starts and took long time to download after downloading I receive the message that can not fetch the updates?
during the ubuntu installation I repeat it 5 times with no success, later I removed the vmbox and installed again so I got ubuntu but after restarting the interface been changed to other colour. 
Pls advise

---

### Post by alphacrucis2 on 2011-07-27
> **kent69 said:**
> I have download the some applications from download center but I can not find them not by search no by run application!!

would you please advise.

More over I have installed ubuntu and Kubuntu in 2 different laptops inside windows via VM box and I found problem with ubuntu download center when I googled the issue and 2 answers I found for my problems one is to remove the lock and the list (dont remember the terminal command)any how when start updating ubuntu by sudo apt-get update the update starts and took long time to download after downloading I receive the message that can not fetch the updates?
during the ubuntu installation I repeat it 5 times with no success, later I removed the vmbox and installed again so I got ubuntu but after restarting the interface been changed to other colour. 
Pls advise

Which version of ubuntu and which applications? Your problem with apt-get sounds like either a network issue or an issue with the mirrors you are using. You want to first verify that network access is working using something like a web browser.

---

### Post by kent69 on 2011-07-27
with regards to the application I was asking in general where they hide them self (not all application) for instance I download php-net-portscan I never rich it!! with regard to Unbuntu updates I download the updates that means Im connected no problems with the mirror or with the connection as I was googling the issue from ubuntu browser.
Thanks

---

### Post by alphacrucis2 on 2011-07-27
> **kent69 said:**
> with regards to the application I was asking in general where they hide them self (not all application) for instance I download php-net-portscan I never rich it!! with regard to Unbuntu updates I download the updates that means Im connected no problems with the mirror or with the connection as I was googling the issue from ubuntu browser.
Thanks

According to what I read on their website this package is a set of php functions that you can use from a php program. It isn't an application you can run as such.

[http://pear.php.net/manual/en/package.networking.net-portscan.php]("http://pear.php.net/manual/en/package.networking.net-portscan.php")

As such it is of probably of no use to you unless you want to learn how to write PHP programs.

---

### Post by oldos2er on 2011-07-27
You can see where each file in a package is installed in the filesystem with ```
dpkg -L <package name>
``` or in Synaptic by right-clicking on an installed package, Properties, Installed files.

Apps meant to be run in a terminal will not create a menu entry.

---

