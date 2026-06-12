---
title: "Can't compile wireshark 1.2.1 (GTK+ ??)"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by relay_man on 2009-08-16
I'm trying to compile the newest version of wireshark for use in troubleshooting some problems I'm having on my network at home.
I've been following the guide here:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
:confused:
So far, things have been going well.  I've been able to find/fix all of the missing items until I got to here:

[checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: GTK+ 2.4 or later isn't available, so Wireshark can't be compiled]

Can anyone suggest what I need to do to resolve the GTK+ problem?  I'm not sure, but this may be the last thing to resolve in getting  wireshark going.

Thanks

---

### Post by Bachstelze on 2009-08-16
Install [font=monospace]libgtk2.0-dev[/font].

---

### Post by relay_man on 2009-08-16
Thanks for the prompt reply, but I think I've already got libgtk2.0 and the currently installed version from the intrepid repos is 2.1.4.
I just noticed that the config.log is asking for GTK+ 2.4 or better.
Perhaps I'd better stop here and research some more.
It may be a major nightmare to get 2.4 installed and working.(if it can be done at all)


Thanks

---

### Post by Bachstelze on 2009-08-16
You have libgtk2.0, but you don't have libgtk2.0-dev, hence your problem. Also, the version of GTK+ in the Intrepid repositories is 2.14.4:

[http://packages.ubuntu.com/intrepid/libgtk2.0-dev](http://packages.ubuntu.com/intrepid/libgtk2.0-dev)

---

### Post by relay_man on 2009-08-16
You are right!

I'll continue to slug it out with config in the wireshark setup now.

Your persistance is very much appreciated.


Thank You

---

### Post by mikull on 2009-08-17
dependencies are heaps..
i have the same problem with wireshark.
i try to install libgtk2.0-dev i get other dependencies issues.
libcairo and shi**
i am totally fed up
its 4 am and i have been trying to install this on my hardy for 2 hrs now.
any ideas guys

i am running hardy i386
ntop works but not this.
what to do..!?
please help! F1 F1

---

### Post by Bachstelze on 2009-08-17
Paste the exact error message you're getting, and tone down the language.

---

### Post by mikull on 2009-08-18
Sorry about my last post mate..was frustrated..
appreciate you getting back to me.
when i do a ./configure i get the below error message:

*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: GTK+ 2.4 or later isn't available, so Wireshark can't be compiled


After this i decided to install gtk+-2.16.0
I get another dependency issue..here it is..

checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.19.7    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

Requested 'glib-2.0 >= 2.19.7' but version of GLib is 2.16.3
No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Could you please help me with this.
I need to get wireshark running! 
thanks heaps..

EDIT: i have installed libatk-dev..
when i try and install libpango from SPM,i get the below:

ibpango1.0-dev:
 Depends: libcairo2-dev but it is not going to be installed
 Depends: libfontconfig1-dev but it is not going to be installed
 Depends: libfreetype6-dev but it is not going to be installed
  Depends: libpango1.0-0 (=1.20.1-1) but 1.20.5-0ubuntu1 is to be installed
 Depends: libxft-dev but it is not going to be installed

and it doesn't install.

and when i install libcairo2-dev from SPM i get this:

  Depends: libcairo2 (=1.6.0-0ubuntu1) but 1.6.0-0ubuntu2 is to be installed
 Depends: libfontconfig1-dev but it is not going to be installed
 Depends: libfreetype6-dev but it is not going to be installed

i did do a force version for libcairo2 and when i try again for libcairo2-dev i get the below:
 Depends: libfontconfig1-dev but it is not going to be installed
 Depends: libfreetype6-dev but it is not going to be installed

it seems like a vicious circle!

---

### Post by Panganat on 2009-09-06
this worked for me  :o [http://www.getdeb.net/release/](http://www.getdeb.net/release/)

---

