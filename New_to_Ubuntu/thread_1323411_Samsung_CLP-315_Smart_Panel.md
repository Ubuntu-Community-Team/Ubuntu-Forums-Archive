---
title: "Samsung CLP-315 Smart Panel"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by lalimalina on 2009-11-11
Hi,

I am trying to install the Smart Panel for my Samsung CLP-315 printer, in order to view specific error messages and toner levels.  Linux is listed as a supported O.S., but none of the people in Samsung tech support know anything about it, so they haven't been able to help me.

The Smart Panel downloaded as a .tar.gz file, and I extracted it to my home folder.  I attempted to follow the instructions on Samsung's website:

"1. When the Administrator Login window appears, type in root in the Login field
and enter the system password.

2. Download and extract the Smart Panel.
[root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)]

3. The Smart Panel will be extracted as ''cdroot'' folder in current path.

4. Execute installation program.
[root@localhost root]#./cdroot/Linux/smartpanel/install.sh

5. Smart Panel will be installed automatically and success message will be displayed in terminal.

6. Smart Panel will be launched automatically after installation."

Everything was fine through step 3.  I assumed I was supposed to type the line from step 4 into a terminal?  That didn't work.  I tried taking off the [root@localhost root]; still didn't work.  Sorry I didn't save that terminal screen!  But can anyone tell me right off what I'm doing wrong there?

After attempting to follow those instructions, I went to the "How to install ANYTHING in Ubuntu!" guide at [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html) and followed the instructions for .tar.gz files.  Here is the brief transcript from that terminal:

"lexie@lalimalina:~$ pwd
/home/lexie
lexie@lalimalina:~$ ls
cdroot   Documents  examples.desktop  Pictures  Templates
Desktop  Downloads  Music             Public    Videos
lexie@lalimalina:~$ cd cdroot
lexie@lalimalina:~/cdroot$ ./configure
bash: ./configure: No such file or directory
lexie@lalimalina:~/cdroot$ make
make: *** No targets specified and no makefile found.  Stop.
lexie@lalimalina:~/cdroot$ sudo checkinstall
[sudo] password for lexie: 
sudo: checkinstall: command not found
lexie@lalimalina:~/cdroot$ sudo make install
make: *** No rule to make target `install'.  Stop.
lexie@lalimalina:~/cdroot$"

So, any ideas as to what I'm doing wrong here?  Thanks!

---

### Post by lalimalina on 2009-11-14
Anyone have any ideas?

---

### Post by wkulecz on 2009-11-17
Claims of Linux support for these Samsung printers should be filed with the FTC as fraudlent, IMHO.

There are plenty of reports of the install scrips being broken on Ubuntu.

All I can suggest is open a terminal window and do:

sudo -i

Then when you get the root prompt repeat all your Samsung specific instructions.

Good luck!

--wally.

---

### Post by ukripper on 2009-11-17
Here is bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/306004](https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/306004)

---

