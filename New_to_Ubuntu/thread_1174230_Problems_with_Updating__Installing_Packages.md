---
title: "Problems with Updating \ Installing Packages"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by RichWagon on 2009-05-30
I've been back and forth with ubuntu for the last year and always end up jumping back to windows.. but I figured I would ask for some help with this first.. 

After trying to install Qtcreator4 a few days ago I got some libqt4 related errors.. Missing dependencies.. etc..  So I tried installing the libqt4core to no avail.  The only issue with that was that I ran 
> sudo apt-get -f install

to install the broken package.. 
in which Hedgewars and Skype were uninstalled.. 

I didn't attempt to fool with that.. but then today I decided to install some more software (I didn't get any errors related to libqt4)  synaptic completely froze.. I had to log off and back on.. which closed synaptic but still said I was locked out.. after restarting I tried to 
> sudo apt-get -f install

to finish installing FCEU and an ftp software that I had chosen (which has escaped my mind)..  

The output for -f install

> Reading package lists... 0%

Reading package lists... 0%

Reading package lists... 6%

Reading package lists... Done



Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       



Reading state information... 0%

Reading state information... 0%

Reading state information... Done


The following packages were automatically installed and are no longer required:

  hedgewars-data linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

1 not fully installed or removed.

After this operation, 0B of additional disk space will be used.



Setting up rott (1.0+dfsg-2) ...

--2009-05-30 17:22:59--  [ftp://ftp.3drealms.com/share/1rott13.zip](ftp://ftp.3drealms.com/share/1rott13.zip)

           => `/usr/share/games/rott/1rott13.zip'

Resolving ftp.3drealms.com... 74.208.171.241

Connecting to ftp.3drealms.com|74.208.171.241|:21... connected.

Logging in as anonymous ... Logged in!

==> SYST ... done.    ==> PWD ... done.

==> TYPE I ... done.  ==> CWD /share ... 

No such directory `share'.



rott: Download of shareware data files failed!

md5sum: /usr/share/games/rott/1rott13.zip: No such file or directory

rott: File integrity check failed!

--2009-05-30 17:23:15--  [ftp://ftp.3drealms.com/share/1rott13.zip](ftp://ftp.3drealms.com/share/1rott13.zip)

           => `/usr/share/games/rott/1rott13.zip'

Resolving ftp.3drealms.com... 74.208.171.241

Connecting to ftp.3drealms.com|74.208.171.241|:21... connected.

Logging in as anonymous ... Logged in!

==> SYST ... done.    ==> PWD ... done.

==> TYPE I ... done.  ==> CWD /share ... 

No such directory `share'.



rott: Download of shareware data files failed!

md5sum: /usr/share/games/rott/1rott13.zip: No such file or directory

rott: File integrity check failed!

--2009-05-30 17:23:32--  [ftp://ftp.3drealms.com/share/1rott13.zip](ftp://ftp.3drealms.com/share/1rott13.zip)

           => `/usr/share/games/rott/1rott13.zip'

Resolving ftp.3drealms.com... 74.208.171.241

Connecting to ftp.3drealms.com|74.208.171.241|:21... connected.

Logging in as anonymous ... Logged in!

==> SYST ... done.    ==> PWD ... done.

==> TYPE I ... done.  ==> CWD /share ... 

No such directory `share'.



rott: Download of shareware data files failed!

md5sum: /usr/share/games/rott/1rott13.zip: No such file or directory

rott: File integrity check failed!

rott: Installation of shareware data files failed!

dpkg: error processing rott (--configure):

 subprocess post-installation script returned error exit status 1

Errors were encountered while processing:

 rott

E: Sub-process /usr/bin/dpkg returned an error code (1)

Please be specific in your answers and thanks in advance if you can help.

---

### Post by RichWagon on 2009-05-30
I'm sticking my foot in my mouth :P 
the problem was the game "rott" I tried to install.. 
the server wasn't responding apparently.. 
I thought it was a proxy problem.. 
but after disabling anon-proxy I still wasn't able to do anything.

---

### Post by RichWagon on 2009-05-30
Now while trying to install Hedgewars I get: 

> hedgewars:
 Depends: libqt4-network but it is not going to be installed
 Depends: libqt4-svg but it is not going to be installed
 Depends: libqt4-xml but it is not going to be installed
 Depends: libqtgui4 but it is not going to be installed

---

### Post by RichWagon on 2009-05-30
ok... this is getting redundant.. 
A quick removal of libqtcore4 and then installing hedgewars again worked.. 
I was trying to install libqt4-core... not knowing the difference.  
All is well again.. sorry for the waste of space.

---

