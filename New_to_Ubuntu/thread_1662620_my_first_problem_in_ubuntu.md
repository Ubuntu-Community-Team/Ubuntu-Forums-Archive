---
title: "my first problem in ubuntu"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by star123 on 2011-01-08
hello every1..i switched to ubuntu 2day n 2day itself i found a problem... i downloaded activeperl 5.12 from a website..please note this perl is for linux and so there is no problem with software...it is a zipped filed extension.. i extracted the contents in my home folder.. installation is by terminal.. 
sh install.sh then the option is to enter the top level directory ..please tell what directory should i give so that it is installed properly.. i tried /home/ActivePerl-5.12 but it doesnt work.. please help:confused::confused::confused:

---

### Post by oldos2er on 2011-01-08
[http://docs.activestate.com/activeperl/5.12/install.html#installing](http://docs.activestate.com/activeperl/5.12/install.html#installing) activeperl on linux (x86)

It says there's a *.deb available; I'd give that a try first (might be easier).

---

### Post by vivek.pandey on 2011-01-08
% dpkg -i ActivePerl-5.12.2.1203-i686-linux.deb

---

### Post by star123 on 2011-01-08
> **oldos2er said:**
> [http://docs.activestate.com/activeperl/5.12/install.html#installing](http://docs.activestate.com/activeperl/5.12/install.html#installing) activeperl on linux (x86)

It says there's a *.deb available; I'd give that a try first (might be easier).

thanx for your help

i went through a similar procedure as given on the page for which you provided the link but problem is same.installation reqiures to enter a top level directory and as given on the page i enterd /home/ActivePerl -5.12/but same error... since i have gone through half way i want to contnue this installation

---

### Post by TheTFo on 2011-01-08
Did you install from the .deb?  I don't think so.

Is this the directory you seek?

/opt/ActivePerl-5.12

---

### Post by star123 on 2011-01-08
> **TheTFo said:**
> Did you install from the .deb?  I don't think so.

Is this the directory you seek?

/opt/ActivePerl-5.12

yes i see that directory here is the screenshot of wats going on

Enter top level directory for install? [/opt/ActivePerl-5.12] [SIZE="5"][SIZE="6"]HERE IS THE PROBLEM[/SIZE][/SIZE]

    The ActivePerl documentation is available in HTML format.  If installed
    it will be available from file:///opt/ActivePerl-5.12/html/index.html.
    If not installed you will still be able to read all the basic perl and
    module documentation using the man or perldoc utilities.

Install HTML documentation [yes] y
Ok.

    The typical ActivePerl software installation requires 200 megabytes.
    Please make sure enough free space is available before continuing.

Proceed? [yes] y
Ok.

Installing ActivePerl...
Copying files to /opt/ActivePerl-5.12...
Install of ActivePerl to /opt/ActivePerl-5.12 failed:

    mkdir /opt/ActivePerl-5.12: Permission denied at perl/lib/ActiveState/RelocateTree.pm line 388

    Sorry about the inconvenience.  If this looks like a problem with
    the installer please report it to the ActivePerl bug database,
    available online at:

        [http://bugs.ActiveState.com/ActivePerl/](http://bugs.ActiveState.com/ActivePerl/)

    For general questions or comments about ActivePerl, please contact
    us at <support@activestate.com>.

    Thank you for trying to install ActivePerl!

---

### Post by oldos2er on 2011-01-08
To enable write access to /opt, run the install script with sudo. **sudo sh ./install.sh**

---

### Post by star123 on 2011-01-08
> **oldos2er said:**
> To enable write access to /opt, run the install script with sudo. **sudo sh ./install.sh**

Thanx a lot it worked..but i have a doubt...i was already logged in admin account so y at all i needed sudo there??

---

### Post by oldos2er on 2011-01-08
The root account is locked by default in Ubuntu. Are you saying you enabled the root account, logged into it, and ran the command? If so you wouldn't have received the error "Permission denied...."

The user account you create when installing Ubuntu is given admin privileges, but you need to use "sudo" (or gksudo for GUI programs) to access them.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

