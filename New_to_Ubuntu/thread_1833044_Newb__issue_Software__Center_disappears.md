---
title: "Newb  issue: Software  Center disappears"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by Boppa on 2011-08-25
Yes, I'm very unschooled about any computer language so be gentle:  I'm running 11.04 and while its working, when I  go to  download additional software (like Chrome) the  Software Center/Download manager shows for less than a second and then disappears. Nothing is available. Since I have Firefox, I can see where it  is downloaded  but when  I click on to open/install, there's the disappearing Software Center...

Any child-like English help is/would be greatly appreciated!

---

### Post by jerrrys on 2011-08-25
open a terminal and enter:

software-center

and post any errors

---

### Post by Boppa on 2011-08-25
@dad-FJ373AA-ABA-SR5501P:~$ software-center
2011-08-25 14:17:57,504 - softwarecenter.db - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 142, in open
    axi = xapian.Database("/var/lib/apt-xapian-index/index")
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3458, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
/usr/share/software-center/softwarecenter/app.py:1190: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-08-25 14:17:58,248 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-08-25 14:17:58,248 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
2011-08-25 14:17:58,258 - softwarecenter.app - INFO - software-center-agent finished with status 0
2011-08-25 14:17:58,259 - softwarecenter.db - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 142, in open
    axi = xapian.Database("/var/lib/apt-xapian-index/index")
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3458, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
2011-08-25 14:17:58,391 - softwarecenter.view.catview - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
Segmentation fault
@dad-FJ373AA-ABA-SR5501P:~$ 

Now thats a  lot to  read!

---

### Post by jerrrys on 2011-08-25
first off, lets install a backup package manager:

sudo apt-get install synaptic

now to try a couple of fixes...

enter these commands one at a time:

sudo rm /var/cache/apt/*.bin

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

and now try the software center again

---

### Post by Boppa on 2011-08-25
I'm assuming that I open another terminal and paste in the SUDO command. I  get this  when I do:
@dad-FJ373AA-ABA-SR5501P:~$ sudo apt-get install synaptic
[sudo] password for dad: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
@dad-FJ373AA-ABA-SR5501P:~$ 

thanks for your  help on this!!!!!!

---

### Post by jerrrys on 2011-08-25
do what it said

sudo dpkg --configure -a

edit:  you do not need to open a separate terminal for each command

---

### Post by Boppa on 2011-08-25
Jerrys, you are AWESOME!!! Thank you so much, it works!!!

---

### Post by jerrrys on 2011-08-25
and welcome to the forum :)

---

