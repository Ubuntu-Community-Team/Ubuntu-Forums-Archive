---
title: "please help install netscape navigator on ubuntu 10.04"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by noodlelover on 2010-08-15
angela@angela-laptop:~$ sudo /home/angela/Downloads/netscape/navigator
[sudo] password for angela: 
sudo: /home/angela/Downloads/netscape/navigator: command not found
angela@angela-laptop:~$ cd
angela@angela-laptop:~$ cd '/home/angela/Downloads/netscape/navigator' 
angela@angela-laptop:~/Downloads/netscape/navigator$ mv navigator/ /usr/local/
mv: cannot stat `navigator/': Not a directory
angela@angela-laptop:~/Downloads/netscape/navigator$ ln -s /usr/local/navigator/navigator /usr/local/bin/navigator
ln: creating symbolic link `/usr/local/bin/navigator': Permission denied
angela@angela-laptop:~/Downloads/netscape/navigator$ sudomv navigator/ /usr/local/
sudomv: command not found
angela@angela-laptop:~/Downloads/netscape/navigator$ ln -s /usr/local/navigator/navigator /usr/local/bin/navigator
ln: creating symbolic link `/usr/local/bin/navigator': Permission denied
angela@angela-laptop:~/Downloads/netscape/navigator$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
angela@angela-laptop:~/Downloads/netscape/navigator$ sudo install
install: missing file operand
Try `install --help' for more information.
angela@angela-laptop:~/Downloads/netscape/navigator$ install
install: missing file operand
Try `install --help' for more information.
angela@angela-laptop:~/Downloads/netscape/navigator$ install navigator
install: missing destination file operand after `navigator'
Try `install --help' for more information.
angela@angela-laptop:~/Downloads/netscape/navigator$ install navigator /home/angela/downloads/
install: target `/home/angela/downloads/' is not a directory: No such file or directory
angela@angela-laptop:~/Downloads/netscape/navigator$ install navigator-bin
install: missing destination file operand after `navigator-bin'
Try `install --help' for more information.
angela@angela-laptop:~/Downloads/netscape/navigator$ ^C
angela@angela-laptop:~/Downloads/netscape/navigator$ 

so confused, please help...  any help would be appreciated =]

---

### Post by zeroseven0183 on 2010-08-15
noodlelover, Netscape Navigator has [long been gone]("http://browser.netscape.com/"). I'm not sure which application are you trying to install but if you want a browser like it, then you already have it since Mozilla Firefox is the default web browser of Ubuntu 10.04.

You can also try other browsers like Konqueror, Midori and Chromium. Open the Ubuntu Software Center and go to Internet > Web Browsers. You'll find there a number of applications.

---

### Post by anewguy on 2010-08-15
And......Mozilla developed the gecko technology that was used in the last versions of Netscape.  Essentially, Mozilla took over development at one point in time with Firefox as the product as an open-source product, if I remember correctly.  Indeed, Netscape has been gone for a long time.

dave ;)

---

### Post by jtarin on 2010-08-15
As was posted...Netscape Navigator is history, but if your interested in running history...let's go. First list all files in the folder that you downloaded. BTW...post the link where you found this download.

---

