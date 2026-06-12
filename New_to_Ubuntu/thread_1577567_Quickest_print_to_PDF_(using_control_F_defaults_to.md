---
title: "Quickest print to PDF (using control F defaults to PostScript) :("
date: 2010-09-19
forum: New to Ubuntu
---

### Post by rocksockdoc on 2010-09-19
I'm new to Ubuntu. I print to PDF a lot but the default control-F application defaults to PostScript. And it does not seem to default to my desired ~/tmp/print directory either.
Plus it does not even default to "print to file" (I don't have a printer hooked up).

Where is the configuration file (aka "edit -> preferences") for the default Ubuntu print command which is initiated by control F?

[COLOR=DarkRed][B]How can I set the preference to PDF instead of PS?
How can I set the directory to a specific directory?
How can I set the action to print to file (not to a printer)?[/B][/COLOR]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169925&stc=1&d=1284880737[/IMG]

---

### Post by gzarkadas on 2010-09-19
[This thread]("http://ubuntuforums.org/showthread.php?t=1567310") provides a solution.

---

### Post by niteshifter on 2010-09-19
Hi,

As gzarkadas posted, cups-pdf will do what you want. The link provided is outdated, cups-pdf isn't hard to set up.

First, get it:
```
apt-get install cups-pdf
```

cups-pdf by default prints to a folder named PDF in your home directory, which you may need to create:
```
cd ~
mkdir PDF

```

Or you can have it print someplace else by editing the file:
```
/etc/cups/cups-pdf.conf
```
Look for this text near the beginning of the file:
```
### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}

Out [COLOR="Red"]${HOME}/PDF[/COLOR]

```
Change the part marked in red, above. Do not put this folder on a removable drive, cups gets freaky when you do and the drive isn't available at print time.

---

