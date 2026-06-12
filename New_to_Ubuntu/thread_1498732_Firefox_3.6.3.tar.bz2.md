---
title: "Firefox 3.6.3.tar.bz2"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-06-01
Having some problems opening a few places with Firefox. Current version is listed (under Help > about) as 3.5.9. Went to Mozilla and downloaded the latest version to see if that would correct the problem. Used the following install using terminal:

[I]cd Downloads
tar -xvjf firefox-3.6.3.tar.bz2[/I]

It went thru the process but when I check the FF Help > About it still shows the 3.5.9 version.

Any suggestions?

---

### Post by -humanaut- on 2010-06-01
I don't know if that will fix your problems with firefox or now but compiling a package from source should look more like this

bzip2 -d package.tar.bz2
tar -xvf package.tar
cd package
./configure
./install or make

---

### Post by Linux_junkie on 2010-06-01
Looks to me that you've installed 3.6.3 has been installed alongside previous version and Ubuntu is still using older version as the default web browser.

---

### Post by flyfishingphil on 2010-06-01
> **-humanaut- said:**
> I don't know if that will fix your problems with firefox or now but compiling a package from source should look more like this

bzip2 -d package.tar.bz2
tar -xvf package.tar
cd package
./configure
./install or make
Was following directions on another post for installing the FF when it's in the tar.bz2. What I did was what was listed. Like I said it appeared to go thru all of the steps, just doesn't show anywhere.

Not sure what you are saying humanaut. I went to Mozilla and downloaded the package for linux and that's what came down.

Linux_junkie. Checked under applications > internet and only one FF showing and it's the 3.5.9 version. Is ther someplace else I need to check to see if it's installed but not the "default" choice?

---

### Post by ajgreeny on 2010-06-01
All your command did was to extract the tarball you downloaded to a folder in Downloads called firefox-3.6.3 or something similar, so look for that in nautilus.

Somewhere in that folder there will be a file called simply firefox, in fact I think there are two from memory, one is the executable, the other a script to run the executable.  Check that the script itself is executable, I think it is by default, and run it by double clicking it.  Firefox 3.6.3 should start up and automatically find your current profile.

---

### Post by flyfishingphil on 2010-06-01
> **ajgreeny said:**
> All your command did was to extract the tarball you downloaded to a folder in Downloads called firefox-3.6.3 or something similar, so look for that in nautilus.

Somewhere in that folder there will be a file called simply firefox, in fact I think there are two from memory, one is the executable, the other a script to run the executable.  Check that the script itself is executable, I think it is by default, and run it by double clicking it.  Firefox 3.6.3 should start up and automatically find your current profile.
Interesting. Followed your instructions. Clicked on the Firefox in the contents. It asked if I wanted to run it, clicked on that and up pops a new FF browser page. Clicked on the Help > About and it shows version 3.5.9. Guess I'll dump the one I just downloaded and start over to see if I can get an updated ubuntu version.

Thanks.

EDIT ADD:

Did some checking around and found that what I think I need is the JRE 6.20 version of Java, not the 3.6.3 version of Firefox. Will follow that further and post what I find, if I can get it to work right.

---

### Post by flyfishingphil on 2010-06-01
Did some checking and, from what I can find, everything is current and operational. Having problems at Pogo games. Tried to Chat with Tech support but they were unable to see my text entries. Go figure!

Would guess problem is at site.

Consider this solved.

---

