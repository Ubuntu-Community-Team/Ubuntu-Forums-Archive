---
title: "How to reinstall Firefox that comes with Ubuntu"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by dniezby on 2009-02-08
Ok, I was messing around and some how removed the firefox that comes with Ubuntu.  How can I repair it's installation?

If I click on the Icon, it says "Could Not Launch Application. Failed to execute child process. "Firefox" (No such file or directory)

When this happened, I was trying to upgrade firefox and didn't realize that there was a difference between the one released by Mozilla and Ubuntu.  So, I followed the steps to remove it and it appears that it removed more than I'd like. 

Here is where I was getting the info:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Here is the code that I think I executed that removed it:
```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

---

### Post by taurus on 2009-02-08
Maybe

```
sudo apt-get purge firefox
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by ptn107 on 2009-02-08
> **taurus said:**
> Maybe

```
sudo apt-get purge firefox
sudo apt-get update
sudo apt-get install firefox
```


```
sudo apt-get remove --purge --auto-remove firefox -y
rm -r ~/.mozilla/
sudo apt-get update && sudo apt-get install firefox -y
```

---

### Post by dniezby on 2009-02-08
I think I just fixed it and updated it.

I just don't know if it's the ubuntu version or the mozilla verion.

I installed this deb for i386

[http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580](http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580)

Then I went to the shortcut on my panel and fixed the destination to /opt/firefox/firefox

When I open it, it successfully shows my history and bookmarks.

The version says 3.0.6

Also, how can I make sure that it gets updated like it's supposed to?

---

### Post by ptn107 on 2009-02-08
The version you installed is _not_ the Ubuntu version.  The only way to install the Ubuntu version is via 'apt-get'*.  Using 3rd party .deb's is a sure way to get files on your system mixed up.

```
sudo apt-get install firefox
```
This will install the most current stable version of Firefox for Ubuntu (3.0.5+nobinonly-0ubuntu0.8.10.1)

---

### Post by OrangeCrate on 2009-02-08
Wouldn't the easiest way of doing this be to install the "ubufox" package from Synaptic, to the Firefox install the OP already had, to get to an Ubuntu Firefox?

---

### Post by dniezby on 2009-02-08
I ran that command and this is what I got:
```
dave@dave-laptop:~$ sudo apt-get install firefox
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  libconvert-binhex-perl libsoap-lite-perl libuser-perl wine-gecko
  libmime-types-perl libnet-ssleay-perl gdesklets-data libossp-uuid-perl
  libmime-tools-perl libossp-uuid15 ttf-liberation python-soappy
  libio-stringy-perl libnet-google-perl docbook-xsl-doc-html
  libemail-date-format-perl nullmailer hddtemp libwww-search-perl
  libmime-lite-perl libfcgi-perl python-fpconst libjcode-pm-perl
  libio-socket-ssl-perl winbind
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-laptop:~$ 

```
I'm guessing I have to unintall the deb file?  How do I do that too?
(Thank goodness for an absolute beginner forum)

---

### Post by ptn107 on 2009-02-08
You can verify if the Ubuntu version is installed by running this command in the terminal:
```
dpkg -l | grep -e firefox -e ubufox
```
If the output is:
```
ii  firefox                                    3.0.5+nobinonly-0ubuntu0.8.10.1         meta package for the popular mozilla web bro
ii  firefox-3.0                                3.0.5+nobinonly-0ubuntu0.8.10.1         safe and easy web browser from Mozilla
ii  firefox-3.0-branding                       3.0.5+nobinonly-0ubuntu0.8.10.1         Package that ships the firefox branding
ii  firefox-3.0-gnome-support                  3.0.5+nobinonly-0ubuntu0.8.10.1         Support for Gnome in Mozilla Firefox
ii  firefox-gnome-support                      3.0.5+nobinonly-0ubuntu0.8.10.1         meta package pointing to the latest gnome-su
ii  ubufox                                     0.6-0ubuntu1.8.10.1                     Ubuntu Firefox specific configuration defaul

```
then the Ubuntu version is installed and configured (make sure each line begins with 'ii').  I wouldn't worry about the .deb file as long as this output matches yours. 


*As for the list of packages you had that were no longer required, a quick
```
sudo apt-get autoremove -y
``` will clear them out.

**The 'ubufox' package is really just for Ubuntu integration and apt support.

---

### Post by dniezby on 2009-02-08
Wow, all I have to say is that this is definately going to take some time to get used to.

Well, here is how I solved (or ptn107 did for me) here is the code I pasted into terminal.

```
sudo apt-get remove --purge --auto-remove firefox firefox-3.0 firefox-3.0-branding firefox-gnome-support firefox-3.0-gnome-support ubufox -y; rm -r ~/.mozilla/; sudo apt-get install firefox -y
```

---

