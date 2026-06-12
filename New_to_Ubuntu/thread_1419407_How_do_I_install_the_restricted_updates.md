---
title: "How do I install the restricted updates?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by gshockxc on 2010-03-01
I've been installing my updates using the terminal screen with the following commands...

```

$ sudo aptitude update

```

And 

```

$ sudo aptitude safe-upgrade

```

Should I be doing something different?  I don't even know why the restricted updates are restricted.  I've been having problems with Kopete - keeps crashing, and there's a Kopete update, but I can't get to it.  Also, I think there are some updates to KDE 4.4, and that keeps crashing, so I probably want those too.  

Any help would be appreciated.

Thanks, 

-gshockxc

---

### Post by Jared Norris on 2010-03-01
I'm not sure what you mean by "restricted updates" but I think you are referring to the restricted-extras packages?

If that is the case have a look at [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") 

It has a lot more information and details but the basics of it is to install the package you need to:

```
$ sudo apt-get install kubuntu-restricted-extras

```

The only other thing I can think of is if you are referring to installing updates from the Proposed Updates repository which is essentially just the testing area for packages planned to be released to the normal repositories. As long as there are no problems with these they will be released to the normal repositories after testing. I would only use this as a last resort if it is your main computer as it is possible these packages will have errors with them, hence them being in the testing phase.

---

### Post by pappy50+ on 2010-03-01
complements of Marco Braida - found from Launchpad

Please first enable the  multiverse repository:
 Open System &#8594; Administration &#8594; Software sources &#8594; [ Tab Ubuntu software ]
enable "Software restrictecd by copyright or legal issue ( multiverse )"
Close and confirm the repository reload.
 Open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type:
(if the system ask you a password give your user password, you will not see nothing when you type it, then press enter)
 sudo dpkg --configure -a
 then to update and upgrade and also check pending or missing packages, still using terminal type:
 sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
 sudo apt-get install  ubuntu-restricted-extras
 Hope this helps

---

