---
title: "Need help with Pidgin.  Needs SSL library for MSN support"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by randell6564 on 2007-06-30
hey folks!
I installed Pidgin on Feisty fawn, but it said that it needs some SSL library for Hotmail/MSN support.
Can someone tell me where to get this library?
Thanks!

---

### Post by randell6564 on 2007-06-30
'bump'!

---

### Post by babis85 on 2007-07-05
Hi, you just need to install the following packages:

```
sudo apt-get install libnss-dev libnspr-dev
```

---

### Post by randell6564 on 2007-07-06
> **babis85 said:**
> Hi, you just need to install the following packages:

```
sudo apt-get install libnss-dev libnspr-dev
```
Well Thank You My Friend!  Just got home from work, going to log off Windoze, log onto Ubuntu and see if indeed these packages work!

I'll post the results.  Thanks again!

---

### Post by randell6564 on 2007-07-06
Well, sorry to say that it didn't work!  I even tryed restarting after installing **libnss-dev** and** libnspr-dev**.  Nothing-Doing!

This really Sucks!

---

### Post by cactaur on 2007-07-06
Hi, do you think you could post the actual output or the actual name of the library? This might help narrow down the programs you might need to install.

---

### Post by randell6564 on 2007-07-06
> **cactaur said:**
> Hi, do you think you could post the actual output or the actual name of the library? This might help narrow down the programs you might need to install.
Hi! "The actual name of the library" is the big mystery in my case!  The "output" only say's that I need to install a supported library.,thats it!

Pidgin works right out of the box for my Yahoo account, but gives the above error when attempting to use my Hotmail account.

---

### Post by Labaro on 2007-07-06
Hi, to make it work, after making
```
sudo apt-get install libnss-dev libnspr-dev
```
yo have to do the ./configue, sudo make and sudo make install again.
Then, it'll work

---

### Post by randell6564 on 2007-07-06
> **Labaro said:**
> Hi, to make it work, after making
```
sudo apt-get install libnss-dev libnspr-dev
```
yo have to do the ./configue, sudo make and sudo make install again.
Then, it'll work
Could you please assist me in just HOW to do the "./configure, sudo make and sudo make install?"
Have no idea what this means!  
Thanks!

---

### Post by Labaro on 2007-07-06
They three separate commands:
```
sudo ./configure

sudo make

sudo make install
```

Run all of them and you'll have it installed and MSN compatible

---

### Post by randell6564 on 2007-07-06
> **Labaro said:**
> They three separate commands:
```
sudo ./configure

sudo make

sudo make install
```

Run all of them and you'll have it installed and MSN compatible
```
sudo ./configure
```
> sudo: ./configure: command not found

---

### Post by scxtt on 2007-07-06
did you install it from source or from a .deb?

---

### Post by randell6564 on 2007-07-06
> **scxtt said:**
> did you install it from source or from a .deb?
.deb
Thanks!

---

### Post by scxtt on 2007-07-06
then it looks like the .deb your got wasn't compiled w/ SSL support ... are you just trying to sign in to an MSN account?

---

