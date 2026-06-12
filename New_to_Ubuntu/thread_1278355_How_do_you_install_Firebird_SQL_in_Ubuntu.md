---
title: "How do you install Firebird SQL in Ubuntu?"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by Don Bowen on 2009-09-29
How do you install a program in Ubuntu?

Specifically, I'm trying to install the Firebird SQL software.  
coming from windows, i'm looking for there to be a "setup" or "install" program, and there's nothing like that.

I've figured out that going to Applications, accessories, terminal gets me the CLI interface, but ...what then?

history: bought all versions of MSDOS as they came out, bought windows 1.0.
learned to program with Turbo Pascal 1.0, bought every subsequent version of windows 
as it came out.  learned to program in C++ with Borland products.

---

### Post by howefield on 2009-09-29
> **Don Bowen said:**
> How do you install a program in Ubuntu?

Specifically, I'm trying to install the Firebird SQL software.

I do not know the program, but have you tried Synaptic Package Manager, is this what you need ?

firebird2.1-super


Or if you prefer, with the terminal

sudo apt-get install firebird2.1-super

---

### Post by marshmallow1304 on 2009-09-29
There are a few ways.

1. System -> Administration -> Synaptic Package Manager
Start typing what you're looking for in the quick search bar and see what comes up.

2. Applications -> Add/Remove
A bit more "user-friendly", but not as much info.

3. If you know exactly what package(s) you need, you can install from the command line.
```
sudo apt-get install <package1> <package2> <package3>
```


If the software you want is not in the repositories (i.e. not installable by the above methods), you can look for a .deb package from the software's website or even source code; there are many howtos about compiling.

---

### Post by Don Bowen on 2009-09-29
here's a quote from an error message that is probably the result of trying to install something incorrectly.

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

OK...great... I can presume that there is a text file at /etc/apt/sources.list that has bad information in it.  
I can presume "sources.list" is the name of the file.
If my computer doesn't like what's in that file... what should be in that file?
can it be blank?
I can also guess that I should edit that file so that it contains
'sudo apt-get update' and 'sudo apt-get install -f'.
I wonder how I can browse to that file?
How do I edit it once I find it?

---

### Post by halitech on 2009-09-29
Found this...

