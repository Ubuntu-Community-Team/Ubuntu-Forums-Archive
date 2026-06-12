---
title: "Screwed up my repository"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by myolbug on 2009-08-11
I get this error message:

**An unresolvable problem occurred while initializing the package information.**

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '‘deb-src' is not known on line 52 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

How do I correct this?

---

### Post by WRDN on 2009-08-11
Could you post the contents of your sources.list file please?

---

### Post by myolbug on 2009-08-11
> **WRDN said:**
> Could you post the contents of your sources.list file please?

Sure, what is the command?

---

### Post by WRDN on 2009-08-11
Post the output of:

```
cat /etc/apt/sources.list
```

Or just copy the text after opening the file in a text editor.

---

### Post by myolbug on 2009-08-11
Thank you, Here it is:

randy@randy-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide usefgksudo gedit /etc/apt/sources.list
 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free # disabled on upgrade to jaunty
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free # disabled on upgrade to jaunty
‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’
‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’
‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’

---

### Post by jrothwell97 on 2009-08-11
You can do this two ways: firstly, you can go there using your file browser. From the Places menu select Computer, then Filesystem. Double-click etc, then apt, then open sources.list and copy it here.

If you think that's a bit long winded, go to Applications/Terminal and type

```
cat /etc/apt/sources.list
```

---

### Post by mgmiller on 2009-08-11
Open a terminal and make it nice and wide.  Then enter the command:
```
cat /etc/apt/sources.list
```

Copy and past the output to here.

---

### Post by jrothwell97 on 2009-08-11
The problem here seems to be that the last lines have quotes around them. Delete the quote marks at the beginning and end of these lines, and run sudo apt-get update again.

---

### Post by myolbug on 2009-08-11
This is exactly what I get:

randy@randy-desktop:~$ sudo su
root@randy-desktop:/home/randy# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

---

### Post by mgmiller on 2009-08-11
These last 3 lines are a problem.  They have a truncated ... in the middle that can't be right and all 3 lines are the same.

Also, they start and end with ['] which is probably the source of your error message.

```
‘deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu") jaunty main’
‘deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu") jaunty main’
‘deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu") jaunty main’
```

Just open the file in your favorite editor and put a # in front of those 3 lines if you don't want to erase them altogether.

Then run a:
```
sudo apt-get update
```
and the error message should stop.

---

### Post by myolbug on 2009-08-11
> **jrothwell97 said:**
> The problem here seems to be that the last lines have quotes around them. Delete the quote marks at the beginning and end of these lines, and run sudo apt-get update again.


I can't remember how to get this into the editor.

---

### Post by mgmiller on 2009-08-11
Assuming you are running Ubuntu and not kubuntu:
```
sudo gedit /etc/apt/sources.list
```If you are running kubuntu it would be:
```
kdesu kate /etc/apt/sources.list
```

---

### Post by myolbug on 2009-08-11
Cool, that has worked, however, I am now getting this?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

---

### Post by mgmiller on 2009-08-11
That's not actually the end of the world.  It just means you did not enter the GPG key when you enabled that repository.  That message can be safely ignored.

If however, you want to add the key, you will need to go back to the launchpad and look for their instructions on how to add the gpg key.

Here is where to get the info from:
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by mgmiller on 2009-08-11
Sorry.  I think the site I sent you to in my last post is not very helpful.  Try this one instead:
[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by myolbug on 2009-08-11
Thanks Much!  I'll work on it from here!

---

### Post by mgmiller on 2009-08-11
This guy actually wrote a script that seems to automate the process:
[http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/](http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/)

---

### Post by myolbug on 2009-08-11
Wow, that is a LOT more than I want to get into at this time.  Is there a way to delete it and eliminate the message?

---

### Post by jrothwell97 on 2009-08-11
You can just ignore the message. It's only to warn you that the packages haven't been verified, and as long as you trust where you're downloading from, you should be safe.

---

### Post by mgmiller on 2009-08-11
For an easy way to disable the repository till you want to work on it, just go to System > Administration > Software Sources.

Click on the "Third-Party Software" tab.

Uncheck the repository you want to ignore for now.

When you click "Close" it will tell you it needs to reload the repository information or some such.  Just Ok it and wait for it to finish.  The window will close by itself when it's done.

---

### Post by myolbug on 2009-08-11
> **mgmiller said:**
> For an easy way to disable the repository till you want to work on it, just go to System > Administration > Software Sources.

Click on the "Third-Party Software" tab.

Uncheck the repository you want to ignore for now.

When you click "Close" it will tell you it needs to reload the repository information or some such.  Just Ok it and wait for it to finish.  The window will close by itself when it's done.

Ahh, THANK YOU!  It is so obvious, I don't know why I didn't see it.  Thanks again!

---

