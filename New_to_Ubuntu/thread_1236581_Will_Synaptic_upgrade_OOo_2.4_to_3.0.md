---
title: "Will Synaptic upgrade OOo 2.4 to 3.0 ?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by colintivy on 2009-08-10
Hi Folks,

I have searched the Forum for any advice so have started this thread in the absence of likely earlier posts. Forgive me if I have missed one please.

Synaptic still shows Version 2.4 as latest and I wonder if an automatic update might be on the way. If not, how do I easily install the real latest version ? Clearly the OOorg website will supply but this seems to take over what Synaptic ought to do. Interestingly it seems that the only textbook on 3.0 available appears to be in German which does not help me much!!!

colintivy :confused:

---

### Post by snowpine on 2009-08-10
If you are using Ubuntu 8.10 or older, you will never get OpenOffice 3 through the normal update process. Typically in Ubuntu, major upgrades like that are "held back" until the next release in the 6-month cycle (9.04 introduced OO3).

You're in luck, though, it's easy to do yourself. There are a few different ways of doing it, and lots of tutorials on the web and in these forums. :)

This worked for me: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by pizza-is-good on 2009-08-10
I dunno, but let me tell you what I know, and hopefully it will help you or someone else who replies.

OOo 3.0 comes in jaunty by default. When I look in synaptic for it, none of the packages show a version #.
In the OOo site, you can download OOo 3.1 for Debian. I don't know if it will run smoothly in Ubuntu.

---

### Post by pizza-is-good on 2009-08-10
OK, I guess I replied a second too late. :lolflag:

---

### Post by snowpine on 2009-08-10
The pizza-eater is correct; downloading the latest version from the OpenOffice.org website is another method you can use.

I prefer the method in my previous post (adding a PPA repository) because it means you automatically get updates as they become available. But they both work. :)

---

### Post by Paddy Landau on 2009-08-10
To upgrade to a later version of OO with 8.10 or earlier, carefully follow the instructions laid down by Hagar:

[[Tutorial] Installing OOo on Ubuntu, Debian and Co.]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68")

Or the Wiki:

[Documentation/How Tos/Installing on Debian based Distros]("http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros")

You need to follow the instructions carefully, though.

---

### Post by Paddy Landau on 2009-08-10
> **snowpine said:**
> I prefer the method in my previous post (adding a PPA repository) because it means you automatically get updates as they become available.
For some people, this is pretty buggy -- the upgrades work but cause parts of OO not to work.

You must be one of the lucky ones!

---

### Post by snowpine on 2009-08-10
> **Paddy Landau said:**
> For some people, this is pretty buggy -- the upgrades work but cause parts of OO not to work.

You must be one of the lucky ones!

Well I am using Jaunty now. :) But it did work for me back when I was using Intrepid.

---

### Post by ENigma885 on 2009-08-10
OpenOffice PPA works great for me in Jaunty and Hardy also. [SIZE="4"]Now [COLOR="Red"]3.1.0[/COLOR] is available also.[/SIZE]
_***It's easy to get it though:-*_
**1** - Open up a terminal window (Application>Accessories>Terminal)
**2** - paste ```
gksudo gedit '/etc/apt/sources.list'
```
**3** - A new text editor window will pop up. Scroll down to the end of it and paste ```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu [COLOR="Red"]hardy[/COLOR] main 
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu [COLOR="Red"]hardy[/COLOR] main 
```
in case u use [COLOR="Red"]Hardy[/COLOR] Heron 8.04, as i see in ur info,. But if u use [COLOR="Blue"]Jaunty[/COLOR] Jackalope 9.04 paste this instead
```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu [COLOR="Blue"]jaunty[/COLOR] main 
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu [COLOR="Blue"]jaunty[/COLOR] main 
```
Save and close!
**4** - Now we have to authenticate the new sources 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF
```
**5** - Update ur sources to make the new packages appear in ur Update Manager
```
sudo apt-get update
```
**6** - Now the 3.1.0 packages should appear in ur update manager as an upgrade. U can install them normally like any other updates or u can 
```
sudo apt-get upgrade
```
**7** - Finally, now u will have OpenOffice 3.1.0 PLUS any updates that will be released later on will appear in ur Update Manager as well.
[U]
**Note: Those packages r **NOT** official Ubuntu packages.[/U]

---

### Post by Paddy Landau on 2009-08-11
> **ENigma885 said:**
> ```
sudo gedit '/etc/apt/sources.list'
```
For graphical programs, always use gksu or gksudo instead of sudo:
```
gksudo gedit '/etc/apt/sources.list'
```Although sudo will usually work, sometimes there's a problem with it.

---

### Post by colintivy on 2009-08-12
Hi Paddy Landau,
Re: Extra advice...Is it your recommended addition to use gksudo just for the first terminal line or do I use it for all the sudo bits thereafter? All sounds a bit daunting but it should be worth it in the end.

colintivy :confused:

Edit Typo removed.

---

### Post by Perfect Storm on 2009-08-12
Only the line: sudo gedit '/etc/apt/sources.list' shall change to gksudo gedit '/etc/apt/sources.list'
because gedit is a gui application text editor.

a non-gui text editor like nano doesn't need gksudo so it should look like
sudo nano /etc/apt/sources.list

You can try them out to test it.


regards
A.I. Dude

---

### Post by colintivy on 2009-08-12
Hi Paddy Landau,

Do I take it that I add the gk to every subsequent line using sudo ?

colintivy :)

---

### Post by fooman on 2009-08-12
> **colintivy said:**
> Hi Paddy Landau,

Do I take it that I add the gk to every subsequent line using sudo ?

colintivy :)

as artificial intellegence has posted above....you only need to use gksudo when using a gui text editor (such as gedit).  if using a non-gui text editor (like nano) there is no need to use the "gk" prefix.

i have written a small how-to for upgrading open office to the latest ppa version. i tried to make it pretty simple and straight forward,  perhaps it will help:

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

---

### Post by ENigma885 on 2009-08-12
> **Paddy Landau said:**
> For graphical programs, always use gksu or gksudo instead of sudo...

Edited. Thanks for the notice. 
For those who want to know more about gksudo vs sudo u can check [[COLOR="Blue"][SIZE="2"][SIZE="3"]this[/SIZE][/SIZE][/COLOR]]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

### Post by Paddy Landau on 2009-08-13
> **colintivy said:**
> Do I take it that I add the gk to every subsequent line using sudo ?
As previous posters mentioned, use *sudo* for command-line commands, and *gksu* or *gksudo* (I don't know the difference) for graphical interfaces.

There's yet another good reason. From the terminal, I often use the command:
```
 gksudo gedit /etc/fstab &
