---
title: "screenlets looking for gnome-keyring in wrong place...I think"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-06-13
First, my apologies to the mods for cross posting this.  Please feel free to remove the following post.
[http://ubuntuforums.org/showthread.php?t=1182479]("http://ubuntuforums.org/showthread.php?t=1182479")

I just did a clean install of Intrepid, and I hit an issue I have never run into before.  When I run ```
screenlets-manager
``` or ```
screenlets-daemon
```from the terminal, I get the following results.
```
daniel@mypos:/usr/share/screenlets-manager$ screenlets-manager
No module RSVG , graphics will not be so good
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 28, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 51, in <module>
    from options import *
  File "/usr/lib/python2.5/site-packages/screenlets/options.py", line 216, in <module>
    import gnomekeyring
ImportError: No module named gnomekeyring

``` and
```
daniel@mypos:/usr/share/screenlets-manager$ screenlets-daemon
No module RSVG , graphics will not be so good
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-daemon.py", line 34, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 51, in <module>
    from options import *
  File "/usr/lib/python2.5/site-packages/screenlets/options.py", line 216, in <module>
    import gnomekeyring
ImportError: No module named gnomekeyring

```
For starters, there is no "gnomekeyring" on my HDD.  There is "gnome-keyring". I don't know if the terminal is just leaving out the punctuation in the error message, or if it's a typo in the source code. But either way, there is no "gnome-keyring" in ```
/usr/lib/python2.5/site-packages/screenlets
``` which is where "screenlets" seems to be looking.

Being new to Ubuntu, I simply thought that I had no "gnome-keyring", so I downloaded it and attempted to install it.
FORTUNATELY, this had an issue as well.  "Gnome-keyring" said it needed "glib-2.0 > 2.16". This time it occured to me to LOOK for the file first, and sure enough, there it was.  But it was a higher version than 2.16, and *not* where "screenlets" was looking.

  And, there-in lies my *first* post, in which I was asking how to find a "glib-2.0 >2.16" file.  There were 42 looks and no replies, which is understandable, as I spent several hours trying to find one with no luck.

Finally, the light went on, and I said to myself,"Dummy, if the apps are in your O/S, (which they are), then the problem lies in screenlets.  Which seems to leave me 2 problems.  Either (A) find a way to get screenlets to look ***where the files are***, or (B) copy and paste the files to ***where screenlets is looking***.

Somehow, neither choice seems right. I am sure there is a 3rd choice that I am overlooking.

And there-in lies *this* post.  I am completely at a loss, as to what to do.  "Screenlets", "screenlets-daemon", and "screenlets-manager" all look to ```
/usr/lib/python2.5/site-packages/screenlets/*
``` for a file that is not there.  It is, however, in several other places, *with* the hyphen.  Any and all help figuring this out will be greatly appreciated.

Since "gnome-keyring" and "glib" are both already installed, and Ubuntu is running fine, (except for the screenlets thing" Why would "gnome-keyring" not find "glib" When I tried installing it?  Surely, "gnome-keyring" and "glib" work together during the normal course of running a session. So "gnome-keyring" must know where "glib" is. I really hate to reinstall, but I am running out of options.

---

