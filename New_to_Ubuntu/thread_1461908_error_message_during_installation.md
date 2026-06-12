---
title: "error message during installation"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by thatstheguy on 2010-04-24
Hey everybody,

I'm unable to play videos and music on the internet.  Attempting to remedy the problem, I visited Ubuntu's Official Documentation page on the support site and tried to download the "ubuntu-restricted-extras package" which supposedly contains the solution.

I am getting an error message when I try to install the package, and I've been getting this message when trying to install regular updates as well.  Here's what it says:

An Error Occurred
The following details are provided:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure-a' to correct the problem
E: _cache->open() failed, please report

So then I tried typing 'sudo dpkg --configure-a' into the terminal, and I'm just getting a bunch of gibberish. I've searched around the forums but haven't found anything helpful. Please help.

Thank you.

---

### Post by yetiman64 on 2010-04-25
I don't know how the the original disruption to dpkg occurred, however the second command you tried to fix it with should be:

```
sudo dpkg --configure -a
```note the space between the switch --configure and the switch -a (pending switch). This could make a difference in your attempt to fix the first problem and cause the resulting errors. For more info on this check 
```
man dpkg
```Also when encountering errors try to copy them to a text file (on your desktop) as they can be posted here for further evaluation (copy and paste into quote or code tags preferably).

Did you retype the error fix given in terminal or did you use copy and paste ? I personally find copy and pasting in terminal much quicker and more accurate in general.

You are right in trying to install ubuntu-restricted-extras for media playback and if you want to play encrypted dvds you'll need libdvdcss2 (different ways of installing it though - one way is by installing medibuntu repos, or by using a shellscript supplied with libdvdread4 - /usr/share/doc/*libdvdread4*/*install*-css.sh).

Sounds like its worth another try, Good Luck.

---