### Post by babis85 on 2007-07-07
Just download this package [http://sourceforge.net/project/downloading.php?group_id=235&filename=pidgin-2.0.2.tar.bz2](http://sourceforge.net/project/downloading.php?group_id=235&filename=pidgin-2.0.2.tar.bz2)

To unpack it, go to the directory where it was downloaded and type in a terminal 
```
tar -xvfj pidgin-2.0.2.tar.bz2
```
Then, go to pidgin-2.0.2 directory and type the three below commands:
```

./configure
make
sudo make install

```

The overall process would probably succeed if there will be no error after running configure. In case sth goes wrong after configure, reply with its output.

Informatively: The first command just checks if the required packages are installed in your system.
The second one, is responsible for what we call "compile".
The third, makes the installation at the appropriate directories.

I hope all these help you.

---

### Post by randell6564 on 2007-07-07
> **scxtt said:**
> then it looks like the .deb your got wasn't compiled w/ SSL support ... are you just trying to sign in to an MSN account?
Yes, I'm trying to activate/sign-in to my MSN Hotmail account.  I actually downloaded and installed **Pidgin** straight from the [URL="http://pidgin.im/pidgin/home/"]Pidgin website
[/URL] the first time!  After that didn't work, (Same Error) I then got the .deb package from a friend who compiled it from source. (Same Error again)

So Even the makers of Pidgin did not include the needed SSL Library for MSN to work on Ubuntu Feisty!
The basic question here is.,What SSL Library is needed in order to make Pidgin work for MSN!?

---

### Post by randell6564 on 2007-07-07
> **babis85 said:**
> Just download this package [http://sourceforge.net/project/downloading.php?group_id=235&filename=pidgin-2.0.2.tar.bz2](http://sourceforge.net/project/downloading.php?group_id=235&filename=pidgin-2.0.2.tar.bz2)

To unpack it, go to the directory where it was downloaded and type in a terminal 
```
tar -xvfj pidgin-2.0.2.tar.bz2
```
Then, go to pidgin-2.0.2 directory and type the three below commands:
```

./configure
make
sudo make install

```

The overall process would probably succeed if there will be no error after running configure. In case sth goes wrong after configure, reply with its output.

Informatively: The first command just checks if the required packages are installed in your system.
The second one, is responsible for what we call "compile".
The third, makes the installation at the appropriate directories.

I hope all these help you.
Thanks my friend! I'm gonna try it.  I'll post the results!

---

### Post by randell6564 on 2007-07-07
Here is the results 'babis'
```
tar -xvfj pidgin-2.0.2.tar.bz2
```
> tar: j: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
The .tar file is in a folder within my home dir. which is where I CD'd to before trying to unpack.

---

### Post by babis85 on 2007-07-07
Sorry, 
just omit '-'. That is, run "tar xvfj ......"

---

### Post by scxtt on 2007-07-07
> **randell6564 said:**
> Yes, I'm trying to activate/sign-in to my MSN Hotmail account.  I actually downloaded and installed **Pidgin** straight from the [URL="http://pidgin.im/pidgin/home/"]Pidgin website
[/URL] the first time!  After that didn't work, (Same Error) I then got the .deb package from a friend who compiled it from source. (Same Error again)

So Even the makers of Pidgin did not include the needed SSL Library for MSN to work on Ubuntu Feisty!
The basic question here is.,What SSL Library is needed in order to make Pidgin work for MSN!?i doubt pidgin is technically responsible for supplying the "SSL Library" - most likely it's a dependency/requirement your system should have - i doubt "dpkg -i pidgin.deb" resolves dependencies ... i have pidgin installed in gentoo, and it was built w/ an "ssl" flag - i have no problems signing into my hotmail account ... my guess is  that somewhere in the configure script there's a way to specify including ssl or not ...

---

### Post by randell6564 on 2007-07-07
Thank you 'babis85', and thank you to everyone else as well!
I finally got it installed using the .tar file from [http://sourceforge.net/project/downloading.php?group_id=235&filename=pidgin-2.0.2.tar.bz2](http://sourceforge.net/project/downloading.php?group_id=235&filename=pidgin-2.0.2.tar.bz2).
I had to install **glib2.0** and **gtk+ 2.0** from synaptic but that part was easy!  The terminal informed me of what I was missing.  
Thanks again!

---

### Post by randell6564 on 2007-07-08
CRAP!
It WAS working!  Now It will not start anymore.  I tryed starting it from terminal and get this error:
> bigboss@bigboss-desktop:~$ pidgin
Segmentation fault (core dumped)
Anyone know what this means and how to fix it?
Thanks!

---

### Post by babis85 on 2007-07-08
What did you do?
Did you uninstall the previous installation with the .deb?
Try running from a console the following command and post the output
```
pidgin -d
```

---

### Post by randell6564 on 2007-07-08
> **babis85 said:**
> What did you do?
Did you uninstall the previous installation with the .deb?
Try running from a console the following command and post the output
```
pidgin -d
```
Yes, I uninstalled the pidgin .deb through synaptic before installing the .tar
Here is the output of **pidgin -d**
> bigboss@bigboss-desktop:~$ pidgin -d
(11:00:40) plugins: probing /usr/local/lib/pidgin/timestamp.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/xmppconsole.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/pidginrc.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/convcolors.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/gestures.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/iconaway.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/history.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/spellchk.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/notify.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/ticker.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/extplacement.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/relnot.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/gtkbuddynote.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/timestamp_format.so
(11:00:40) plugins: probing /usr/local/lib/pidgin/markerline.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libqq.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libgg.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libjabber.so
(11:00:40) plugins: /usr/local/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(11:00:40) plugins: probing /usr/local/lib/purple-2/ssl.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libicq.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/ssl-nss.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/statenotify.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/ssl-gnutls.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libnovell.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libzephyr.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/log_reader.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/offlinemsg.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/liboscar.so
(11:00:40) plugins: /usr/local/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(11:00:40) plugins: probing /usr/local/lib/purple-2/psychic.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libmsn.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libsimple.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/autoaccept.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/joinpart.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/idle.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libyahoo.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/buddynote.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libirc.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/newline.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libxmpp.so
(11:00:40) plugins: probing /usr/local/lib/purple-2/libaim.so
(11:00:40) util: Reading file accounts.xml from directory /home/bigboss/.purple
(11:00:40) util: Reading file status.xml from directory /home/bigboss/.purple
(11:00:40) stun: using server 
(11:00:40) stun: using server 
(11:00:40) gtkblist: added visibility manager: 1
(11:00:40) docklet: created
(11:00:40) util: Reading file blist.xml from directory /home/bigboss/.purple
(11:00:40) prefs: Reading /home/bigboss/.purple/prefs.xml
(11:00:40) prefs: Finished reading /home/bigboss/.purple/prefs.xml
(11:00:40) prefs: removing pref /purple/debug/timestamps
(11:00:40) plugins: Unable to find saved plugin /usr/lib/gaim/docklet.so
(11:00:40) plugins: Loading saved plugin /usr/local/lib/pidgin/notify.so
(11:00:40) Session Management: ICE initialized.
(11:00:40) Session Management: Connecting with no previous ID
(11:00:40) Session Management: Handling new ICE connection... (11:00:40) done.
(11:00:40) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000118391764000000052830046
(11:00:40) Session Management: Using pidgin as command
(11:00:41) account: Connecting to account pipsquacktiger
Segmentation fault (core dumped)

---

### Post by randell6564 on 2007-07-08
any luck at deciphering?

---

### Post by slyckstyx on 2007-07-12
> **Labaro said:**
> Hi, to make it work, after making
```
sudo apt-get install libnss-dev libnspr-dev
```
yo have to do the ./configue, sudo make and sudo make install again.
Then, it'll work

:) This worked perfectly.  Thanks!

---

### Post by Contrarian on 2007-07-12
> **babis85 said:**
> Hi, you just need to install the following packages:

```
sudo apt-get install libnss-dev libnspr-dev
```

How am I suppose to know this based on the error message?  

It's things like this that still annoy me about linux.  When missing libraries how are you suppose to know which library you need and where to get it?  Aside from doing a search for someone whose had similar problems on google.

---

### Post by sambehera on 2007-07-14
> **slyckstyx said:**
> :) This worked perfectly.  Thanks!

This worked perfectly.  Thanks!

and thanks for pointing out that it worked perfectly ...

---

### Post by kevdog on 2007-07-14
Just to chime in an alternative method on how to do this, I am using feisty and installed it via instructions listed here:

[http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/pidgin-previously-gaim-on-ubuntu-feisty-fawn](http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/pidgin-previously-gaim-on-ubuntu-feisty-fawn)

I know it requires a third party repository which is often frowned upon, but the other simply backported pidgin and the plugins from the gusty build.

It works for me.  Whether something breaks in the future Ill find out.

---

### Post by Faust942 on 2007-07-17
I already did 

sudo apt-get install libnss-dev libnspr-dev

And it tells me its already installed.

Does this mean I still should ./configure, make, sudo make install?

---

### Post by SuperAndy on 2007-07-17
i have recently started getting a seg fault as well. worked fine, and i changed nothing. i have reverted to the gaim beta shipped with feisty. tried a reinstall as well. any help on that would be great

---

