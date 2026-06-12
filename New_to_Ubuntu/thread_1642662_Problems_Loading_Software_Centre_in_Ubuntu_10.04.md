---
title: "Problems Loading Software Centre in Ubuntu 10.04"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by tesex167 on 2010-12-10
When I click on Ubuntu Software Centre in the Applications menu it fails to open despite being able to open before.  What has gone wrong?

Also I cannot open the Synaptic Package manager in the System>Administration menu.  Instead I get the following error message;

E: Syntax error /etc/apt/apt.conf.d/99synaptic:5: Extra junk at end of file

Are these two problems related and how can they be resolved?

---

### Post by bwhite82 on 2010-12-10
> **tesex167 said:**
> When I click on Ubuntu Software Centre in the Applications menu it fails to open despite being able to open before.  What has gone wrong?

Also I cannot open the Synaptic Package manager in the System>Administration menu.  Instead I get the following error message;

E: Syntax error /etc/apt/apt.conf.d/99synaptic:5: Extra junk at end of file

Are these two problems related and how can they be resolved?

Hi,

Can you attach the aforementioned "apt.conf" here? I will analyze to see the problem. Also in a terminal shell, type the following:

software-center

And post the results of that command here.

---

### Post by tesex167 on 2010-12-10
thanks soldierboy.  Here is what I get in terminal when I type software-center;

ubuntu@ubuntu:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:5: Extra junk at end of file
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 53, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 19, in <module>
    import fileutils
  File "/usr/lib/python2.6/dist-packages/apport/fileutils.py", line 15, in <module>
    from packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:5: Extra junk at end of file

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:5: Extra junk at end of file



P.S.  if required how do I locate/attach the apt.conf?

---

### Post by bwhite82 on 2010-12-10
Your reply above confirms that the problem is affecting both applications. Go back to the terminal and type this (just copy and paste it):

cp /etc/apt/apt.conf.d/99synaptic ~/apt.txt

Then when you are replying here, click on "manage attachments" then "add file" and add the "apt.txt" file.

---

### Post by sandyd on 2010-12-10
> **tesex167 said:**
> thanks soldierboy.  Here is what I get in terminal when I type software-center;

ubuntu@ubuntu:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:5: Extra junk at end of file
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 53, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 19, in <module>
    import fileutils
  File "/usr/lib/python2.6/dist-packages/apport/fileutils.py", line 15, in <module>
    from packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:5: Extra junk at end of file

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:5: Extra junk at end of file



P.S.  if required how do I locate/attach the apt.conf?
```

sudo nano /etc/apt/apt.conf.d/99synaptic

```
theirs an extra blank line at the end of the file.
go to the end using your arrow keys, and delete the blank line.

---

### Post by bwhite82 on 2010-12-10
sandyd may very well have the answer and much more eloquently I might add! When I saw "junk" I was thinking some random characters were inserted somehow. Let us know if that fixed it.

---

### Post by tesex167 on 2010-12-11
ok this is what I get when I type in 'sudo nano /etc/apt/apt.conf.d/99synaptic' in terminal;

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL



this includes a blank line at the end.  I have tried deleting the blank line just using backspace and saving but it has no effect (the blank line keeps appearing when I run the command in terminal again).  Is there a 'proper' alternative way to delete the blank line?

---

### Post by arjunlalb on 2010-12-11
blank lines doesnt cause problems usually,ryt?? :-o

---

### Post by sandyd on 2010-12-11
> **tesex167 said:**
> ok this is what I get when I type in 'sudo nano /etc/apt/apt.conf.d/99synaptic' in terminal;

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL



this includes a blank line at the end.  I have tried deleting the blank line just using backspace and saving but it has no effect (the blank line keeps appearing when I run the command in terminal again).  Is there a 'proper' alternative way to delete the blank line?

ok. THAT file shouldn't be there.
thats part of the /etc/sudoers file, which I have no idea how it got to where it is right now.

your going to have to do this.

