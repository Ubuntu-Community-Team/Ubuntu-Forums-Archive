---
title: "Appropriate location for log file?"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by japhyr on 2010-08-09
Hello,

I am just getting around to installing 10.04.  Rather than install all my programs through synaptic this time, I am writing a script to install them all automatically.  This way, when 10.10 comes out I just run the script again and all the latest versions of programs are installed for me.

The script is logging the output of "apt-get install".  Where should this log be located?  I was going to put it in /var/log, but when I run the script permission is denied to create a file there.  Should I change permissions on the var/log folder, or put my log file somewhere else?

---

### Post by bodhi.zazen on 2010-08-09
> **japhyr said:**
> Hello,

I am just getting around to installing 10.04.  Rather than install all my programs through synaptic this time, I am writing a script to install them all automatically.  This way, when 10.10 comes out I just run the script again and all the latest versions of programs are installed for me.

The script is logging the output of "apt-get install".  Where should this log be located?  I was going to put it in /var/log, but when I run the script permission is denied to create a file there.  Should I change permissions on the var/log folder, or put my log file somewhere else?

Personally I would put the log in your home directory.

In order to install , you are running commands as root, so I advise the script be called with sudo. If you do so you would be able to log in /var/log

---

### Post by japhyr on 2010-08-09
Running the script with sudo works.  I am also trying to learn more about appropriate locations for parts of the system.  Is there a particular reason for putting this log in my home folder, rather than in /var/log?

---

### Post by -kg- on 2010-08-09
I can't speak for BZ, but I would think it would be ease of finding it.  Quite a few log files are stored in "/var/log", and your personal log file would be a little difficult to find.  You can store it in it's own directory along with the script, then it would be easy to find once you did the install.

There is another reason; if you have a separate "/home" partition, you can do an installation and leave your "/home" partition intact.  "/var" is contained in the "/" (root) directory, which is overwritten in the installation process.  That means you would have to (find and) save the log file elsewhere before the installation so you would have it to use.

Of course, if you didn't create a separate "/home" partition, you're going to have to do that anyway, since "/home" will be on the "/" partition and will be destroyed in the installation process.  If your specially created log file is somewhere you can easily find it, that will make it more easy to back up with the rest of your data.

---

### Post by bodhi.zazen on 2010-08-09
> **japhyr said:**
> Running the script with sudo works.  I am also trying to learn more about appropriate locations for parts of the system.  Is there a particular reason for putting this log in my home folder, rather than in /var/log?

No it would be personal preference. I assume you will run it only once, and I tend to think of /var/log as ongoing system logging.

---

### Post by japhyr on 2010-08-10
> **-kg- said:**
> There is another reason; if you have a separate "/home" partition, you can do an installation and leave your "/home" partition intact.  "/var" is contained in the "/" (root) directory, which is overwritten in the installation process.  That means you would have to (find and) save the log file elsewhere before the installation so you would have it to use.

I do have a separate /home partition, but I don't think that makes a difference here.  Reinstalling the OS means I have to run this script again, and it's the new log file that will be significant.  Regardless, your point is well taken that I may want to keep my own logs out of the system directory.

I ended up making a scripts folder in my home directory, and keeping the log file there as well.  Thank you both for the input.

---