[http://www.firebirdsql.org/index.php?op=files&id=engine_213](http://www.firebirdsql.org/index.php?op=files&id=engine_213)

Look under Linux for the compressed tarball and download the one you need (ie. x86 or AMD64) after you extract it, look in the folder for a read me for install instructions

---

### Post by halitech on 2009-09-29
> **Don Bowen said:**
> here's a quote from an error message that is probably the result of trying to install something incorrectly.

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

OK...great... I can presume that there is a text file at /etc/apt/sources.list that has bad information in it.  
I can presume "sources.list" is the name of the file.
If my computer doesn't like what's in that file... what should be in that file?
can it be blank?
I can also guess that I should edit that file so that it contains
'sudo apt-get update' and 'sudo apt-get install -f'.
I wonder how I can browse to that file?
How do I edit it once I find it?

no, you don't want to edit the file and add that info, it will break things worse. In the terminal, run
```
sudo apt-get update && sudo apt-get install -f
```
post any output here if there are errors as well as the output of
```
cat /etc/apt/sources.list
```

---

### Post by Don Bowen on 2009-09-29
> **howefield said:**
> I do not know the program, but have you tried Synaptic Package Manager, is this what you need ?

firebird2.1-super


Or if you prefer, with the terminal

sudo apt-get install firebird2.1-super

OK...what is synaptic package manager and where may I find it?
and you write 
"or if you prefer, with the terminal"
do you mean open the terminal and go and type that line?

---

### Post by Don Bowen on 2009-09-29
> **halitech said:**
> no, you don't want to edit the file and add that info, it will break things worse. In the terminal, run
```
sudo apt-get update && sudo apt-get install -f
```post any output here if there are errors as well as the output of
```
cat /etc/apt/sources.list
```

I found someone else's instructions on how to install firebird and editted some file somewhere with the lines they suggested, and now Ubuntu add/remove programs doesn't work at all.
I presume I can fix this by deleting the ubuntu patitions (both of them) and re-installing from the CD.. (sigh)...

---

### Post by halitech on 2009-09-29
> **Don Bowen said:**
> I found someone else's instructions on how to install firebird and editted some file somewhere with the lines they suggested, and now Ubuntu add/remove programs doesn't work at all.
I presume I can fix this by deleting the ubuntu patitions (both of them) and re-installing from the CD.. (sigh)...

before you get drastic, open a terminal and post the results of
```
cat /etc/apt/sources.list
``` and we can try to fix things

---

### Post by oldos2er on 2009-09-29
> **Don Bowen said:**
> I found someone else's instructions on how to install firebird and editted some file somewhere with the lines they suggested, and now Ubuntu add/remove programs doesn't work at all.
I presume I can fix this by deleting the ubuntu patitions (both of them) and re-installing from the CD.. (sigh)...

 That would be like killing a butterfly with an H-bomb. All you need to do is get your sources.list file straightened out. Can you run this command in a terminal, and post the output here?
```
cat /etc/apt/sources.list
```

---

### Post by Michael.Godawski on 2009-09-29
hi, 
before getting frustrated because linux does not act the way you want it to,
I would have a read in the Ubuntu Pocket Guide.

[LIST]
[*][http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[/LIST]
Beside this I am sure I can leave you with alone with the help of the other helpful users.
Installing new applications is really not difficult, once you get accustomed to the new system.

---

### Post by Don Bowen on 2009-09-29
> **halitech said:**
> no, you don't want to edit the file and add that info, it will break things worse. In the terminal, run
```
sudo apt-get update && sudo apt-get install -f
```post any output here if there are errors as well as the output of
```
cat /etc/apt/sources.list
```


I'm embarrassed to say that I don't even understand what you're asking for.
you wrote "post any output here if there are erros as well as the out of ..."
Post output as a reply to this message?

---

### Post by Don Bowen on 2009-09-29
don@B1501:~$ sudo apt-get update && sudo apt-get install -f
[sudo] password for don: 
E: Type 'sudo' is not known on line 3 in source list /etc/apt/sources.list.d/firebird.list
don@B1501:~$

---

### Post by bruno9779 on 2009-09-29
the command apt-get, Add & Remove from "applications" menue and Synaptic package manager in "system">"administration" are differet interfaces for the same function.

they all look at ~/sources.list for servers where to look for packages (sw)

sources.list must not be empty, and editing it has its rationale (do not chuck things in there to see if it works, google for howtos or open a new thread)

---

### Post by bruno9779 on 2009-09-29
you are on the good direction.

now open terminal and type
```

cat /etc/apt/sources.list
```

press enter, copy the outut and post it here as a reply.

alternatively you can navigate to /etc/apt with the graphical interface, open sources list and post the content

---

### Post by Don Bowen on 2009-09-29
> **oldos2er said:**
> That would be like killing a butterfly with an H-bomb. All you need to do is get your sources.list file straightened out. Can you run this command in a terminal, and post the output here?
```
cat /etc/apt/sources.list
```

I agree, but coarse tools are all we have as beginners.  Finer adjustments come later.
Here's the output of that command you asked for:  (It's big!)

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
don@B1501:~$

---

### Post by oldos2er on 2009-09-29
> **Don Bowen said:**
>  Post output as a reply to this message?
 
 Yes. Enter this command into a terminal:
```
gksu gedit /etc/apt/sources.list.d/firebird.list
``` In front of line 3, add a comment mark # so that it looks like "# sudo...." Save and exit the file, then run
```
sudo apt-get update
```You should now be able to install Firebird.

Edit: Your sources.list looks fine.

---

### Post by bruno9779 on 2009-09-29
never mind

---

### Post by Don Bowen on 2009-09-29
I can tell it will be less work to re-install Ubuntu than to waste everyone's time here.  I don't want to wear out my welcome that quickly.  I'll be back online in about an hour after the re-install.
thank you all for your help.
I've learned a lot...especially that I shouldn't blindly follow someone's directions on how to install something... doing that wiped out the "Add/Remove Programs" feature of ubuntu.
We learn by doing.

---

### Post by Don Bowen on 2009-09-29
never mind?
should I not try what you suggested?

---

### Post by philinux on 2009-09-29
Post #17 should get you fixed.

---

### Post by bruno9779 on 2009-09-29
I edited my post to "never mind" because the answer there was already better than mine.

It is a pity that you are re-installing, people here really like it when they go crazy over someone's problem, and then... it works!! 

it feels so good!

---

### Post by j.bell730 on 2009-09-29
> **oldos2er said:**
> Yes. Enter this command into a terminal:
```
gksu gedit /etc/apt/sources.list.d/firebird.list
``` In front of line 3, add a comment mark # so that it looks like "# sudo...." Save and exit the file, then run
```
sudo apt-get update
```You should now be able to install Firebird.

Edit: Your sources.list looks fine.

No, no, follow these instructions.

---

### Post by oldos2er on 2009-09-29
> **Don Bowen said:**
> I can tell it will be less work to re-install Ubuntu than to waste everyone's time here.  I don't want to wear out my welcome that quickly.

 You're not wearing out your welcome.

 Thing is, if you reinstall Ubuntu, then try to install Firebird again, there's a good chance you'll just be running into the same problem.

 Problems with sources.list are usually easily fixed; it just seems to be time-consuming what with all the back-and-forth (which is what these fora are all about).

---

### Post by philinux on 2009-09-29
> **oldos2er said:**
> You're not wearing out your welcome.

 Thing is, if you reinstall Ubuntu, then try to install Firebird again, there's a good chance you'll just be running into the same problem.

 Problems with sources.list are usually easily fixed; it just seems to be time-consuming what with all the back-and-forth (which is what these fora are all about).

I think he's gone off to reinstall. :P

---

### Post by oldos2er on 2009-09-29
> **philinux said:**
> I think he's gone off to reinstall. :P

 D'oh!

---

### Post by juancarlospaco on 2009-09-29
I never understand why people get mad with sources.list problems, 
just calm down, relax, breath, and analyze the problem,

..**is just a list of URLs**!!!

Even if you dont have the PGP keys you will be warned several times but it works,
and the URL are the same since first release of Ubuntu, 
only change the folder by the current codename.

---

### Post by scrooge_74 on 2009-09-29
Did you get a look at the Ubuntu Guide Michael posted a bit earlier?

I think you are trying to run before you learn to walk.

Synaptic is your friend, lots of stuff there to install.  Also what is mean as sources.list is the file where the server repositories for all the stuff you want to install is located.

Also you have to remember that some apps you want to install may not be ready for the Ubuntu version you are running, you will get sometimes those weird messages about libraries or broken packages because the app coming from a third party repository or tar ball is not in line with the latest distribution.

In my particular case, all my production equipment uses stables distributions (=a bit old) so Im using currently Ubuntu Server 8.04, Debian Lenny for a mail server and this laptop, and other families laptops use Ubuntu 8.04, sometimes latest version is not for everybody (you may run into problems with video drivers for example or some inestability)

Still have fun and welcome

---

### Post by Don Bowen on 2009-09-30
OK..tried that.
typed "gksu gedit /etc/apt/sources.list.d/firebird.list" at the terminal prompt.
Doing that puts me into a text editor of some sort, with a blank page.
What line 3 did you mean exactly?  As the page is blank, there is no line 3 to modify.

> **oldos2er said:**
> Yes. Enter this command into a terminal:
```
gksu gedit /etc/apt/sources.list.d/firebird.list
``` In front of line 3, add a comment mark # so that it looks like "# sudo...." Save and exit the file, then run
```
sudo apt-get update
```You should now be able to install Firebird.

Edit: Your sources.list looks fine.

---

### Post by Don Bowen on 2009-09-30
I actually am having fun.  It's a great joy to jump into a new subject.  There are a lot of friendly folk here, and I hope to benefit from their experience.

> **scrooge_74 said:**
> Did you get a look at the Ubuntu Guide Michael posted a bit earlier?

I think you are trying to run before you learn to walk.

Synaptic is your friend, lots of stuff there to install.  Also what is mean as sources.list is the file where the server repositories for all the stuff you want to install is located.

Also you have to remember that some apps you want to install may not be ready for the Ubuntu version you are running, you will get sometimes those weird messages about libraries or broken packages because the app coming from a third party repository or tar ball is not in line with the latest distribution.

In my particular case, all my production equipment uses stables distributions (=a bit old) so Im using currently Ubuntu Server 8.04, Debian Lenny for a mail server and this laptop, and other families laptops use Ubuntu 8.04, sometimes latest version is not for everybody (you may run into problems with video drivers for example or some inestability)

Still have fun and welcome

---

### Post by Don Bowen on 2009-09-30
Good morning all...
I'm back from re-installing Ubuntu.

I found a site that explains how to install the Firebird SQL software in Ubutu even,
 the only trouble is the directions don't work.
Here's the link: ***[http://www.firebirdsql.org/manual/ubusetup.html](http://www.firebirdsql.org/manual/ubusetup.html)***

The directions say type the command

***# apt-get install firebird2-super-server***

and I'll see

***The following extra packages will be installed:***

what I get back is 

[I][B]don@B1501:~$ 
don@B1501:~$ apt-get install firebird2-super-server
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
don@B1501:~$[/B][/I] 

It occurs to me that the # part of the command may be an actual part
of the command and not the prompt...hmm... lets go try that..

Nope. PUtting a # in front of the command causes the terminal to reply
with the same prompt.  I conclude that the # denotes a comment in a
script and probably shouldn't have been included in the directions.
Any thoughts?  I'm stuck again.

---

### Post by Don Bowen on 2009-09-30
Re-installing always works.... that's why I do it.  It also ensures a clean slate so that a previous mistake doesn't influence a solution that might have worked...without that previous mistake.
I am confident that I can Install Firebird SQL on Ubuntu, all that remains is the learning how!
cheers,
DB

> **bruno9779 said:**
> I edited my post to "never mind" because the answer there was already better than mine.

It is a pity that you are re-installing, people here really like it when they go crazy over someone's problem, and then... it works!! 

it feels so good!

---

### Post by Don Bowen on 2009-09-30
putting "sudo" in front of a command seems to be a way to give yourself privileges 
you don't normally have... I'm going to go and read up on that now...

but in the directions I tried putting "sudo" in front of the first direction and got the
following output.

[I][B]don@B1501:~$ sudo apt-get install firebird2-super-server
[sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firebird2-super-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  firebird2.0-server-common
E: Package firebird2-super-server has no installation candidate
don@B1501:~$ [/B][/I]

Ubuntu starts to do something (install perhaps?) and then tells me that the package is
not available.  I've downloaded the software and de-compressed it....  maybe the 
problem is I need to refer to the directory where the files are....
Is it possible, in Terminal CLI, to change directories so the terminal program can find 
things more easily?
Is there a default location Terminal looks in?  Might make more sense to unpack the software there?

---

### Post by hotstovejer on 2009-09-30
> **Don Bowen said:**
> putting "sudo" in front of a command seems to be a way to give yourself privileges 
you don't normally have... I'm going to go and read up on that now...

but in the directions I tried putting "sudo" in front of the first direction and got the
following output.

[I][B]don@B1501:~$ sudo apt-get install firebird2-super-server
[sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firebird2-super-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  firebird2.0-server-common
E: Package firebird2-super-server has no installation candidate
don@B1501:~$ [/B][/I]

Ubuntu starts to do something (install perhaps?) and then tells me that the package is
not available.  I've downloaded the software and de-compressed it....  maybe the 
problem is I need to refer to the directory where the files are....
Is it possible, in Terminal CLI, to change directories so the terminal program can find 
things more easily?
Is there a default location Terminal looks in?  Might make more sense to unpack the software there?

Don,

That message is telling you that firebird2.0-server-common replaces firebird2-super-server in the repositories. It's apt's way of helping you find what you need, as opposed to depending on you to know the name of every package.

Try this.

```
sudo aptitude install firebird2.0-server-common
```

What this will do is install the program you are looking for, as well as any other files (known as dependencies) that the program needs. Try that, and let us know what happens.

Thanks!

Jeremy

---

### Post by Don Bowen on 2009-09-30
> **howefield said:**
> I do not know the program, but have you tried Synaptic Package Manager, is this what you need ?

firebird2.1-super


Or if you prefer, with the terminal

sudo apt-get install firebird2.1-super

Progress of the unknown kind follows:
Wow!  I was going back over the posts and came to this one and tried the command.
It put out a lot of text that looks like it might be installing the software!    
I have no idea what I just did with the command 

**sudo apt-get install firebird2.1-super**

but the show was impressive.
If it installed the software, (and that's a big if), 
1. Where did it get the software from?
2. what folder did it install to (is there a c:\program files equivalent in linux?)
3. how do I find the software to run it, if the command installed it?

Here's the output I got back.  (Linux is certainly wordy!)

[I][B]don@B1501:~$ The following extra packages will be installed:
bash: The: command not found
don@B1501:~$ 
don@B1501:~$ apt-get install firebird2-super-server
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
don@B1501:~$ sudo apt-get install firebird2.1-super
[sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firebird2.1-common firebird2.1-server-common libfbclient2
Suggested packages:
  firebird2.1-doc
The following NEW packages will be installed:
  firebird2.1-common firebird2.1-server-common firebird2.1-super libfbclient2
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 5795kB of archives.
After this operation, 13.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe firebird2.1-common 2.1.1.17910-release.ds1-1ubuntu1 [940kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe firebird2.1-server-common 2.1.1.17910-release.ds1-1ubuntu1 [603kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe libfbclient2 2.1.1.17910-release.ds1-1ubuntu1 [728kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe firebird2.1-super 2.1.1.17910-release.ds1-1ubuntu1 [3525kB]
Fetched 5795kB in 19s (299kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package firebird2.1-common.
(Reading database ... 121956 files and directories currently installed.)
Unpacking firebird2.1-common (from .../firebird2.1-common_2.1.1.17910-release.ds1-1ubuntu1_i386.deb) ...
Selecting previously deselected package firebird2.1-server-common.
Unpacking firebird2.1-server-common (from .../firebird2.1-server-common_2.1.1.17910-release.ds1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libfbclient2.
Unpacking libfbclient2 (from .../libfbclient2_2.1.1.17910-release.ds1-1ubuntu1_i386.deb) ...
Selecting previously deselected package firebird2.1-super.
Unpacking firebird2.1-super (from .../firebird2.1-super_2.1.1.17910-release.ds1-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up firebird2.1-common (2.1.1.17910-release.ds1-1ubuntu1) ...
Setting up firebird2.1-server-common (2.1.1.17910-release.ds1-1ubuntu1) ...
adduser: Warning: The home directory `/var/lib/firebird' does not belong to the user you are currently creating.

Setting up libfbclient2 (2.1.1.17910-release.ds1-1ubuntu1) ...

Setting up firebird2.1-super (2.1.1.17910-release.ds1-1ubuntu1) ...
Created default security.fdb
 * Firebird 2.1 server manager not running.
 * Not starting Firebird 2.1 server manager
 * Use `dpkg-reconfigure firebird2.1-super' to enable.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
don@B1501:~$[/B][/I]

---

### Post by semitone36 on 2009-09-30
Welcome Don and allow me to attempt to answer some of your questions.

Firstly, putting "sudo" in front of a command grants you temporary administrator privileges for the duration of the command that follows it.  Commands that alter important files in your file system (such as apt-get install) require you to use sudo before they will execute.  Its just one of the ways Linux handles security differently than windows.

> 
If it installed the software, (and that's a big if),
1. Where did it get the software from?
2. what folder did it install to (is there a c:\program files equivalent in linux?)
3. how do I find the software to run it, if the command installed it?

1.  When you type "sudo apt-get install <package>, you are telling ubuntu to reference the sources.list file to look up packages that are on the servers listed there.  If it finds the package you asked for, it will install it and also give an output of useful information pertaining to the package. (giving the output a read through is always a good idea!)

2.  Yes and no.  I have only been using linux for a little over a year and this is one area where my knowledge is still a little fuzzy.  I will let somebody else who might know more try to answer this question.

3.  First look through your applications menu and see if it has a button there.  If not, try typing "firebird" into the terminal.

---

### Post by Don Bowen on 2009-09-30
> **hotstovejer said:**
> Don,

That message is telling you that firebird2.0-server-common replaces firebird2-super-server in the repositories. It's apt's way of helping you find what you need, as opposed to depending on you to know the name of every package.

Try this.

```
sudo aptitude install firebird2.0-server-common
```What this will do is install the program you are looking for, as well as any other files (known as dependencies) that the program needs. Try that, and let us know what happens.

Thanks!

Jeremy

actually , I think I'd like the super server version.... got a command for that?

---

### Post by 3rdalbum on 2009-09-30
> **Don Bowen said:**
> Progress of the unknown kind follows:
Wow!  I was going back over the posts and came to this one and tried the command.
It put out a lot of text that looks like it might be installing the software!    
I have no idea what I just did with the command 

**sudo apt-get install firebird2.1-super**

but the show was impressive.
If it installed the software, (and that's a big if), 
1. Where did it get the software from?
2. what folder did it install to (is there a c:\program files equivalent in linux?)
3. how do I find the software to run it, if the command installed it?

It gave one error message/warning which I'm not sure relates to, but that error/warning did not stop the installation. So yes, it's installed.  It looks like you need to run the dpkg reconfigure command for this package, for some reason; in the terminal just paste this in:

```
sudo dpkg-reconfigure firebird2.1-super
```

Unusual, but hopefully this will get the software to run on bootup.

1. It got the software from the Ubuntu repositories - it's a big online catalog of software that can be easily installed within Ubuntu. If you go to System > Administration > Synaptic Package Manager you can see the entire contents of the catalog.

2. You don't need to know where it all installed to. If you want to know, then it's available under Properties in Synaptic.

3. Video tutorial in my signature for this situation, but I believe this software probably just runs constantly; it's a server. How you interact with the server is probably discussed in the documentation on the program's website, or in the "man" page.

---

### Post by semitone36 on 2009-09-30
> **Don Bowen said:**
> actually , I think I'd like the super server version.... got a command for that?

This link may help you: [https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1).

You might also want to book mark that site [http://help.ubuntu.com](http://help.ubuntu.com).  Whenever I want to install a package that isnt immediately available from the standard repositories I search the program name at the homepage and it will usually give me a pretty good howto.  

Also, be sure to read through the ubuntu [_handbook_]("http://www.ubuntupocketguide.com/index_main.html") that was mentioned earlier.  It will help you understand how/where programs are installed and also help you make sense of these commands that we are giving you

---

### Post by Don Bowen on 2009-09-30
> **3rdalbum said:**
> It gave one error message/warning which I'm not sure relates to, but that error/warning did not stop the installation. So yes, it's installed.  It looks like you need to run the dpkg reconfigure command for this package, for some reason; in the terminal just paste this in:

```
sudo dpkg-reconfigure firebird2.1-super
```Unusual, but hopefully this will get the software to run on bootup.

1. It got the software from the Ubuntu repositories - it's a big online catalog of software that can be easily installed within Ubuntu. If you go to System > Administration > Synaptic Package Manager you can see the entire contents of the catalog.

2. You don't need to know where it all installed to. If you want to know, then it's available under Properties in Synaptic.

3. Video tutorial in my signature for this situation, but I believe this software probably just runs constantly; it's a server. How you interact with the server is probably discussed in the documentation on the program's website, or in the "man" page.

That was interesting!  typing in that one command you suggested cause FireBird to run a configuration program for setting up the SQL SysDBA.  That part I'm familiar with... 
This makes me think that the software really is installed... but if it were, then there should be icons and  a CLI interface  for SQL ...somewhere... Firebird as an SQL server has a number of standard utilities that help a sysdba make the thing work.
   i'm going to reboot Ubuntu to see if that changes the available programs (now there's a MS Windows behavior for you!  reboot to see if anything changes.!)
I'll announce it joyfully if the program is installed and usable.

---

### Post by Don Bowen on 2009-09-30
After one reboot, there's still no evidence that Firebird SQL server is actually installed and running anywhere.  None of its icons show up under applications, and I can find none of the attendant CLI utilities that make Firebird a useful SQL tool.

I can only conclude that Firebird, for all this effort, is NOT installed yet, so I'd like to keep going with this thread.... I'm back to being stuck again.. so if anyone has an idea about how firebird should be installed...lets have it.

For now, I'll go back to the "how to install firebird in Linux" site and see if I can make sense out of the directions.

If I download the software and put it in a folder somewhere, shouldn't I be installing it from that folder?  Is there some way to tell Ubuntu, "hey, the software I want to install is in this folder, look there when you need something"?

What is the point of downloading something if you never tell Ubuntu that it's there and you want it installed?

---

### Post by Don Bowen on 2009-09-30
> **oldos2er said:**
> Yes. Enter this command into a terminal:
```
gksu gedit /etc/apt/sources.list.d/firebird.list
``` In front of line 3, add a comment mark # so that it looks like "# sudo...." Save and exit the file, then run
```
sudo apt-get update
```You should now be able to install Firebird.

Edit: Your sources.list looks fine.

I'm re-reading posts... I still don't understand what you meant by line 3.  Line 3 of what?
When I open terminal and type in the command you listed, Ubuntu responds by opening some sort of editor. Text Editor? with nothing in it?  Is that what you thought it would do?

---

### Post by oldos2er on 2009-09-30
The link semitone36 gave you ([https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1)) is more up-to-date than the one you referenced, Don. 

 Did you use ```
dpkg -L firebird2.1-super
``` to see where the file installed?

---

### Post by oldos2er on 2009-09-30
> **Don Bowen said:**
> I'm re-reading posts... I still don't understand what you meant by line 3.  Line 3 of what?
When I open terminal and type in the command you listed, Ubuntu responds by opening some sort of editor. Text Editor? with nothing in it?  Is that what you thought it would do?

 That was advice for your previous install of Ubuntu; it's not going to apply to a new install, since, as you pointed out, the file doesn't exist by default.

---

### Post by Don Bowen on 2009-09-30
> **oldos2er said:**
> The link semitone36 gave you ([https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1)) is more up-to-date than the one you referenced, Don. 

 Did you use ```
dpkg -L firebird2.1-super
``` to see where the file installed?

here's where it went....but how do i go there to run the programs that are there?

/.
/usr
/usr/bin
/usr/bin/gbak
/usr/bin/gdef
/usr/bin/gfix
/usr/bin/gpre
/usr/bin/qli
/usr/bin/gsec
/usr/bin/fbstat
/usr/bin/isql-fb
/usr/bin/nbackup
/usr/lib
/usr/lib/firebird
/usr/lib/firebird/2.1
/usr/lib/firebird/2.1/bin
/usr/lib/firebird/2.1/bin/fb_lock_print
/usr/lib/firebird/2.1/bin/fbserver
/usr/lib/firebird/2.1/bin/fbguard
/usr/lib/firebird/2.1/bin/fbmgr.bin
/usr/lib/firebird/2.1/bin/fbmgr
/usr/lib/firebird/2.1/UDF
/usr/lib/firebird/2.1/UDF/fbudf.so
/usr/lib/firebird/2.1/UDF/ib_udf.so
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/firebird2.1-super
/usr/share/doc
/usr/share/doc/firebird2.1-super
/usr/share/doc/firebird2.1-super/README.Debian
/usr/share/doc/firebird2.1-super/TODO.Debian
/usr/share/doc/firebird2.1-super/copyright
/usr/share/doc/firebird2.1-super/NEWS.Debian.gz
/usr/share/doc/firebird2.1-super/changelog.gz
/usr/share/doc/firebird2.1-super/changelog.Debian.gz
/etc
/etc/default
/etc/default/firebird2.1-super
/etc/init.d
/etc/init.d/firebird2.1-super

---

### Post by Don Bowen on 2009-09-30
None of those files look like "executables"...if that's the right word... What is an "executable" file in Linux anyways?  In windows/dos it's .com and .exe... is there an equivalent designation in Linux?

---

### Post by Temposs on 2009-09-30
hi Don,
   If you know which programs you want to run, just open a terminal and put the one you want to run in the command line. Anything in a "bin" directory is usually a program. So, you can just do something like:

```
/usr/bin/gpre
```

I don't really know which one you want to run, though.

---

### Post by Temposs on 2009-09-30
Don,
   You are probably wanting a GUI tool for Firebird SQL, but what you've installed so far only has command line utilities. If you want a GUI tool, the help site [https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1) recommends a program called FlameRobin.

To install FlameRobin, go to Applications->Add/Remove. Search for flamerobin. Check it and click Apply a couple times. Then it should get installed and appear in your Applications menu Applications->Programming->FlameRobin.

---

### Post by Temposs on 2009-09-30
The instructions that I gave for installed FlameRobin is how you can install most apps for Ubuntu. It really is quite easy :-)

---

### Post by oldos2er on 2009-09-30
> **Don Bowen said:**
> None of those files look like "executables"...if that's the right word... What is an "executable" file in Linux anyways?  In windows/dos it's .com and .exe... is there an equivalent designation in Linux?

 No, Linux doesn't rely on file extensions in the way DOS/Win does. "Executable" in Linux is a particular file permission setting (see [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)).

 Every file in /usr/bin should be executable. Just enter the file name in a terminal.

---

### Post by Don Bowen on 2009-09-30
> **hotstovejer said:**
> Don,

That message is telling you that firebird2.0-server-common replaces firebird2-super-server in the repositories. It's apt's way of helping you find what you need, as opposed to depending on you to know the name of every package.

Try this.

```
sudo aptitude install firebird2.0-server-common
```What this will do is install the program you are looking for, as well as any other files (known as dependencies) that the program needs. Try that, and let us know what happens.

Thanks!

Jeremy

OK..here's the output from that command.  As usual, verbose without being informative.  Now it's time to go and look to see if there are any new applications that I can run that I didn't have before.... I mean that is the idea of installing something...

don@B1501:~$ sudo aptitude install firebird2.0-server-common
[sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  firebird2.0-server-common 
The following packages will be REMOVED:
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
0 packages upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 511kB of archives. After unpacking 72.9MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe firebird2.0-server-common 2.0.4.13130-1.ds1-5ubuntu1 [511kB]
Fetched 511kB in 1s (257kB/s)                     
(Reading database ... 123192 files and directories currently installed.)
Removing linux-headers-2.6.28-11-generic ...
Removing linux-headers-2.6.28-11 ...
Selecting previously deselected package firebird2.0-server-common.
(Reading database ... 106891 files and directories currently installed.)
Unpacking firebird2.0-server-common (from .../firebird2.0-server-common_2.0.4.13130-1.ds1-5ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firebird2.0-server-common_2.0.4.13130-1.ds1-5ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/gdef.1.gz', which is also in package firebird2.1-server-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/firebird2.0-server-common_2.0.4.13130-1.ds1-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

---

### Post by Don Bowen on 2009-09-30
> **Temposs said:**
> Don,
   You are probably wanting a GUI tool for Firebird SQL, but what you've installed so far only has command line utilities. If you want a GUI tool, the help site [https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1) recommends a program called FlameRobin.

To install FlameRobin, go to Applications->Add/Remove. Search for flamerobin. Check it and click Apply a couple times. Then it should get installed and appear in your Applications menu Applications->Programming->FlameRobin.

Actually, no, I much prefer to work with the command line interface for Firebird.  In windows the utility is called ISQL.exe.  There are also other ClI utilities that allow creating users and granting rights to different parts of the database.  They may well be on here, but I can tell this thread has gone on too long...

I'm beginning to realize that there is no generic way to install something on Linux.  Each program seems to have elaborate scripts ... "a great sound and fury..."

---

### Post by Don Bowen on 2009-09-30
don@B1501:~$ sudo apt-get install firebird2.1-super
[sudo] password for don: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
firebird2.1-super is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
don@B1501:~$ 

still no icons to click on or programs to run...How can anyone say Firebird is installed?

---

### Post by 3rdalbum on 2009-09-30
> **Don Bowen said:**
> 

still no icons to click on or programs to run...How can anyone say Firebird is installed?

If it's a command-line program, then there will not be any icons in your Applications menu.

Right now you have probably 1,000 command-line apps installed on your system, so they're purposely not in your Applications menu :-)

The earlier package you installed has programs, from the listing you gave us:

/usr/bin/gbak
/usr/bin/gdef
/usr/bin/gfix
/usr/bin/gpre
/usr/bin/qli
/usr/bin/gsec
/usr/bin/fbstat
/usr/bin/isql-fb
/usr/bin/nbackup

When you run them in the terminal, you don't have to give the /usr/bin/ part.

The screencast "Where did my installed program go?" in my signature shows you how to locate programs associated with a particular package in Synaptic.

---

### Post by Don Bowen on 2009-09-30
yes, that command was actually useful because it appears to list all the folders that Firebird went to during it's install (if it's actually installed).  So far, this list of directories is all the evidence I have that something is installed.  
This is disturbing because the only way I know to get rid of all the files it put in those places your command lists is to.... re-install Ubuntu.  Add/Remove programs gives me no options to remove software like this.

---

### Post by Don Bowen on 2009-09-30
Except Firebird, since Firebird doesn't show up in the list of available applications.  Of course it's easy to install programs on the "list".

---

### Post by Temposs on 2009-09-30
> **Don Bowen said:**
> Actually, no, I much prefer to work with the command line interface for Firebird.  In windows the utility is called ISQL.exe.  There are also other ClI utilities that allow creating users and granting rights to different parts of the database.  They may well be on here, but I can tell this thread has gone on too long...

I'm beginning to realize that there is no generic way to install something on Linux.  Each program seems to have elaborate scripts ... "a great sound and fury..."

If you want to run the equivalent of ISQL.exe in the Linux version, it appears to be called:

```
isql-fb
```

Try typing that into the command line. It should work.

There are indeed standard ways to install things on Linux/Ubuntu. You're just not used to it yet. Linux is not Windows. The standard way to install something from the command line is with apt-get. The standard way with a GUI is with Synaptic Package Manager or the Add/Remove program, both of which underlyingly use apt-get anyway.

You can tell which programs you have installed very easily. Simply open System->Administration->Synaptic Package Manager, search for the package you want to know is installed, and if it's checked(or has a filled in green box), then it's installed. Otherwise, it's not installed. If you want to see where the installed files are, right-click on the package, choose Properties, click the Installed Files tab, and look at where the files are located.

These are all very well-principled and standard procedures on Linux/Ubuntu. It just takes some getting used to, and you shouldn't keep trying to fit it into the Windows box, if you want to be successful in Linux.

---

### Post by Temposs on 2009-09-30
> **Don Bowen said:**
> yes, that command was actually useful because it appears to list all the folders that Firebird went to during it's install (if it's actually installed).  So far, this list of directories is all the evidence I have that something is installed.  
This is disturbing because the only way I know to get rid of all the files it put in those places your command lists is to.... re-install Ubuntu.  Add/Remove programs gives me no options to remove software like this.

If you want to uninstall Firebird once you've installed it, it is very easy. You just open System->Administration->Synaptic Package Manager and search for the package you want to remove. Click the green box to uncheck the program. Click Apply a couple times and it's completely removed. Very easy and well-principled.

The equivalent from the command line is:

```
sudo apt-get remove firebird-super2.1
```

Synaptic basically runs that command when you use the GUI. It's all very standardized. As long as you install things with apt-get or Synaptic Package Manager or Add/Remove, you can also easily remove those programs via the same mechanism.

---

### Post by Don Bowen on 2009-09-30
Frustration level too high again... time to re-install Ubuntu.
  
Somewhere, some has installed Ubuntu and Fiebird... (of course, that presumption may be incorrect in itself!) 
Where is the ISQL.EXE program?  When I can run that and work with databases, then I'll know Firebird is installed.  Until then, it's just wasting space on the HD.

I'll be back later with a fresh install.  I'm hoping to imae the two Ubuntu partitions with Norton Ghost so that they can be restored to working order more easily.

---

### Post by Temposs on 2009-09-30
> **Don Bowen said:**
> Except Firebird, since Firebird doesn't show up in the list of available applications.  Of course it's easy to install programs on the "list".

Firebird doesn't show up on Add/Remove because Add/Remove mostly only shows applications that have a GUI(though there are some exceptions to that, like media codecs). Add/Remove is meant to be the most user-friendly application for computer novices. 

For the full list of applications you need to open System->Administration->Synaptic Package Manager. As I've described above, you can do all of your application installation and removal with this as well. Synaptic Package Manager is meant to be the GUI application installer for more computer savvy people and developers and such.

---

### Post by oldos2er on 2009-09-30
> **Don Bowen said:**
>  Where is the ISQL.EXE program?


 [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by scrooge_74 on 2009-10-01
> **oldos2er said:**
> [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

+1 on that link, very helpfull

---

### Post by Don Bowen on 2009-10-01
edit: this text was a reply to another post.  It showed up in the wrong place.  Not sure why.

This is that strange instruction that asks us to put something in front of line 3 when there is no identifiable line 3 to put anything in front of.  Following these puts me into some kind of editor on a blank page.  
I didn't understand the original instructions, and I don't understand your reply.
"no, no, follow these instructions"  what instructions are you referring to?

---

### Post by Don Bowen on 2009-10-01
> **Temposs said:**
> If you want to run the equivalent of ISQL.exe in the Linux version, it appears to be called:

```
isql-fb
```Try typing that into the command line. It should work.

There are indeed standard ways to install things on Linux/Ubuntu. You're just not used to it yet. Linux is not Windows. The standard way to install something from the command line is with apt-get. The standard way with a GUI is with Synaptic Package Manager or the Add/Remove program, both of which underlyingly use apt-get anyway.

You can tell which programs you have installed very easily. Simply open System->Administration->Synaptic Package Manager, search for the package you want to know is installed, and if it's checked(or has a filled in green box), then it's installed. Otherwise, it's not installed. If you want to see where the installed files are, right-click on the package, choose Properties, click the Installed Files tab, and look at where the files are located.

These are all very well-principled and standard procedures on Linux/Ubuntu. It just takes some getting used to, and you shouldn't keep trying to fit it into the Windows box, if you want to be successful in Linux.

I can only relate Ubuntu to what I know.  I don't really want it to fit into the Windows box, as I'm trying to get away from windows.

Yours is a very informative post.  Thank you.  I'll use Synaptic Package Mgr. to tell what programs are installed.  I'm surprised that Firebird left no visible way to run the software so much so that you would have to use Synaptic to tell that it was installed at all!  How useful is that?

I've re-installed Ubuntu now and imaged the installation, so re-imaging the HD now takes a minimal amount of time and puts Ubuntu back in a clean/stable state.  That will make learning this easier.  

Now, it's time to install Firebird again.... if I can locate how that was done.  Then I'll go and try to run the ISQL program with "ISQL-fb" at the terminal prompt.  What does fb stand for?

---

### Post by Don Bowen on 2009-10-01
edit: how come these replies I make don't show up next to the posts they're meant for?

book marked that page!  Seems like a good one!  Now I have to remember to save the book marks from Ubuntu so that when I re-image to fix some change I've made I don't lose them.

---

### Post by Don Bowen on 2009-10-01
> **oldos2er said:**
> [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

 				 				**Re: How do you install a program in Ubuntu?** 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **Don Bowen** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8033584#post8033584") 				
 				* Where is the ISQL.EXE program?*
 			 		 	 	 
 [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
 		                   		  		  		 		 			 				__________________
				-- 
 Ann
  Jaunty Jackalope (from the Jackalope's home, Wyoming)

OK.. I get the point.  Linux is not windows, and thank goodness it's not!
Still, I was hoping that an abstract thought might come from a direct question.
Installing software on a computer (any computer, any OS) is the act of putting someone else's program on your machine that wasn't there  before.  Now that it's there, there has to be some way to get the computer's CPU to execute the instructions in that file whether the code is machine language or some interpreted P-code.  

I know that there isn't a file called "ISQL.EXE" for me to run, but there is some file that is its equivalent and can be "run" on an Ubuntu installation.
I was hoping someone would say "well, Don, there really aren't executables in Linux, there are ?????? files.  To run these files you ????????  (click on an icon, run a command at a CLI interface)... "  

When a programmer sits and codes a program, there is usually a compiler that compiles that text into machine usable instructions aimed at a specific CPU and OS.  
What are those filese called in Linux?  Does Linux allow programs to execute through the CPU directly or does Linux act as an interpreter?  If I sit and write a "hello world" prgram, compile it, and save it..... how do I know where to find it and identify it as the result of the compilation and not the source code I wrote?
I suppose I need to form the questions in some other way.  My apologies for being obtuse.

---

### Post by Temposs on 2009-10-01
> **Don Bowen said:**
> I can only relate Ubuntu to what I know.  I don't really want it to fit into the Windows box, as I'm trying to get away from windows.

I'm just trying to encourage you to be conscious that you are trying to fit things into the Windows box still. You'll get there :-)

> **Don Bowen said:**
> Yours is a very informative post.  Thank you.  I'll use Synaptic Package Mgr. to tell what programs are installed.  I'm surprised that Firebird left no visible way to run the software so much so that you would have to use Synaptic to tell that it was installed at all!  How useful is that?

For programs that run only from the command line in Ubuntu, there are almost never any GUI links to those programs. This is a difference between Windows and Linux. Linux is command line oriented at heart, and Windows is GUI oriented at heart. So, if you install a command line program in Linux, why would you clutter your applications menus with links to command line programs? Rather, if you're using a command line application, then you should use the command line to run that application.

However, there is a way to manually add a shortcut to a command line application in the Ubuntu menu or panels, if you really really want that. If you wanted to add a shortcut in the panel, right-click an empty part of the panel(the bars at the top or bottom). Choose "Add to Panel". Double click "Custom Application Launcher". Choose "Application in Terminal" from the drop-down menu. Type the command you want the short cut for. You can enter in the other information too if you want, and choose a different icon. When you click OK, the shortcut will appear.

> **Don Bowen said:**
> I've re-installed Ubuntu now and imaged the installation, so re-imaging the HD now takes a minimal amount of time and puts Ubuntu back in a clean/stable state.  That will make learning this easier.

> **Don Bowen said:**
> Now, it's time to install Firebird again.... if I can locate how that was done.  Then I'll go and try to run the ISQL program with "ISQL-fb" at the terminal prompt.  What does fb stand for?

This is how to install the Firebird package you wanted from Synaptic Package Manager. Go to System->Administration->Synaptic Package Manager. Search for firebird. Scroll down until you see firebird2.1-super. Click the box next to it. Click apply a couple times and it will install.

---

### Post by Don Bowen on 2009-10-01
**Re: How do you install a program in Ubuntu?** 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **oldos2er** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8026088#post8026088") 				
 				[I]Yes. Enter this command into a terminal:
 	Code:
 	gksu gedit /etc/apt/sources.list.d/firebird.list 
 In front of line 3, add a comment mark # so that it looks like "# sudo...." Save and exit the file, then run
 	Code:
 	sudo apt-get update 
You should now be able to install Firebird.

Edit: Your sources.list looks fine.

this post still escapes me... running the first line puts me in "gedit"  and editor for "g" presumably, but the edit page is blank, so the subsequent instruction of "in front of line 3 ad a comment mark ...." makes no sense.  There is no line three.  
What was this post meant to communicate?
[/I]

---

### Post by Temposs on 2009-10-01
Don, if you'd like, we can chat by IM. I think you would benefit from some real-time communication...

If you have an AOL IM account, my screen name is the same as my ubuntuforums user name.

Feel free any time.

---

### Post by Don Bowen on 2009-10-01
**Re: How do you install a program in Ubuntu?** 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **Don Bowen** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8035836#post8035836") 				
 				*I can only relate Ubuntu to what I know. I don't really want it to fit into the Windows box, as I'm trying to get away from windows.*
 			 		 	 	 
I'm just trying to encourage you to be conscious that you are trying to fit things into the Windows box still. You'll get there :smile:

 	Quote:
 	 	 		 			 				 					Originally Posted by **Don Bowen** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8035836#post8035836") 				
 				*Yours is a very informative post. Thank you. I'll use Synaptic Package Mgr. to tell what programs are installed. I'm surprised that Firebird left no visible way to run the software so much so that you would have to use Synaptic to tell that it was installed at all! How useful is that?*
 			 		 	 	 
For programs that run only from the command line in Ubuntu, there are almost never any GUI links to those programs. This is a difference between Windows and Linux. Linux is command line oriented at heart, and Windows is GUI oriented at heart. So, if you install a command line program in Linux, why would you clutter your applications menus with links to command line programs? Rather, if you're using a command line application, then you should use the command line to run that application.

However, there is a way to manually add a shortcut to a command line application in the Ubuntu menu or panels, if you really really want that. If you wanted to add a shortcut in the panel, right-click an empty part of the panel(the bars at the top or bottom). Choose "Add to Panel". Double click "Custom Application Launcher". Choose "Application in Terminal" from the drop-down menu. Type the command you want the short cut for. You can enter in the other information too if you want, and choose a different icon. When you click OK, the shortcut will appear.

 	Quote:
 	 	 		 			 				 					Originally Posted by **Don Bowen** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8035836#post8035836") 				
 				*I've re-installed Ubuntu now and imaged the installation, so re-imaging the HD now takes a minimal amount of time and puts Ubuntu back in a clean/stable state. That will make learning this easier.*
 			 		 	 	 
 	Quote:
 	 	 		 			 				 					Originally Posted by **Don Bowen** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8035836#post8035836") 				
 				*Now, it's time to install Firebird again.... if I can locate how that was done. Then I'll go and try to run the ISQL program with "ISQL-fb" at the terminal prompt. What does fb stand for?*
 			 		 	 	 
This is how to install the Firebird package you wanted from Synaptic Package Manager. Go to System->Administration->Synaptic Package Manager. Search for firebird. Scroll down until you see firebird2.1-super. Click the box next to it. Click apply a couple times and it will install.
 		                   		  		  		 		 			 				__________________
				System76 Darter Ultra
Intel Pentium Core 2 Duo, 2.53Ghz
2 GB DDR2 SDRAM
Intel X4500 Graphics Card


OK... !!! Success!!! After much exploration, I think I can answer the question: 

[B]Q: How do you install a program in Ubuntu?

A:  Use add/remove programs or Synaptic Package Manager.  Find the program you want on the list, check it, and then apply to let Synaptic install it.[/B]


Thank you all for suffering beginner posts to get there!
Now, I hope to explore a little further....

Lets use Firebird as an example since I can now install it correctly (I think).
If I go do the Firebird website and download its Ubuntu installation files to a known folder....  How do I install those?
The larger question here is "How do you install programs that aren't on the Synaptic guest list?"

---

### Post by Don Bowen on 2009-10-01
> **Temposs said:**
> Don, if you'd like, we can chat by IM. I think you would benefit from some real-time communication...

If you have an AOL IM account, my screen name is the same as my ubuntuforums user name.

Feel free any time.
Thank you.  You're gracious.  Those of us who work as technicians in the ed biz are behind firewalls that don't allow instant messaging.
I was able to install the "ISQL" program on the application menu, and it actually works!
you once asked why anyone would want an icon for a command line program, and for me, the answer is to remind me that it exists and maybe even what it does.    If I can't see them now and then, I'll forget that they exist.

---

### Post by scrooge_74 on 2009-10-01
Install tor ;) and go around your firewall :p

---

### Post by Don Bowen on 2009-10-01
> **scrooge_74 said:**
> Install tor ;) and go around your firewall :p
Your suggestion speaks to the core of this thread.
Sure just go and install something.... 
well,  lets review what I've learned so far:
Programs are installed from the "Add/Remove" programs app or from the Synaptic.
If they are not on either list, they can't be installed (I know that's incorrect, but that's functionally true for my current understanding).
Since TOR doesn't appear on either list, it is impossible to install.
Until I learn how to install things without Synaptic or Add/remove, TOR and other programs not on the guest list are simply out of reach.

---

### Post by scrooge_74 on 2009-10-01
Well tor is in the repositories the package is called tor, if you cant find it the only reason would be that the repository where it is has not been enable by you.

If you want to learn how to install things first off all forget about the Add/remove, I never liked and in the past it did not worked well. Install things from synaptics until you get the hang of command line apt-get or aptitude (<--is similar to synaptics but ugly graphics and from command line).

90% of what you need to install is in synaptic in the standard repositories.
another 9% is in third party repositories that you can add to synaptic list of repositories which then becomes 99% of apps, what is left out are programs not that common or too new, those you get the added fun of having to download a tar ball and then compile them, since you are new at linux dont get into compiling stuff till you are more confy with the system, and then is likely you will seldom need to do compiling

---

### Post by Don Bowen on 2009-10-02
> **scrooge_74 said:**
> Well tor is in the repositories the package is called tor, if you cant find it the only reason would be that the repository where it is has not been enable by you.

If you want to learn how to install things first off all forget about the Add/remove, I never liked and in the past it did not worked well. Install things from synaptics until you get the hang of command line apt-get or aptitude (<--is similar to synaptics but ugly graphics and from command line).

90% of what you need to install is in synaptic in the standard repositories.
another 9% is in third party repositories that you can add to synaptic list of repositories which then becomes 99% of apps, what is left out are programs not that common or too new, those you get the added fun of having to download a tar ball and then compile them, since you are new at linux dont get into compiling stuff till you are more confy with the system, and then is likely you will seldom need to do compiling
I'll look through Synaptic again for TOR.  I begin to understand that there are things called "repositories" or safe places where software is setup so that it may be easily installed.
Adding repositories to the list of trusted places in Synaptic seems to be how things are installed.
Learning continues...
If TOR isn't in My Synaptic list (and if I've disabled it, then I surely didn't do it on purpose), then how do I get TOR to show up on this list?

I downloaded Nero for Ubuntu, and it unpacked as a .DEB file.  I'm guessing that's short for Debian which is one flavor of Linux installation.  It installed with a simple double click, no synaptic, no add/remove.... that means that it is possible to install things directly though I recognize it's progably safer/easier to use repositories.

I'll go look for TOR again on the Synaptic list.

---

### Post by Don Bowen on 2009-10-02
more installing stuff...

I was looking to download VLC for Ubuntu.  It's my fav media player, and sure enough, they have a version 1.0 for it.... but... it gives the following instruction...

**Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "multiverse"  repository activated.**

well I went to that menu in Synaptic, and I can guess that they want me to add some repository to a list somewhere. 
What's interesting to me is that they don't name the URL for multiverse specifically
Nor do they tell me where the reference to Multiverse goes.... 
What does it mean to have "multiverse repository activated"?
What steps do you take to accomplish that?

---

### Post by Don Bowen on 2009-10-02
> **Don Bowen said:**
> I'll look through Synaptic again for TOR.  I begin to understand that there are things called "repositories" or safe places where software is setup so that it may be easily installed.
Adding repositories to the list of trusted places in Synaptic seems to be how things are installed.
Learning continues...
If TOR isn't in My Synaptic list (and if I've disabled it, then I surely didn't do it on purpose), then how do I get TOR to show up on this list?

I downloaded Nero for Ubuntu, and it unpacked as a .DEB file.  I'm guessing that's short for Debian which is one flavor of Linux installation.  It installed with a simple double click, no synaptic, no add/remove.... that means that it is possible to install things directly though I recognize it's progably safer/easier to use repositories.

I'll go look for TOR again on the Synaptic list.
TOR comes in when you want to download some other software that is probably a front end for TOR.
It's called VISI something I think.
It's never listed as TOR all by itself...
Is that what you meant to install?

---

### Post by Don Bowen on 2009-10-02
> **oldos2er said:**
> Yes. Enter this command into a terminal:
```
gksu gedit /etc/apt/sources.list.d/firebird.list
``` In front of line 3, add a comment mark # so that it looks like "# sudo...." Save and exit the file, then run
```
sudo apt-get update
```You should now be able to install Firebird.

Edit: Your sources.list looks fine.
what did you mean by "in front of line 3?"

---

### Post by scrooge_74 on 2009-10-03
Good to see you are learning

A bit of an explanation here will help you out.

Repositories are server which have all the packages you need for installing stuff (dependencies, libraries, etc ,etc not just the program you want)

Synaptic has to go look at a file in /etc/apt/ called sources.list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free


Any line that has a # in front, is what is called commented out, apt or synaptic wont use it since the system takes the # symbol as a comment, you could write stuff in there if you want to remember something which wont make any sense to the system but since it has the # symbol it wont get read or interpreted by it.


So when it told you that some repositories in ubuntu are not enable is that they have the # symbol in front you could do it manually in that file, but go into synaptic>configuration>repositories, you can enable them there, then you do a package reload, and all the other packages in that repositories will show up

Tor is a proxy system to let you bypass blocks on the system, for more info:

htt://www.torproject.org/

---

### Post by Don Bowen on 2009-10-03
> **scrooge_74 said:**
> Good to see you are learning

A bit of an explanation here will help you out.

Repositories are server which have all the packages you need for installing stuff (dependencies, libraries, etc ,etc not just the program you want)

Synaptic has to go look at a file in /etc/apt/ called sources.list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free


Any line that has a # in front, is what is called commented out, apt or synaptic wont use it since the system takes the # symbol as a comment, you could write stuff in there if you want to remember something which wont make any sense to the system but since it has the # symbol it wont get read or interpreted by it.


So when it told you that some repositories in ubuntu are not enable is that they have the # symbol in front you could do it manually in that file, but go into synaptic>configuration>repositories, you can enable them there, then you do a package reload, and all the other packages in that repositories will show up

Tor is a proxy system to let you bypass blocks on the system, for more info:

htt://www.torproject.org/
well there is no "configuration" menu visible in synaptic.
The Menu bar reads:
file, edit, packages, settings, help.  
I don't see it under settings, so I have to ask...
what do you mean?

---

