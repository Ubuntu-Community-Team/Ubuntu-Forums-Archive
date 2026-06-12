---
title: "Mozilla install path?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by HugoB on 2009-06-05
A very basic question, but where can I find the install path of Mozilla within Ubuntu? (I'm using Ubuntu 9.4)

I would like to try and copy files from the installed directory.

Thank you in advance

---

### Post by markharding557 on 2009-06-05
/home/user-name/.mozilla
this contains all settings,cache and add ons etc

---

### Post by HugoB on 2009-06-05
My apologies. I was looking for Firefox's install directory that comes with Ubuntu when it is installed.

The install directory was found (on my machine) at:
/etc/firefox-3.0/

Thanks for the reply :)

---

### Post by HugoB on 2009-06-05
My apologies. I was looking for Firefox's install directory that comes with Ubuntu when it is installed.

The install directory was found at:
/etc/firefox-3.0/

Another direcory:
/home/user-name/.mozilla

Also exists, but it was hidden on my machine.

Thanks for the reply :)

---

### Post by SunnyRabbiera on 2009-06-05
The application directory for mozilla firefox is in /usr/lib
But be warned you cannot edit anything in the folders here by default, it needs root permissions, to bypass you need sudo.
To get easy access I say install the gksu-nautilus package, it makes the use of a terminal less needed.

---

### Post by Rubicon_82 on 2009-06-05
Hi,

If you are new to Linux, you may be unaware of the following:

In Windows, *most* programs are self contained within one directory, usually 'C:\Program Files\<program name>'.  This is not the case in Linux, where programs installed from the package manager have the package files spread over several directories.  This is done for several reasons, such as avoiding duplication of shared libraries, or ensuring that all program binaries are can be found within the $PATH environment variable.

In Ubuntu, you can determine the location of files *installed* for a given package by running the command:
```

dpkg -L <package-name>
```
for example 'dpkg -L firefox-3.0'.

In addition to the files listed by the above command, the application may also create hidden user configuration files in your home directory.  To locate these, try the following:
```

find ~/ -iname <package-name>
```
for example 'find ~/ -iname firefox'.

There should also be GUI based methods for locating this information, have a search through your package manager or file browser's search function for more information.

---

### Post by valex on 2009-06-05
here is my outout. :(

> ```
bash: dpgk: command not found
```

---

### Post by Rubicon_82 on 2009-06-05
> **valex said:**
> here is my outout. :(

Sorry, I mistyped the command.  It should be:
```

dpkg -L firefox-3.0
```

---

### Post by SunnyRabbiera on 2009-06-05
> **valex said:**
> here is my outout. :(

Its a typo, the command is actually dpkg -l

> **Rubicon_82 said:**
> Sorry, I mistyped the command.  It should be:
```

dpkg -L firefox
```
what he said :D

---

### Post by lovinglinux on 2009-06-05
What are you trying to achieve? Why do you need to copy Firefox installation files?

---

### Post by HugoB on 2009-06-17
Hi everyone

Maybe the title of the forum was a bit misleading. I was only exploring the filesystem of Ubuntu Linux a little bit.

Knowing where Mozilla (or other applications) is installed on a machine can be useful for many reasons (but not all reasons).

_Backing up:_
Some files in Mozilla's installed directory could be manually backed up, if there is no tool within the browser that can perform this function for you.

There could be other reasons, but I might not be aware of it.

---

### Post by Bölvaður on 2009-06-17
uh... that might not be the best way to back up your stuff.

you dont need to backup programs really, just take down the name of the packages, there is a command that was piped into a text document which made that list for you... I think it was with apt-get or... you'll find it on the forum.

Secondly, all your config files are kept in hidden folders in your home directory.
So just look for directories beginning with . (a dot) in your home directory.
The reason why the config files are kept there is because the programs are not allowed to access other places (not even their own files) outside of /tmp and /home.

---

### Post by lovinglinux on 2009-06-17
> **HugoB said:**
> _Backing up:_
Some files in Mozilla's installed directory could be manually backed up, if there is no tool within the browser that can perform this function for you.

You don't need to backup any program installation files or folders. They can be re-installed any time with a simple command or through the installation managers.

What you really need to backup is the configuration files, which are located (most of the time), in your home directory. Firefox for example stores configurations in profiles, allowing several users to use Firefox independently with the same user account or allowing the same user to have different configurations for different situations. Firefox profiles are stored in the folder /home/*username*/.mozilla/firefox. You can backup everything inside that folder or use a Firefox extension like [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109).

> **Bölvaður said:**
> you dont need to backup programs really, just take down the name of the packages, there is a command that was piped into a text document which made that list for you... I think it was with apt-get or... you'll find it on the forum.

If you need to create a list of installed programs for re-installation after a clean install or to replicate the same programs on another machine follow this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

---