1. ask another forum member (I don't use ubuntu, so....) to post the output of
```

cat /etc/apt/apt.conf.d/99synaptic

```
run
```

sudo mv /etc/apt/apt.conf.d/99synaptic /etc/apt/apt.conf.d/99synaptic.bak

sudo nano /etc/apt/apt.conf.d/99synaptic

```
then paste the output into the screen.

---

### Post by tesex167 on 2010-12-12
I typed in the following in terminal;

gksudo software-center

and here is what I get;

Traceback (most recent call last):  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:11: Extra junk at end of file
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 53, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 19, in <module>
    import fileutils
  File "/usr/lib/python2.6/dist-packages/apport/fileutils.py", line 15, in <module>
    from packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:11: Extra junk at end of file

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 36, in <module>
    apt_pkg.init()
SystemError: E:Syntax error /etc/apt/apt.conf.d/99synaptic:11: Extra junk at end of file


Result: software center still not working and therefore any ideas on how to fix this problem would be much appreciated...

Thanks

---

### Post by tajiknomi on 2010-12-12
[SIZE=2]Write in terminal and paste the output here

 [/SIZE]```
[SIZE=3]gedit /etc/apt/apt.conf.d/99synaptic[/SIZE]
```

---

### Post by madjr on 2010-12-12
it may be a bug, you can see if someone has reported it or you can report it.

[https://bugs.launchpad.net/ubuntu/+source/software-center](https://bugs.launchpad.net/ubuntu/+source/software-center)


last fix, would be just to reinstall ubuntu.

---

### Post by tesex167 on 2010-12-12
tajiknomi:  my output in gedit;



# tty3 - getty
#
# This service maintains a getty on tty3 from the point the system is
# started until it is shut down again.

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /bin/login -f ubuntu </dev/tty3 > /dev/tty3 2>&1

---

### Post by tajiknomi on 2010-12-12
> **tesex167 said:**
> tajiknomi:  my output in gedit;



# tty3 - getty
#
# This service maintains a getty on tty3 from the point the system is
# started until it is shut down again.

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /bin/login -f ubuntu </dev/tty3 > /dev/tty3 2>&1

[SIZE=2]In my case the Output is:-

"APT::Install-Recommends "true";"[/SIZE]
[SIZE=2]
Note sure what the problem is,but the message which i read in your output(in 1st post) that their is something ***broken*** here..

Ok, 1st make a ***backup*** of your file so that you can edit then

[/SIZE]```
[SIZE=2]sudo cp /etc/apt/apt.conf.d/99synaptic /etc/apt/apt.conf.d/99synaptic_backup[/SIZE]
```[SIZE=2]Once you had done that...then try this

[/SIZE]```
sudo gedit /etc/apt/apt.conf.d/99synaptic
```[SIZE=2]And remove all the stuff their, [/SIZE]

[SIZE=2]and ***edit*** their[/SIZE] > "[SIZE=3] APT::Install-Recommends "true";[/SIZE] "
[SIZE=2]Without Quotation,and then try again[/SIZE]...

---

### Post by tesex167 on 2010-12-12
Hi tajiknomi,

I tried that but I still can't get software-center to load

---

### Post by tajiknomi on 2010-12-12
> **tesex167 said:**
> Hi tajiknomi,

I tried that but I still can't get software-center to load

[SIZE=2]What error did you get this time...from terminal...?

Moreover, i had attached my ***99synaptic-file, ***Make sure that you had Edited Exactly as mine ...

click on this link > [/SIZE][http://dl.dropbox.com/u/16158781/99synaptic](http://dl.dropbox.com/u/16158781/99synaptic)

---

### Post by s.fox on 2010-12-12
Please do not create duplicate threads on the same problem. Thank you.

Threads Merged.

---

### Post by MSEslacker on 2012-01-15
Hey.

Similar problem as originally reported by tesex167 on 12/10/2010.
A full year old...maybe time to start a new thread.

I wasn't using Software Center.  I used Synaptic, under the System menu on Xubuntu 11.10 (Oneiric).
But similar problem, failing with "Extra junk at end of file" in 99synaptic.

Problem arose after attempting to install RealPlayer's linux version (may be unrelated?).
RP is available here as a .deb package: [http://uk.real.com/realplayer/other-versions](http://uk.real.com/realplayer/other-versions)
Command line I used, in ~/Downloads, was: sudo dpkg -i RealPlayer11GOLD.deb
This failed, complaining of missing dependency package lsb.

I tried to run Synaptic and install LSB (Linux Standard Base).  
But synaptic wouldn't run:
E: Syntax error /etc/apt/apt.conf.d/99synaptic:1: Extra junk at end of file
And Synaptic closed immediately.

My 99synaptic file only contained 1 line, as follows (this is the output of `more 99synaptic`):
 mozilla/AOL_Time_Warner_Root_Ce
(that's the full text, complete with leading space)

Temporary workaround: I copied 99synaptic to 99synaptic.bak, removed 99synaptic, and tried again.
This time Synaptic worked with no problem.
I got LSB and dependencies installled.   Installed Realplayer with dpkg (as before).

So, what does 99synaptic actually do?  Synaptic seems to get by just fine without it...
Will it be re-generated by Synaptic if it's needed again?
And where can I find a copy of 99synaptic as it should look on a fresh installation?

---

### Post by bluexrider on 2012-01-15
> **tajiknomi said:**
> [SIZE=2]What error did you get this time...from terminal...?

Moreover, i had attached my ***99synaptic-file, ***Make sure that you had Edited Exactly as mine ...

click on this link > [/SIZE][http://dl.dropbox.com/u/16158781/99synaptic](http://dl.dropbox.com/u/16158781/99synaptic)
Error 404 on your link, please check and revise.

---

### Post by rossmurray on 2012-04-12
You still had a problem with this issue? After hours of searching for this problem I also noticed that my applications were having trouble being found in Unity too. And I may have stumbled upon the answer to your problem. Seems that the cache of Software Center got corrupted for me and I could remove the cache to essentially reset it.

In terminal type the following command:
```
rm -r ~/.cache/software-center
```

Anyway I finally have Software Center back up and running but can't see the apps folder yet. Hope this works for you too.

---

