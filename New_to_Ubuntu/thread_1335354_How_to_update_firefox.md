---
title: "How to update firefox"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by sagarsiddhpura on 2009-11-23
I have downloaded firefox 3.5.5.tar.bz2 from Mozilla site.
How should i update my installed firefox using that achieve?

Sagar Siddhapura

---

### Post by ukripper on 2009-11-23
Well that is why it is not recommended just use the tar balls from websites.

If you want your apps to be updated you need to make sure they are pulled from repos not from indivdual websites. For firefox 3.5 if you are using Karmic(9.10) it is already there. But if you using 9.04 then you need to add via ppa or ubuntuzilla [http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/). Check this link - [http://tombuntu.com/index.php/2009/07/03/install-firefox-35-in-ubuntu-904/](http://tombuntu.com/index.php/2009/07/03/install-firefox-35-in-ubuntu-904/)

---

### Post by gdonwallace on 2009-11-23
There are two ways to handle this.  As stated in the previous post, if you are not running 9.10, then you need to follow the links provided on how to add the Repo's for firefox.

The other way, is to continue what you are doing.  The only downside is that when another update comes along, you have to download and update again; just as you did this time.  If that is not a problem, then go for it.  Anywho; unzip the file and it will create a firefox directory (/firefox) and it may be followed by the version number (/firefox-3.5)  It is best to put programs that you install manually into the /opt directory; as this directory is not touched during Ubuntu (or linux for that matter) updates.  To do that just sudo mv <directory> /opt/  This will move firefox to that directory.  

As for plugins, bookmarks, etc.  That will all be there for you.  Because Linux uses a unified directory structure (meaning all versions or distros that are Debian have the same directories), the new install will be able to locate the directory that the plugins, etc are stored in.

no problems.  I find on Firefox and OpenOffice that I like to do the manual install, because it affords me a little more control over when to do the update or when not too.  

Hope this helps.

Good luck.

---

### Post by aysiu on 2009-11-23
If you absolutely feel the need to use tarballs instead of the built-in update manager, this is the easiest way to do it:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

