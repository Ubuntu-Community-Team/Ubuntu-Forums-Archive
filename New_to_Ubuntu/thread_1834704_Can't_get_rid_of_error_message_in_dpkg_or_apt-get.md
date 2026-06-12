---
title: "Can't get rid of error message in dpkg or apt-get"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by rtruswell on 2011-08-27
Hi,

I was trying to install a printer driver recently, and I failed.   Worse, the failure seems to have upset dpkg and apt-get, and now regular  package management tasks frequently aren't working.

Here are all the details I can remember:

The package which failed to install is dcp7065dnlpr, a Brother printer driver downloaded off their website.

The error message generated when I tried to install it with dpkg was (I think):

start: Unknown job: lpd

I tried dpkg -r, dpkg -P, and dpkg --remove-reinstreq (i.e. all the  options which seemed relevant on the dpkg man page), to remove the  broken package, but they all generated variants on the same theme:

dpkg: error processing dcp7065dnlpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 dcp7065dnlpr

But trying to reinstall it didn't get anywhere - same error messages as with the first attempt to install.  (I believe that the  first time I tried this, there were some different error messages, along  the lines of "start: Unknown job: lpd", and mentioning the prerm and  postrm scripts, but I can't generate those again).

If I try dpkg -l | grep dcp7065dnlpr, I get:

rHR dcp7065dnlpr                          2.1.0-1                                    Brother DCP-7065DN LPR driver

(or iHR, or PHR, on the first line, depending on whether I last used the -i/-r/-P option).

Similarly, if I try to do pretty much anything with apt-get, I now get  error messages based around this package.  e.g. apt-get install  alarm-clock generates:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package dcp7065dnlpr needs to be reinstalled, but I can't find an archive for it.

Presumably, this is because the package didn't come from a repository but was downloaded direct from the Brother website.  Again, the promising-sounding options from the apt-get man page (-f, -m,  --ignore-hold) don't help.

One last detail: there was a CUPS driver for the same printer installed  at the same time.  That one has been installed with no problems - just  mentioning it in case it's relevant:

ii  cupswrapperdcp7065dn                  2.0.4-2                                    Brother DCP7065DN CUPS wrapper driver

Of course, in the long run, I want to get this printer working (and I  might end up asking for help with that if I get stuck again, I'm afraid), but  in the short term, I'd just like to get this package cleaned up, and get  everything working smoothly again.  I get the feeling I'm missing  something very basic, but googling/reading man pages hasn't helped me.   If any of you can straighten me out, it'd be much appreciated.

---

### Post by wojox on 2011-08-27
Maybe this will help: [http://ubuntuforums.org/showthread.php?t=1833289](http://ubuntuforums.org/showthread.php?t=1833289)

---

### Post by iponeverything on 2011-08-28
create a fake lpd so that job will finishes then delete it.

to create it:
```
 sudo ln -s /bin/true /etc/init.d/lpd 
```

to delete it:

```
sudo rm /etc/init.d/lpd
```

---

### Post by rtruswell on 2011-08-28
iponeverything: worked beautifully, touch wood.  I'd never come across /bin/true before.  Thanks for the advice.

wojox: Thanks.  When I start fighting with the printer again, that may well be useful.

---

