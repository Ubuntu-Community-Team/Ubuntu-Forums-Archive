---
title: "I am completely lost"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by StephenG on 2009-12-16
I thought I had some of this figured out. Apparently not.  I've downloaded the latest driver from H-P, in order to get all the functions working on my PhotoSmart printer.  It shows on my desktop as "hplip-3.9.12.run" and is supposed to be an auto-install.  I downloaded it here since the Update Manager wasn't finding it and the one it does find is outdated enough to not make the printer fully functional.  I can not figure out the command(s) to get the file to actually install.  Anyone?

---

### Post by doas777 on 2009-12-16
open a terminal, and type

```
sudo <path to .run file>
```

or if you are already in the directory, just run
```
sudo ./hplip-3.9.12.run
```

---

### Post by StephenG on 2009-12-16
Thanks for such a prompt response.  And this is the result:

stephen@Stephen-laptop:~/Desktop$ sudo ./hplip-3.9.12.run
sudo: ./hplip-3.9.12.run: command not found
stephen@Stephen-laptop:~/Desktop$

---

### Post by wojox on 2009-12-16
Right-click the file and select Properties

Under the Permissions tab, make sure that Allow executing file as program is ticked and press Close

Double-click the .run file to open it. A dialog box should appear

Press Run in Terminal to run the installer

---

### Post by doas777 on 2009-12-16
are you sure the run file is on your desktop?

also if you have marked it as executable, and the line still does not work, try this:
```
sudo sh ./hplip-3.9.12.run
```

---

### Post by bodhi.zazen on 2009-12-16
hplip is in the repositories

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hplip&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hplip&searchon=name&subword=1&version=all&release=all)

Is there some reason you are manually installing it ?

---

### Post by LowSky on 2009-12-16
```
sudo apt-get install hplip
```

---

### Post by sandyd on 2009-12-16
> **bodhi.zazen said:**
> hplip is in the repositories

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hplip&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hplip&searchon=name&subword=1&version=all&release=all)

Is there some reason you are manually installing it ?
sometimes, the hplip in the repos has some kind of problem that causes it not to detect any printers at all, even after running the setup.
i think thats the problems the OP is having.

---

### Post by doas777 on 2009-12-16
the op mentioned that it did not provide a full feature set (not that that is an entirely reasonably expectation).

---

### Post by bodhi.zazen on 2009-12-16
Well, it the version in the repose does not work, and assuming you downloaded the file to your desktop :

```
cd ~/Desktop
chmod a+x hplip-3.9.12.run
sudo ./hplip-3.9.12.run
```

---

### Post by StephenG on 2009-12-16
The version in the repository is 3.9.8.  My printer is a PhotoSmart Premium and it really wants 3.9.12 to make the scan, fax, etc., from desktop available.  I could find no way to force the repository to locate 3.9.12, and am happy to try to do it that way of you can adivse a procedure for getting it located online.

Will manually installing it cause everything else to crash around me?

---

### Post by chillyomi on 2009-12-16
hmmm

---

### Post by 3rdalbum on 2009-12-16
> **StephenG said:**
> The version in the repository is 3.9.8.  My printer is a PhotoSmart Premium and it really wants 3.9.12 to make the scan, fax, etc., from desktop available.  I could find no way to force the repository to locate 3.9.12, and am happy to try to do it that way of you can adivse a procedure for getting it located online.

Will manually installing it cause everything else to crash around me?

There doesn't seem to be a PPA providing this version of the package. I personally think HP should provide an Ubuntu repository for it, don't you?

Installing hplip manually shouldn't cause any problems.

You first need to make this file executable (Linux security feature). Open a terminal (Applications > Accessories > Terminal) and type the following (but don't run it yet):

```
sudo chmod a+x
```

Press the space bar to insert a space after the x, and then drag the file into the terminal window. Bring the terminal back to the front and hit Enter to run this command.

Now you can run the program. It needs system-wide access, so we need to run it as root with 'sudo'. Type the word 'sudo', put a space after it, and then drag the file into the terminal as before and run it.

---

### Post by StephenG on 2009-12-16
Certainly I think HP should provide the depository for all their drivers.  Since I don't know what a PPA is, I guess I couldn't agree with you more -- or less -- on that question.

Thanks to all for the step-by-step assistance.

Stephen

---

### Post by 3rdalbum on 2009-12-16
> **StephenG said:**
> Certainly I think HP should provide the depository for all their drivers.  Since I don't know what a PPA is, I guess I couldn't agree with you more -- or less -- on that question.

Oh sorry... a PPA is a repository as well, but just a slightly different kind (administered by one person and hosted at launchpad.net).

---

### Post by StephenG on 2009-12-16
Ahhh.  Having resisted any Windows involvement until at least 1996 or 7, preferring DOS command line and simplicity, I thought the transition to linux would be easy.  It's not been.  I ffel very foolish asking questions that should be easy, but the commands are different enough from DOS to muck everything up.  Would that there was a manual (bible-sized) like my old DOS 6.2 -- about 3 or 400 pages thick with all the commands and their various switches, with examples, etc. .... That's my idea of OS heaven.

---

### Post by bodhi.zazen on 2009-12-16
> **StephenG said:**
> Ahhh.  Having resisted any Windows involvement until at least 1996 or 7, preferring DOS command line and simplicity, I thought the transition to linux would be easy.  It's not been.  I ffel very foolish asking questions that should be easy, but the commands are different enough from DOS to muck everything up.  Would that there was a manual (bible-sized) like my old DOS 6.2 -- about 3 or 400 pages thick with all the commands and their various switches, with examples, etc. .... That's my idea of OS heaven.

You might enjoy this link :

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by mubeenjukaku on 2009-12-17
HPLIP Automatic installer supports various Linux distributions. Please read the detailed instructions at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) on how to install HPLIP using automatic installer.

---

### Post by dFlyer on 2009-12-24
I install this last night, very easy. No need to change any thing from the download. Just open the command line (terminal) change to the directory the file was saved in and type:

sh hplip-3.9.12.run

Press enter and when asked (a) for auto configure and install. It will check your OS for which distro you have and ask for the root password. For ubuntu it is the sudo password which should be your own if your the administor. It will download the archives it needs to compile your program and then install it.

gary

---

### Post by Cake-diva1986 on 2010-01-14
when I type in the command sh hplip-3.9.12.run I get this

sh: Can't open hplip-3.9.12.run

so what should I do now ?

---

### Post by Cake-diva1986 on 2010-01-14
ok i got it going, but I cant scan. whats the sane file I need?

---

