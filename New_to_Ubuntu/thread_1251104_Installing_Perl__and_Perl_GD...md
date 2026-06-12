---
title: "Installing Perl  and Perl GD.."
date: 2009-08-27
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-27
How to install perl and perl GD from terminal?

---

### Post by tr333 on 2009-09-02
Open a terminal and run the following command:
```
sudo apt-get install libgd-gd2-perl
```

This will install the GD library for Perl.  perl should be already installed on your system at /usr/bin/perl.

---

### Post by karthick87 on 2009-09-02
I have installed perl and perl-GD now..But when i run the below command i get the following error..
root@karthick-desktop:~#  ./squid-graph --output-dir=/tmp/squid-graph < /var/log/squid/access.log
-bash: ./squid-graph: No such file or directory

---

### Post by tr333 on 2009-09-02
That error is telling you it can't find the file squid-graph in the current directory.  I noticed that you are running the command with a root shell.  Do you need to run the command as the root user, or can it be run by the normal user account?

---

