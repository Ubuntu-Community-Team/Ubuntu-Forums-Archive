---
title: "Create a local folder that connects to remote sftp/ftp folder"
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by goemonburo on 2014-04-24
I have spent almost an hour trying to figure out how to do this in Lubuntu.  I've seen great Ubuntu and Fedora walk throughs but don't seem to have those same tools in Lubuntu.  All I want is a folder on the desktop where I can drag/drop to my remote FTP.

Every option I have within the GUI in Lubuntu seems to assume that I want to make a new LOCAL folder.  There's no option to specify the location or enter login credentials.

Please help me out if you know what I need to do.  Thank you!

---

### Post by goemonburo on 2014-04-25
Or maybe this could be a question about how to set this up via the command line?  All the GUI tutorials I see are for Ubuntu and it looks totally different from what I'm seeing on my desktop.  In Fedora this took only a few moments...can't believe that's not similarly easy to do here.  Can anyone help?  Either with a brief GUI for Lubuntu tutorial or something via the command line?  Thank you!  :-)

---

### Post by goemonburo on 2014-04-26
This should not have been this difficult:  1) mkdir SomeLocalFolder  2) "sshfs login@YourRemoteSite: ~/SomeLocalFolder"  Done.  Why someone couldn't have offered this to me a day ago is mystifying.  But it's all figured out now.  Thanks!

---

