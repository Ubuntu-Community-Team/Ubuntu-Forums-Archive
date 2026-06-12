---
title: "Repairing VLC Player's installation"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by dniezby on 2009-02-17
Anyone know how I can repair VLC player's installation?

Everytime it tries to open, it says that it cannot find a skin. Then I navigate to the default skin.vlt and it closes the viewer.

Thinking it's all fixed, I try to open the viewer again and it gives me the error again.

I already tried to uninstall it and reinstall it.

I'm sure that you Ubuntu Masters will have a Terminal command that can reinstall it cleanly for me.

Please help...

---

### Post by whoop on 2009-02-17
Did you remove it in Synaptic? Did you select "mark for complete removal"?

---

### Post by Titan8990 on 2009-02-17
It is hard for applications to uninstall addons that you have made yourself. If there was a command that could do it, it would be this one:


sudo apt-get remove --purge vlc && sudo apt-get install vlc

---

### Post by dannyboy79 on 2009-02-17
I always use aptitude versus apt-get because when you use apt-get, it will install the package and all the dependencies but come to time to uninstall it, it won't uninstall the unneeded dependencies so before you know it your machine has all these programs on it that aren't needed. Where as aptitude will remove the unneeded dependences along with the main app you're trying to remove. same thing from the command line just use aptitude not apt-get. so it would be this
```
sudo aptitude --purge vlc && sudo aptitude install vlc
```

---

### Post by Titan8990 on 2009-02-17
> **dannyboy79 said:**
> I always use aptitude versus apt-get because when you use apt-get, it will install the package and all the dependencies but come to time to uninstall it, it won't uninstall the unneeded dependencies so before you know it your machine has all these programs on it that aren't needed. Where as aptitude will remove the unneeded dependences along with the main app you're trying to remove. same thing from the command line just use aptitude not apt-get. so it would be this
```
sudo aptitude --purge vlc && sudo aptitude install vlc
```


Thanks for the info, I was unaware of the difference.


I personally just use this, however:  sudo apt-get autoremove

---

### Post by dniezby on 2009-02-17
> **dannyboy79 said:**
> I always use aptitude versus apt-get because when you use apt-get, it will install the package and all the dependencies but come to time to uninstall it, it won't uninstall the unneeded dependencies so before you know it your machine has all these programs on it that aren't needed. Where as aptitude will remove the unneeded dependences along with the main app you're trying to remove. same thing from the command line just use aptitude not apt-get. so it would be this
```
sudo aptitude --purge vlc && sudo aptitude install vlc
```
I just tried sudo apt-get autoremove and it seemed to work but when I reinstalled it, it still popped up with that error.

I'm going to try the aptitude method now.

---

### Post by dniezby on 2009-02-17
> **Titan8990 said:**
> Thanks for the info, I was unaware of the difference.


I personally just use this, however:  sudo apt-get autoremove
I enter the aptitude command and this is what came up:
```
Unknown command "vlc"
aptitude 0.4.11.3
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 safe-upgrade - Perform a safe upgrade
 full-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package
 why          - Show the manually installed packages that require a package, or
                why one or more packages would require the given package
 why-not      - Show the manually installed packages that lead to a conflict
                with the given package, or why one or more packages would
                lead to a conflict with the given package if installed

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress
                indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends	Specify whether or not to treat recommends as
                strong dependencies
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
 -i             Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

```

---

### Post by Titan8990 on 2009-02-17
You didn't type the command right. Here is says: Unknown command "vlc"

This means that you typed vlc somewhere in the command when it is simply:


sudo apt-get autoremove

---

### Post by mc4man on 2009-02-17
Very simple fix, in a terminal
```
vlc --reset-config
```

---

### Post by dniezby on 2009-02-17
> **mc4man said:**
> Very simple fix, in a terminal
```
vlc --reset-config
```
That worked. 

The reset config fixed everything.

Thank you.

---

### Post by dannyboy79 on 2009-02-18
> **dniezby said:**
> I enter the aptitude command and this is what came up:
```
Unknown command "vlc"
aptitude 0.4.11.3
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 safe-upgrade - Perform a safe upgrade
 full-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package
 why          - Show the manually installed packages that require a package, or
                why one or more packages would require the given package
 why-not      - Show the manually installed packages that lead to a conflict
                with the given package, or why one or more packages would
                lead to a conflict with the given package if installed

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress
                indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends	Specify whether or not to treat recommends as
                strong dependencies
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
 -i             Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

```
I apologize, I gave you the wrong command. It would be
```
sudo aptitude remove vlc
```

---

