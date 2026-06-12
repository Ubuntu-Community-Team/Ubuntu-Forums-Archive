---
title: "Can't install anything"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Kungal on 2010-09-07
Hi all,

I have just installed Ubuntu and I am having a problem where I can't install any new programs at all.  THis is probably a simple problem but one which I have no idea about fixing since I am completely new to linux.

I would like to install Synergy (a mouse and keyboard sharing program) so I go the the software manager (which is a brilliant idea by the way), locate it and click install.  Then I get the error "the package system is broken".  Then I try running the suggested code in the terminal and get

```
  @ubuntu:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```Exactly the same thing happens for every program I try to install

Pleas help me

---

### Post by muteXe on 2010-09-07
Stick a "sudo" on the front of your command.

edit: more -> you cant install stuff if you're a normal user, hence the need for "sudo":
```

sudo apt-get install blah blah blah

```

it'll ask you for your password, then it should it be fine.

---

### Post by ibuclaw on 2010-09-07
```
sudo apt-get install -f
```

Remember to use 'sudo' when you need to perform administration tasks. :)

---

### Post by Paddy Landau on 2010-09-07
You may find the GUI easier to use than the command line.

[LIST]
[*]From your menu, go to Ubuntu Software Centre.
[*]In the search box at the top right, type *synergy*.
[*]You'll see two entries. Press Install on the first one ("synergy") and, if you want, Install on the second one ("QuickSynergy"). Fill in your password when prompted.
[/LIST]

---

### Post by Kungal on 2010-09-07
Ok thanks for telling me that sudo is for administrator type tasks,  However, the there seems to be some sort of error with the system

```

sam@ubuntu:~$ sudo apt-get install -f
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  synergy
The following NEW packages will be installed:
  synergy
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/626kB of archives.
After this operation, 1,511kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 122934 files and directories currently installed.)
Unpacking synergy (from .../synergy_1.3.1-6ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/synergy_1.3.1-6ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/synergyc', which is also in package synergy-plus 0:1.3.4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/synergy_1.3.1-6ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
sam@ubuntu:~$ 

```Paddy Landau:
I noted in the post that I am trying command line because the software manager didn't work

---

### Post by Paddy Landau on 2010-09-07
> **Kungal said:**
> Paddy Landau:
I noted in the post that I am trying command line because the software manager didn't work
:oops: Sorry!

It looks as though you already have a package called Synergy+ installed. Synergy and Synergy+ have merged.

I would suggest that you uninstall Synergy+ (try System > Administration > Synaptic Package Manager if Ubuntu Software Centre doesn't work).

Then try again to install.

---

### Post by Kungal on 2010-09-07
Great,  I successfully uninstalled synergy plus and then installed synergy and it appead to work without any errors.

What's more, I can now install any piece of software in the software manager (at least any that I have tried).
Thanks for you help so far, but I have one more question.

How do I run programs once they're installed?  I have installed 7-zip and Synergy but I can't work out how to actually start these programs so that I can use them.

---

### Post by Paddy Landau on 2010-09-07
> **Kungal said:**
> How do I run programs once they're installed?
7-zip is a command-line program, not GUI. It's also available from Nautilus; if you right-click a file, group of files or folder and select Compress, you get the choice of using 7z.

I don't know about synergy, because I've never used it. Isn't it command-line? Did you try QuickSynergy for the configuration?

---

### Post by gauravj on 2010-09-07
7-zip will be integrated with file roller. In synaptic for
installed packages, right click and select properties. you will 
get a tab for installed files. look for executable files and run 
them from terminal.
Search for .desktop files. You will find them in /usr/share/app-install/desktop or in /usr/share/applications.
Open one of them and you can see the command for launching the application.
EXEC entry.

---

### Post by Kungal on 2010-09-07
I see, I assumed that 7-zip would work the same on ubuntu as it does on windows. 

Thanks for all your help

---

### Post by Paddy Landau on 2010-09-07
> **Kungal said:**
> I assumed that 7-zip would work the same on ubuntu as it does on windows.
I've never used it on Windows. In Ubuntu, it's easy just to use Nautilus. There are others, such as bzip, gzip and zip (used with tar if you are grouping files in the same archive).

Actually, I thought that 7-zip was installed by default, because I get 7z on Nautilus and I've never installed manually (I've never used 7-zip).

If your question is answered, please mark the thread as Solved.

---

