---
title: "problems resolving a broken package removal"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Huntz23 on 2009-02-19
I was cleaning out some clutter and I have a package hanging up the works.  In terminal I get this

[PHP]Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  ttf-opensymbol
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 84078 files and directories currently installed.)
Removing ttf-opensymbol ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning
dpkg: error processing ttf-opensymbol (--remove):
 subprocess post-removal script returned error exit status 4
Errors were encountered while processing:
 ttf-opensymbol
E: Sub-process /usr/bin/dpkg returned an error code (1)
Some errors occurred while unpacking. I'm going to configure the
packages that were installed. This may result in duplicate errors
or errors caused by missing dependencies. This is OK, only the errors
above this message are important. Please fix them and run [I]nstall again
Press enter to continue.


installation script returned error exit status 100.
Press <enter> to continue.                       [/PHP]

any ideas?

---

### Post by ellgor on 2009-02-20
Hi,

Try this:

sudo apt-get -f install

after this has completed, then start removing things (going by the error message only half of an app was installed, this should fully install it).

Regards, Ellgor.

---

### Post by Huntz23 on 2009-02-21
Thanks for the reply Ellgor.

apt-get -f install gives me this message:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-opensymbol
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ttf-opensymbol
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 84078 files and directories currently installed.)
Removing ttf-opensymbol ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning
dpkg: error processing ttf-opensymbol (--remove):
 subprocess post-removal script returned error exit status 4
Errors were encountered while processing:
 ttf-opensymbol
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

still no go.

and rummaging I have come  across 'dpkg --configure -a' and that comes back with this:
```
Setting up ttf-opensymbol (2.0.4-0ubuntu7) ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 ttf-opensymbol

```

it doesn't fly either

Just for my own curiousityI did 'cd' into them directories and they do exist.

just plain old stumped still.

---

### Post by Huntz23 on 2009-02-22
OK I figured it out, I was reading my post and noticed fontconfig seemed to be the failure.
I tried to to fix it and and nothing worked.
So I uninstalled to and it pulled the string and took kubuntu-core with it.
But with a fresh install of kubuntu-core. everything sorted it self out.

So call me lucky that it worked or lucky that I stubled on it but I call it solved so far.

---

