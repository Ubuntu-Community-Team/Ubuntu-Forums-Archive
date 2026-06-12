---
title: "Help in developing a Network Appliation to monitor pc in a network"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by valaparambil88 on 2009-01-31
I am developing a Network Appliation to monitor computers in a network.
Specs are

   1. App monitors the current web page viewed in each system
   2. App also can shutdown the computer in the network
   3. App can show all process run by each computer in the network



I am now confused how to start my project.
Pls guide me in my project.

---

### Post by yeats on 2009-02-01
Hi -

Why don't you post to one of the Programming and Development boards?  This board is mainly for new users with very basic questions about functionality.. . .

[http://ubuntuforums.org/forumdisplay.php?f=310]("http://ubuntuforums.org/forumdisplay.php?f=310")

Good luck

---

### Post by Gulyan on 2009-02-01
Not sure about how to do 1st but the 2nd and 3rd can easily be done with ssh:
Install ssh on the network computers and type in a terminal:
```
ssh user@address
```
After you login you can use:
```
ps -e
```
to display all processes
```
shutdown -h now
```
to shutdown

You can also use all the other commands available from the terminal.

---

### Post by llamakc on 2009-02-01
> **valaparambil88 said:**
> I am developing a Network Appliation to monitor computers in a network.
Specs are

   1. App monitors the current web page viewed in each system
   2. App also can shutdown the computer in the network
   3. App can show all process run by each computer in the network



I am now confused how to start my project.
Pls guide me in my project.

Is this homework?

---

