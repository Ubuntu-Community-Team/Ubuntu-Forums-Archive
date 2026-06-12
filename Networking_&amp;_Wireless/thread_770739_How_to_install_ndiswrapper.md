---
title: "How to install ndiswrapper?"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by puifais on 2008-04-27
I have no internet, yet, so I'm trying to install my driver, which requires ndiswrapper.  I went to their website and downloaded ndiswrapper-1.52.tar.gz onto my desktop, hoping to extract the file and see something with a .deb in it.  Instead, there's this file called INSTALL, which is more like a text instructions of how to install the application.  First thing it tells me to do is

tar zxvf ndiswrapper-version.tar.gz

The response I get is 

tar: ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I figured it probably had something to do with my .tar.gz file not being at the default directory that terminal looks for.  **But what is the default directory**?  I thought it was desktop, so that's where I placed the file.  Also, the next thing the instructions tell me to do is to change directory to the newly created ndiswrapper-version directory then run make uninstall.  **How do I change my directory in terminal**?

Just another quick question.  When I install anything using terminal, most likely, it needs to go download extra package or whatever in order to install the app.  But if I already have the .deb file of that app, my computer shouldn't need to be connected to the internet, right?

Also, I heard people saying I need to go to synaptic package manager to add ndiswrapper.  When I search for ndiswrapper or any programs I want, nothing ever come up.  Is this just because I'm not connected to the internet so synaptic package manager can't update/reload the list of available packages?

---

### Post by puifais on 2008-04-27
Great, now I know how to change the directory.  So now I can create and access the directory I said earlier.  When I put in make uninstall, though, here's what I get:

puifais@Fabian:~/ndiswrapper-1.52$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/bin/rm: cannot remove `/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': Permission denied
make: *** [uninstall] Error 1

What can I do to fix this error 1?

---

### Post by puifais on 2008-04-27
Yeah, I'm sure.  I added sudo in front of make uninstall and was able to get through that with no error, phew!  The next command "make," however, has an error that span about 30 lines...  I also move on to the next line which is "make install" and that has an error (about 2 lines) as well.  I mean, seriously, how do people normall install ndiswrapper when there's no internet?  Does everyone run into the same problem?

---

### Post by kevdog on 2008-04-27
Take a look at this thread

It should give you the basic idea:
(You might need to change some instructions to meet your situation)

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