```Note the trailing ampersand.

Try doing this with *sudo*. You'll find that you need to know about handling background jobs from the command line, specifically *fg*.

---

### Post by Paddy Landau on 2009-08-13
I've just discovered the difference between gksu and gksudo.

gksu acts like sudo. So don't use it for GUI programs.

Having read more about it, I suspect that while sudo is not always safe (e.g. with Firefox), gksudo always is. So, my question to those who know a little more is: Could one *always* use gksudo, even when sudo would have been fine?

---

### Post by Tootler on 2009-08-14
I finally got 00 3.1 installed after a number of false starts, but all the icon images have disappeared. At one point various "unknown media type" messages flashed across the screen but were gone too quickly for me to note them down.

During the various attempts at installing it, including the final successful one I kept getting warning messages about missing language packs. On the final attempt I noted the messages and here they are.

```
perl: warning: Setting locale failed
perl: warning: Please check that your locale settings
	LANGUAGE = (unset);
	LC_ALL = (unset)
	LANG = 	"en_GB.UTF-8"
are supported and installed on your system
perl: warning: Falling back to the standard locale ("C")
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: 
locale: Cannot set LC_ALL to default locale:
Gtk -WARNING **: Locale not supported by C library
	Using the fallback 'C' locale. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line54, <> line 1.
Gtk -WARNING **: Locale not supported by C library
	Using the fallback 'C' locale. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 60, <> line 1.
Gdk -WARNING **: Locale not supported by C library
	Using the fallback 'C' locale. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 60, <> line 1.
	
```

I think this may be down to an upgrade I did just before I started because there were a number of error messages flashed across the screen during the upgrade which suggests the upgrade was buggy. The upgrade was of a couple of libraries, I can't remember which now, but if that is what the problem is, then I will post a new thread as there is clearly something needs fixing.

---

### Post by Paddy Landau on 2009-08-15
> **Tootler said:**
> I finally got 00 3.1 installed after a number of false starts, but all the icon images have disappeared...
I strongly recommend that you follow Hagar's instructions (as per [post #6]("http://ubuntuforums.org/showthread.php?p=7763556#post7763556")):
[[Tutorial] Installing OOo on Ubuntu, Debian and Co.]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68")

In step 1 ("Remove all the packages from the installed version"), be sure first to exit *all* instances of OpenOffice, including the tray's QuickStarter if you have it.

You may find that you have to delete your directory [COLOR=DarkRed]~/.openoffice.org[/COLOR], which would mean that you'll lose all your preferences and would have to set them again.

I found that carefully following those steps solved my problems.

The alternative is either to go back to the default OO 2.4, which I understand you don't want to do, or to upgrade to Jaunty.

---

### Post by philinux on 2009-08-15
Click the backports link. I think OO 3 is backported to hardy.

---

### Post by Paddy Landau on 2009-08-15
> **philinux said:**
> Click the backports link. I think OO 3 is backported to hardy.
Thanks, I didn't know about that!

---

### Post by colintivy on 2009-08-15
Hi Paddy & other helpful bodies,

There seems to be a distinct high level of commonality amongst you thank you all. I have other more pressing matters in hand right now (Home on to separate partition that I want to achieve when time permits) but I am sure the advice above will be quite sufficient. The use of gk seems to be valuable and not evident within some earlier posts which I will explore. I note that there is a tendency to advise Copy/paste rather that rely on typing without errors  which seems to be worthwhile, is this a correct observation? I have generally tried to edit directly in such activities but with much diligence to avoid typos. Solved will be attached when proven !

a grateful colintivy :)

---

### Post by Paddy Landau on 2009-08-15
> **colintivy said:**
> ... there is a tendency to advise Copy/paste rather than rely on typing 
Even better...

Understand the command before using it.

After all, sometimes a poster types it wrong!

To understand a command, go to the terminal and use the *man* command. For example:
```
man sudo
```When that doesn't clarify things, use Google. There are plenty of excellent sites about Linux out there.

---

### Post by colintivy on 2009-08-18
Hi Paddy,

Thanks for that, I will man more often!
Pardon my ignorance... how do I mark the thread as Solved ? I cannot find a reference to this anywhere. Expected it under Tools but to no avail.

colintivy :)

---

### Post by Paddy Landau on 2009-08-18
> **colintivy said:**
> how do I mark the thread as Solved ?
The solved-marking mechanism broke on this forum, so it's no longer used.

Go to your [very first post in this thread]("http://ubuntuforums.org/showthread.php?p=7763476#post7763476"), press *Edit* and *Go Advanced*. Add the text "[Solved]" in front of your title. Press *Save Changes*.

---

### Post by colintivy on 2009-08-27
Hi Paddy!

Thanks for that (as you will see) just got back to the forum. Should have sorted the method out myself but am suitably humble and educated.

colintivy :) :)

---

