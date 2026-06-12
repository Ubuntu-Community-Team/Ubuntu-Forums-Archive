---
title: "Apt Authentication issue"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by tuibird on 2010-03-24
My brother installed this for me just prior to xmas, but it seems to not be accepting updates.  here I will type the messages I'm getting.

**Information Available**                          **Apt Aauthentication Issue**
Problem during package list update.  The package list failed with an authentication failure.  This usually happens behind a network proxy server.  Please try to click on the  "run this action now" button to correct the problem or update the list manually by clicking update manager and clicking on "check".  I have done this and get this other message coming under

**Update Manager                         An Error Occurred**
W: an error occurred during  signature verification.  The repository is not updated and previous indes files will be used. GPGerror: Http//nz.archive.ubuntu.com karmic updates Release:  The following signatures were invalid BADSIG 40976EAF437DO5B5  Ubuntu Archive automatic signing key <ftp master @ubuntu.com>  .

  This error message goes on along similar vein, but I don't have it to copy and would take ages.  Anyway each time I try to update it time since last update gets longer, so currently my computer last accepted update 75 days ago.

Hoping someone can help and I may learn something, because it looks like  my brother  is sick of looking after me and my computer.

Many thanks

---

### Post by 2hot6ft2 on 2010-03-24
Open a terminal
Applications > Accessories > Terminal
and run
```
cat /etc/apt/sources.list
```
Highlight the results and right click copy, then right click paste it in the reply box.
Highlight it again and click on the # sign at the top of the reply box.

Also run this before closing the terminal since it will sometimes fix the errors.
```
sudo apt-get update
```
type in your password when prompted and hit Enter it wont be displayed.
You may just get the same errors you've been getting but it's worth a shot.
> **tuibird said:**
> Http//nz.archive.ubuntu.com
Wierd, aside from the fact the H at the beginning should be lower case that takes me to this wikipedia page.
[http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)

Ahah, changing the H to h and adding the : after http so it's [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) and it works. I missed that : being missing.

---

### Post by gmargo on 2010-03-25
There's a long thread on this in the bug reports: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234)  (There's a solution in post #50 but its overly complicated.  Post #65 is the method I would use, and is listed below.)

The probable cause is an out-of-date package list file.  Easiest solution is to re-download all the package list files.  If that by itself does not work, then change the archive mirror.

Before re-download all the list files, you can either clean out /var/lib/apt/lists or save the old one like this:
```

cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```

---

### Post by sturg_nz on 2010-07-30
I sorted this same problem out by following this post [http://http://drew.thewithers.org/2009/12/how-to-fix-ubuntu-gpg-error-badsig.html]("http://http://drew.thewithers.org/2009/12/how-to-fix-ubuntu-gpg-error-badsig.html"). Worked a treat

---

