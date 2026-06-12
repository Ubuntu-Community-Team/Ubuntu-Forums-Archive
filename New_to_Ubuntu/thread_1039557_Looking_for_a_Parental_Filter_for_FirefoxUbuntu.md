---
title: "Looking for a Parental Filter for Firefox/Ubuntu"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-14
I've just finished putting together a PC for someone who wants to have a separate account setup for their little girl, and want a parental controls filter enabled on that account so they don't have access to adult oriented websites.  What's recommended for this?

---

### Post by bumanie on 2009-01-14
I think Dans Guardian can help you. [Look here]("https://wiki.edubuntu.org/ContentControl") for more information.

---

### Post by lykwydchykyn on 2009-01-14
Here's a link to a setup howto.  It's a little old, but it should still work.
[http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

You can probably skip the bit about firehol for younger children, and just setup proxying in firefox or whatever browser is being used.  

I use this setup with my kids and it works well.  If you have questions, just ask.

---

### Post by crjackson on 2009-01-14
> **diablo75 said:**
> I've just finished putting together a PC for someone who wants to have a separate account setup for their little girl, and want a parental controls filter enabled on that account so they don't have access to adult oriented websites.  What's recommended for this?

[Read This Parental Control HOW TO]("http://ubuntuforums.org/showthread.php?t=843510&highlight=timekpr")

[TIME KEEPER HOW TO]("http://ubuntuforums.org/showthread.php?t=887769")

[and OPENDNS - FREE & awesome]("http://www.opendns.com/")

---

### Post by MrWES on 2009-01-14
> **lykwydchykyn said:**
> Here's a link to a setup howto.  It's a little old, but it should still work.
[http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

You can probably skip the bit about firehol for younger children, and just setup proxying in firefox or whatever browser is being used.  

I use this setup with my kids and it works well.  If you have questions, just ask.

So is it necessary to install the firehol package? Or just don't configure it?

Bill

---

### Post by crjackson on 2009-01-14
> **MrWES said:**
> So is it necessary to install the firehol package? Or just don't configure it?

Bill

Have a look at the 1st link I posted above.

---

### Post by Dr Small on 2009-01-14
I think this is the best guide for setting up web filter as a transparent proxy (no need to configure Firefox to use the proxy) with Squid + DansGuardian:
[http://www.linux.com/articles/113733](http://www.linux.com/articles/113733)

---

### Post by moody_mark on 2009-01-14
For the browser if using Firefox, Id recommend pro-con latte

[https://addons.mozilla.org/en-US/firefox/addon/1803]("https://addons.mozilla.org/en-US/firefox/addon/1803")

---

### Post by ChildOfMana on 2009-01-14
An alternative to a software package is to use [OpenDNS]("http://www.opendns.com/").

It's very easy to set up (full instructions on the site) and if you sign up for an account (it's free) you can set a content filter to deny access to any site (or set of search results, for example) you want.

The disadvantage to this of course is that because the service runs on the OpenDNS servers it will affect all the accounts on your network in the same way.

Maybe not what you're looking for but worth a mention nonetheless, if only for it's ease of use - and the fact that you'll likely get faster DNS resolution (depending in what area you live) as well.

---

### Post by bodhi.zazen on 2009-01-14
Some really nice suggestions / links in this thread, thanks everyone.

---

### Post by diablo75 on 2009-01-16
I downloaded the webcontentcontrol deb package from this address:

[https://launchpad.net/webcontentcontrol/+download](https://launchpad.net/webcontentcontrol/+download)

And installed it.  I've messed with it for just a couple minutes on my own PC and I think it will work nicely (it was very easy to setup).

But I'd like to uninstall it from my own computer.  How do I do that?

---

### Post by bodhi.zazen on 2009-01-16
> **diablo75 said:**
> I downloaded the webcontentcontrol deb package from this address:

[https://launchpad.net/webcontentcontrol/+download](https://launchpad.net/webcontentcontrol/+download)

And installed it.  I've messed with it for just a couple minutes on my own PC and I think it will work nicely (it was very easy to setup).

But I'd like to uninstall it from my own computer.  How do I do that?

You can remove the package with any of several tools. Synaptic or Add/Remove.

From the command line 

sudo apt-get remove package

pdkg -r package

Note: those last two are just package not package-1.2.3.deb

---

### Post by diablo75 on 2009-01-17
Well here's what I tried:

```
user@userpc:~$ sudo dpkg -r webcontentcontrol
(Reading database ... 137435 files and directories currently installed.)
Removing webcontentcontrol ...
prerm remove|deconfigure called
Unconfiguring dansguardian+firehol+tinyproxy
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
 * Stopping Firewall firehol                                             [ OK ] 
Stopping tinyproxy: tinyproxy.
 * Stopping DansGuardian dansguardian                                    [ OK ] 
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
All OK! Everything was stopped
Running from /home/user
===>importing /usr/share/webcontentcontrol/backup.dgs.full
tar: /usr/share/webcontentcontrol/backup.dgs.full: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dpkg: error processing webcontentcontrol (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 webcontentcontrol
user@userpc:~$ 

```

If I try to remove the firehol or dandguardian packages via synaptic, I get this error:

E: webcontentcontrol: subprocess pre-removal script returned error exit status 2

So... how do I fix this?

---

### Post by diablo75 on 2009-01-17
Bump.

I need to get this removed and fixed.  Since installing this software, I have been unable to VNC into my PC!

---

### Post by lykwydchykyn on 2009-01-17
Does this file exist: /usr/share/webcontentcontrol/backup.dgs.full?
try this:
```

sudo aptitude purge firehol tinyproxy dansguardian

```

Probably firehol is blocking your vnc.

---

### Post by diablo75 on 2009-01-17
```
user@userpc:/usr/share/webcontentcontrol$ ls
CustomApps.conf  reference  scripts  webcontentcontrol_GUI
zeke@zekepc:/usr/share/webcontentcontrol$ sudo aptitude purge firehol tinyproxy dansguardian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  webcontentcontrol 
The following packages will be REMOVED:
  dansguardian{p} firehol{p} tinyproxy{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3510kB will be freed.
The following packages have unmet dependencies:
  webcontentcontrol: Depends: firehol but it is not installable
                     Depends: tinyproxy but it is not installable
                     Depends: dansguardian but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
webcontentcontrol

Score is 121

Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  aggregate{u} clamav{u} clamav-base{u} clamav-freshclam{u} dansguardian{p} 
  firehol{p} gambas2-gb-form{u} gambas2-gb-form-dialog{u} gambas2-gb-gtk{u} 
  gambas2-gb-gui{u} gambas2-gb-qt{u} gambas2-gb-qt-kde{u} 
  gambas2-gb-qt-kde-html{u} gambas2-gb-settings{u} gambas2-runtime{u} 
  libclamav5{u} tinyproxy{p} webcontentcontrol{a} 
0 packages upgraded, 0 newly installed, 18 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 29.7MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 137501 files and directories currently installed.)
Removing aggregate ...
Removing webcontentcontrol ...
prerm remove|deconfigure called
Unconfiguring dansguardian+firehol+tinyproxy
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
 * Stopping Firewall firehol                                             [ OK ] 
Stopping tinyproxy: tinyproxy.
 * Stopping DansGuardian dansguardian                                    [ OK ] 
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
All OK! Everything was stopped
Running from /
===>importing /usr/share/webcontentcontrol/backup.dgs.full
tar: /usr/share/webcontentcontrol/backup.dgs.full: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dpkg: error processing webcontentcontrol (--remove):
 subprocess pre-removal script returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 webcontentcontrol
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

user@userpc:/usr/share/webcontentcontrol$ 

```

The file you asked about did not exist, even after using the deb file to reinstall the package.  Running the command you suggested produced the above output.

Arrgh!
](*,)

---

### Post by lykwydchykyn on 2009-01-18
try:
```

touch /usr/share/webcontentcontrol/backup.dgs.full

```

Then try purging all that stuff.  If that doesn't cut it, try:
```

sudo dpkg --force-all -r webcontentcontrol

```

Sounds like a bit of bad packaging on someone's part.  You should report this to whoever puts webcontentcontrol together.

---

### Post by diablo75 on 2009-01-18
Got it fixed:

[https://bugs.launchpad.net/webcontentcontrol/+bug/318301](https://bugs.launchpad.net/webcontentcontrol/+bug/318301)

---

