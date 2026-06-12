---
title: "updated firefox to 3.5.5 ubuntuzilla errors"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Alex82 on 2009-11-26
After update I keep getting the following error and cant use package manager or firefox?

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 51 in source list /etc/apt/sources.list, E:The list of sources could not be read.


cat/etc/apt/sources.list returns

alex@alex-laptop:~$ 
alex@alex-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/apt) all main
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29



alex@alex-laptop:~$

---

### Post by sandyd on 2009-11-26
> **Alex82 said:**
> After update I keep getting the following error and cant use package manager or firefox?

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 51 in source list /etc/apt/sources.list, E:The list of sources could not be read.


cat/etc/apt/sources.list returns
```

alex@alex-laptop:~$ 
alex@alex-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/apt) all main
**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29**

```


alex@alex-laptop:~$
```
gksudo gedit /etc/apt/sources.list
```remove this line from the bottom```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```and then save, close and run this
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

```& please wrap the output in [code] tags in the future.

---

### Post by bwang on 2009-11-26
Run
```
sudo gedit /etc/apt/sources.list
```
and delete the last line (the one with 'sudo' in it)

---

### Post by kansasnoob on 2009-11-26
> **bwang said:**
> Run
```
sudo gedit /etc/apt/sources.list
```
and delete the last line (the one with 'sudo' in it)

+1!

That doesn't belong there.

---

### Post by Alex82 on 2009-11-27
ok did all that and package manager now works again. computer tells me firefox 3.5.5 is installed (dont know where)

When I click the fire fox button on my application bar nothing happens?[http://www.google.com.au/firefox?client=firefox-a&rls=org.mozilla:en-GB:official](http://www.google.com.au/firefox?client=firefox-a&rls=org.mozilla:en-GB:official)

---

### Post by Alex82 on 2009-11-27
I now have firefox working again but it is still version 3.0.15. how do I get 3.5.5 to replace this?

thanks

---

### Post by wilee-nilee on 2009-11-27
Right click on the applications for edit menus then click on Internet and see if it is there and just needs to be clicked off then on to show in the menu . If not click on Internet again with the menu edit open then new item then browse at the right of command then go to files-user-bin and look for the Firefox bin in the list and click on it then name the launcher and you should be set.

---

### Post by Alex82 on 2009-11-27
I cant seem to find the new install of 3.5.5 at the moment I am running 3.0.15 from usr/lib/firefox3.0.15/firefox

---

### Post by wilee-nilee on 2009-11-27
> **Alex82 said:**
> I cant seem to find the new install of 3.5.5 at the moment I am running 3.0.15 from usr/lib/firefox3.0.15/firefox

Did you try my post.

---

### Post by Alex82 on 2009-11-27
Sorry yes I did and fire fox refuses to start....


when I ubuntuzilla.py -a checkforupdatetext -p firefox in the terminal I get...

The version of Firefox currently installed is /opt/firefox/firefox-bin: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory
The latest version available from Mozilla is 3.5.5

but i have installed this already?

---

### Post by wilee-nilee on 2009-11-27
I  am not a command line user much so I don't really have an answer beyond the ones I have given, but there are many on the forum who can help so I think you will get some help.

---

### Post by Alex82 on 2009-11-27
no problem thanks for the help I think i will try to wipe and install it again and see what happens.

---

### Post by wilee-nilee on 2009-11-27
If your just going to wipe install the ppa links.
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)

This should add FF 3.5 to synaptic or you can input from the terminal after updating do you know how to do this and add he keys.

---

### Post by wilee-nilee on 2009-11-27
Edit: computer hang caused double post.

---

### Post by Alex82 on 2009-11-27
> **wilee-nilee said:**
> If your just going to wipe install the ppa links.
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)

This should add FF 3.5 to synaptic or you can input from the terminal after updating do you know how to do this and add he keys.


Not sure how you do that no, I just reinstalled from ubuntuzilla and was told it was a success.  Restarted firefox and still running version 3.0.15?
could it be a hardy heron or 64bit problem?

---

### Post by wilee-nilee on 2009-11-27
> **Alex82 said:**
> Not sure how you do that no, I just reinstalled from ubuntuzilla and was told it was a success.  Restarted firefox and still running version 3.0.15?
could it be a hardy heron or 64bit problem?

It has been a couple of years that I have used ubuntzilla so I don't remember the details.
But here is a page from ubuntzilla that has instructions for the ppa installs.
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Have you looked in synaptic for FF 3,5

---

### Post by Alex82 on 2009-11-27
Hardy and Intrepid

    Release time-frame: TBA
    The Ubuntu Mozilla Team is working to make Firefox 3.5 available for older releases. 

When you have installed the new package, a new icon will appear in Applications > Internet alongside your old Firefox icon. The name is based on the codename for the new Firefox release, so Firefox 3.5 was labeled Shiretoko Web Browser. If you do not like this name , install abrowser-3.5-branding and Firefox 3.5 label will be renamed to a simple Web Browser. 


not seeing any of this and cant find firefox 3.5.5 on system anywhere

---

### Post by wilee-nilee on 2009-11-27
So you did the right click on applications-edit menus then clicked on internet to see if the FF3.5 icon was there sometimes with a new install it is there but you have to uncheck then check it again to get it to show in the menu.

The ppa links are the easiest way to do this and once you do it a couple of times you will have the hang of it. I am not real good at giving descriptions of the process and how to add keys so hopefully somebody will give you this help. I do it the long way by adding the debs to the source list and save the keys in a gedit file in home then add the keys to the source list. There are wget ways to do this that I have never bothered to learn so if somebody helps you it will probably be in that format. 

Sorry man you will be set up within he next 24 hours at the most when people who can give you better instructions come back on line.

What I do these days is install Ubuntu Tweak and let it do all the work of adding ppa's and keys, I am just plain lazy. ;)

---

### Post by Norm24 on 2009-11-27
You may wish to try this also:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

This method worked great for me.

---

### Post by nanotube on 2009-11-30
> **Alex82 said:**
> Not sure how you do that no, I just reinstalled from ubuntuzilla and was told it was a success.  Restarted firefox and still running version 3.0.15?
could it be a hardy heron or 64bit problem?

first: when you say "i reinstalled from ubuntuzilla", you mean that you ran "ubuntuzilla.py -a install -p firefox", and it went through the install process, and said all's well. correct? you didn't just install the ubuntuzilla package and leave it at that, right?

second: when you 'restart firefox' make sure you completely quit firefox, and check that all firefox processes are gone with command:
```
ps ax |grep firefox
```

then start firefox again, and that should fire up the ubuntuzilla-installed version, which should be 3.5.5.

---

