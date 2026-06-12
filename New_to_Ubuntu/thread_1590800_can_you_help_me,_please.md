---
title: "can you help me, please"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by zazlox on 2010-10-08
I'm having a big problem with checkbox , everytime , I install something like a program or a package , i have this message


E: checkbox: subprocess installed post-installation script returned error exit status 1
E: checkbox-cli: dependency problems - leaving unconfigured
E: checkbox-gtk: dependency problems - leaving unconfigured
E: hwtest: dependency problems - leaving unconfigured
E: hwtest-cli: dependency problems - leaving unconfigured
E: hwtest-gtk: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

*****************************************
also when i try to use the application "system>administration>system testing.

it won't work

I don't know exactly how to fix this problem.

i'm using ubuntu 9.10

uname -r output : 2.6.31-22-generic


i need your help , please . i'm a beginner , i like ubuntu or you can say linux OS , i don't to go back to windows anymore.

---

### Post by k33bz on 2010-10-08
What exactly are you trying to install, and where did you get it from?

---

### Post by andrewthomas on 2010-10-08
try 

```
sudo apt-get install -f
```

and 

```
sudo dpkg --configure -a
```

and post any errors

---

### Post by zazlox on 2010-10-08
andrewthomas
..............

that's the results

samir@samir-desktop:~$ sudo apt-get install -f
[sudo] password for samir: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up checkbox (0.8.6) ...
Traceback (most recent call last):
  File "/usr/share/checkbox/install/config", line 15, in <module>
    from debconf import Debconf, DebconfCommunicator
ImportError: No module named debconf
dpkg: error processing checkbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of checkbox-cli:
 checkbox-cli depends on checkbox (= 0.8.6); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-gtk:
 checkbox-gtk depends on checkbox (= 0.8.6); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest:
 hwtest depends on checkbox; however:
  Package checkbox is not configured yet.
dpkg: error processing hwtest (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest-cli:
 hwtest-cli depends on checkbox-cli; however:
  Package checkbox-cli is not conNo apport report written because the error message indicates its a followup error from a previous failure.
                                                           No apport report written because the error message indicates its a followup error from a previous failure.
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             figured yet.
dpkg: error processing hwtest-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest-gtk:
 hwtest-gtk depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
dpkg: error processing hwtest-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 checkbox
 checkbox-cli
 checkbox-gtk
 hwtest
 hwtest-cli
 hwtest-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
samir@samir-desktop:~$ 
**************************
samir@samir-desktop:~$ sudo dpkg --configure -a
Setting up checkbox (0.8.6) ...
Traceback (most recent call last):
  File "/usr/share/checkbox/install/config", line 15, in <module>
    from debconf import Debconf, DebconfCommunicator
ImportError: No module named debconf
dpkg: error processing checkbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hwtest:
 hwtest depends on checkbox; however:
  Package checkbox is not configured yet.
dpkg: error processing hwtest (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-cli:
 checkbox-cli depends on checkbox (= 0.8.6); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-gtk:
 checkbox-gtk depends on checkbox (= 0.8.6); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest-cli:
 hwtest-cli depends on checkbox-cli; however:
  Package checkbox-cli is not configured yet.
dpkg: error processing hwtest-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest-gtk:
 hwtest-gtk depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
dpkg: error processing hwtest-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 checkbox
 hwtest
 checkbox-cli
 checkbox-gtk
 ubuntu-desktop
 hwtest-cli
 hwtest-gtk
samir@samir-desktop:~$ 
***************************************

actually , i wasn't trying to install anything. 

in synaptic , there is no broken package

---

### Post by sikander3786 on 2010-10-08
Try

```
sudo aptitude install -f
```

Aptitude works better with dependencies for me.

---

### Post by zazlox on 2010-10-08
sikander3786
..........

i'm trying now this command


sudo aptitude install -f


i'll answer you back , if it works or not

thank you

---

### Post by zazlox on 2010-10-08
I still have the same error message concernig checkbox

Setting up kde-l10n-engb (4:4.3.2-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for python-support ...
Errors were encountered while processing:
 checkbox
 checkbox-cli
 checkbox-gtk
 hwtest
 hwtest-cli
 hwtest-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up checkbox (0.8.6) ...
Traceback (most recent call last):
  File "/usr/share/checkbox/install/config", line 15, in <module>
    from debconf import Debconf, DebconfCommunicator
ImportError: No module named debconf
dpkg: error processing checkbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hwtest:
 hwtest depends on checkbox; however:
  Package checkbox is not configured yet.
dpkg: error processing hwtest (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-cli:
 checkbox-cli depends on checkbox (= 0.8.6); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-gtk:
 checkbox-gtk depends on checkbox (= 0.8.6); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest-cli:
 hwtest-cli depends on checkbox-cli; however:
  Package checkbox-cli is not configured yet.
dpkg: error processing hwtest-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest-gtk:
 hwtest-gtk depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
dpkg: error processing hwtest-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 checkbox
 hwtest
 checkbox-cli
 checkbox-gtk
 ubuntu-desktop
 hwtest-cli
 hwtest-gtk
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

samir@samir-desktop:~$ 


I used all those commands but i still got the same problem

---

### Post by sikander3786 on 2010-10-08
Try

```
sudo apt-get install --reinstall checkbox hwtest checkbox-cli checkbox-gtk ubuntu-desktop hwtest-cli hwtest-gtk
```

If it still doesn't work, I doubt you'll have to either reinstall or do it the ugly way. See post # 5 in the following thread. You can wait for some other replies but I am out of ideas for now...

[http://www.ubuntuforums.org/showthread.php?t=1580470](http://www.ubuntuforums.org/showthread.php?t=1580470)

After you've done that, do all these commands.

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get install -f
```

---

### Post by zazlox on 2010-10-08
sikander
..........


thanks a lot for helping me.

i'll try those tips


just an information , i was googling , and i find a trick , i tried it 

and i don't recieve anymore this error message from checkbox

i used this command
sudo apt-get purge checkbox


i'm just asking if this command will harm my system or make it acting badly

i don't know what exactly did , i think it desinstall the package chekbox & checkbox-gtk

---

### Post by sikander3786 on 2010-10-08
It will uninstall all the package checkbox with all its configuration. Then you will need to reinstall it. No harm at all.

---

### Post by zazlox on 2010-10-08
sikander3786
..................

thanks a lot for everything

the link yu gave me , it was very useful

i solved the problem

and also those commands helped too

i found it googling

cd /var/lib/dpkg
mv status status-bad
cp status-old status

apt-get update
......................................

however , thanks a lot , it's very kind of you

---

