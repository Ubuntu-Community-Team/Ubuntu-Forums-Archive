---
title: "I cannot connect to a Secure Server using WebDAV"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by mingohills on 2008-11-19
Ok.
My specs.  Ubuntu Intrepid on a Dell Inspiron XPS M140.

Previously I was running Hardy, but I had a harddrive crash, however the problem, started back then.  Perhaps you have seen the problems or had the problems related to secure weddav on Hardy and Intrepid, but just in case let me give you the run down.

Nautilus:
"Connect to Server. . ."
-only a custom location can be used because not https option.  If i use the davs: protocol, I get an error unauthorized.
From the location panel in a file manager.  I type in the URI with davs:// protocol, same thing.

fusedav:
-This basically freezes up or gives me permission denied. Stating GSSAPI problems.

davfs2:
-Same problem.  I go through login etc.  (I've allowed users and edited fstab). Returns a GSSAPI error.  Can't authenticate to server.  

Konquereor:
-Although I am not a fan of running to file managers, on my Hardy system this worked.  I enabled webdavs protocol and type the webdavs://<address> in the address bar.  Now I get "Connection Unexpectedly Interrupted"

Dolphin:
-I type the webdavs://<address> in the address bar.  Returns "host is broken"


Now I also use Onlinefilefolder.com (godaddy's virtual filefolder) I can access it fine from nautilus and everywhere else.  

My office's server is running Windows Server 2003.  The certificate is GoDaddy.  

I will be happy to give any and all details to anyone willing to help me.  At this point I don't care how sloppy it is.  I just need access to that server for work.

Right now I access the server from FF3, download my file, share the edited file on to my girlfriends Windows XP machine, and upload via her webdav client at the end of the day.

This is really starting to drive me up the wall.  

Any suggestion saving me the hassle of using multiple computers would be a blessing!!!

Thank you in advance for your help.

---

### Post by mingohills on 2008-12-02
Bump

---

### Post by jalfrock on 2009-01-12
In Nautilus, click on File -> "Connect to Server".

From the "Service Type" drop-down list, select "Custom Location".

In the "Location (URI)" textbox, type "davs://username@your.server.com/your/path".

Add a bookmark if you want it.

Click on "Connect".  This will also ask you for a password if your DAV share requires a password.

Best,

jalfrock

---

### Post by AFarris01 on 2009-02-09
I'm having a similar issue, but this fix does not work for me.

I need access to a webDAV share for conducting webmastering... I've tried using nautilus, konqueror, and the davfs2 route, of those only the davfs2 worked, but its terribly slow, and if i try to transfer more than 5MB at a time, it causes nautilus to lock up, and the transfer does not continue.

trying to access the share using the method above yields the nautilus error "HTTP Error, Permantly Moved"

any ideas?

---

