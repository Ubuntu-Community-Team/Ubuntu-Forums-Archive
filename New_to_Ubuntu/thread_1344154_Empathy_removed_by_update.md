---
title: "Empathy removed by update"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by David Oxland on 2009-12-02
I had a strange one yesterday;  
Updates came and warned of a whole bunch of files to be removed.  Went ahead with the updates and now Empathy has been removed completely. Still shows in Synaptic as available for install.
Questions:
-Any one know why or had similar? 
-Anything do do with complete removal and reinstall of Flashplayer?
-Is it OK to reinstall? 

Thanks 
David
Karmic 64bit

---

### Post by Locke_99GS on 2009-12-02
Personally, I tried to give Empathy a chance, and used it for a couple of months before removing it myself and instaling Pidgin in it's place :) so I'm unaware of what went wrong there.

It is unrelated to Flash.

You can re-install it, and it should pick up right where it left off, with all your accounts and everything still in-tact. Removing a package leaves it's configuration in tact, unless it was specifically "purged", which is done manually, not automatically.

```
sudo aptitude install empathy
```

---

### Post by corncob on 2009-12-02
I'd go ahead and reinstall Empathy.  If you fear that there is some kind of a conflict with your upgrades you could install Pidgin instead.  I've used them both and, for my purposes, I don't see much difference.

---

### Post by David Oxland on 2009-12-02
Locke_99GS
This is a bit unusual for me;  I went to Ubuntu software center and tried to add Empathy,,,,,,,,,gave broken missing dependencies message. 
So, went to synaptic and tried empathy common.,,,,same messages.
Tried sudo apt-get install Empathy,,,,,,,,,,same messages.
all this because I'm used to using apt-get,
then (as you instructed),
sudo aptitude install empathy ,,,,,,and got all this
- 
.david@david-desktop:~$ sudo aptitude install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  libempathy30 
The following NEW packages will be installed:
  empathy empathy-common{a} geoclue{a} geoclue-hostip{a} 
  geoclue-localnet{a} geoclue-manual{a} geoclue-yahoo{a} 
  libchamplain-0.4-0{a} libchamplain-gtk-0.4-0{a} telepathy-gabble{a} 
  telepathy-salut{a} 
The following packages will be REMOVED:
  libempathy-common{a} python-papyon{u} python-telepathy{u} 
  telepathy-butterfly{u} 
0 packages upgraded, 11 newly installed, 4 to remove and 1 not upgraded.
Need to get 3,130kB/3,304kB of archives. After unpacking 5,779kB will be used.
The following packages have unmet dependencies:
  libempathy30: Depends: libempathy-common (= 2.28.1.1-1+ppa9.10+1) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
indicator-applet-session
indicator-session
libempathy30
ubuntu-desktop

Score is -394
The following NEW packages will be installed:
  empathy empathy-common{a} geoclue{a} geoclue-hostip{a} 
  geoclue-localnet{a} geoclue-manual{a} geoclue-yahoo{a} 
  libchamplain-0.4-0{a} libchamplain-gtk-0.4-0{a} telepathy-gabble{a} 
  telepathy-salut{a} 
The following packages will be REMOVED:
  indicator-applet-session{a} indicator-session{a} libempathy-common{a} 
  libempathy30{a} python-papyon{u} python-telepathy{u} 
  telepathy-butterfly{u} telepathy-idle{u} ubuntu-desktop{a} 
0 packages upgraded, 11 newly installed, 9 to remove and 1 not upgraded.
Need to get 3,130kB/3,304kB of archives. After unpacking 4,325kB will be used.
Do you want to continue? [Y/n/?]


so I did and the install happened with restored configuration;

Now the question is: aptitude vs apt-get,,,, I thought they were the same but obviously not.
What is the difference?
Thanks very much for your help

PS: part of the reason I balked at trying ANY of these was that one package to be removed was Ubuntu Desktop which was scary. Now harm done it seems

---

### Post by igknighted on 2009-12-02
> **David Oxland said:**
> PS: part of the reason I balked at trying ANY of these was that one package to be removed was Ubuntu Desktop which was scary. Now harm done it seems

The 'ubuntu-desktop' package is merely a metapackage... essentially a package that contains nothing, but depends on everything that would be in a default install.  Its only purpose is to make install easy (installing that one package gives you everything needed), it doesn't have any real purpose on its own.

---

### Post by David Oxland on 2009-12-03
I have reinstalled Empathy and that's OK except that MSN contacts are not available any more;
More puzzling is that what seems to have disappeared with Gnome Desktop is the Stop Menu consisting of options Hibernate, Suspend,  Shutdown, change users etc. 
I'm having a time getting that back.

---

### Post by Locke_99GS on 2009-12-03
```
sudo apt-get install indicator-applet-session indicator-session
```

You may have to add the applet into your gnome panel again.

---

### Post by David Oxland on 2009-12-04
sudo apt-get install indicator-applet-session indicator-session

This get me into an endless cycle where;
it requires libempathy30 which 
then cannot be installed because libempathy-common is missing
when I try to install libempathy-common it requires to remove the indicator-applet-session dependencies.
They seem to be in conflict
Also with the indicator-applet-session indicator-session installed the shutdown menu does not reappear but Empathy is uninstalled.
David

---

### Post by Locke_99GS on 2009-12-04
Thats odd. You could try using aptitude to install the same packages, but that may not go according to plan, either.

You could also try to install the ubuntu-desktop package, of which empathy and the indicator-applet should belong.

---

### Post by corncob on 2009-12-04
> **David Oxland said:**
> I have reinstalled Empathy and that's OK except that MSN contacts are not available any more;
More puzzling is that what seems to have disappeared with Gnome Desktop is the Stop Menu consisting of options Hibernate, Suspend,  Shutdown, change users etc. 
I'm having a time getting that back.

Try right-clicking the task bar, then select 'add to panel'.  Finally, select 'shut down...'

---

### Post by rmotters on 2009-12-04
I had a similar problem last night. I worked out the problem was down to me having emapthy installed from the telepthy ppa ([https://launchpad.net/~telepathy/+archive/ppa]("https://launchpad.net/~telepathy/+archive/ppa")) loaded.

This was updated to a new version of empathy, a couple of days ago. This  change of version caused the indicator-applet to have a problem, cuase it requires the library from v2.28 as a dependancy.

I spent the night installing and removeing empathy and trying to get my system back to normal. In the end I had lost the indicator applet, the fast-switch applet and empathy would not work at all. I chose to backup my home directory and re-install the OS.

---

### Post by David Oxland on 2009-12-04
Looks that is what I'm up against.
Here's the output of my latest attempt and you can see that there is a conflict.

david@david-desktop:~$ sudo aptitude install ubuntu-desktop package
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find package "package", and more than 40
packages contain "package" in their name.
Couldn't find package "package", and more than 40
packages contain "package" in their name.
The following packages are BROKEN:
  libempathy30 
The following NEW packages will be installed:
  empathy empathy-common{a} firefox-gnome-support ttf-indic-fonts-core 
  ttf-lao ttf-thai-tlwg ttf-unfonts-core ttf-wqy-zenhei ubuntu-desktop 
The following packages will be REMOVED:
  libempathy-common{a} libsofia-sip-ua-glib3{u} libsofia-sip-ua0{u} 
  python-papyon{u} python-telepathy{u} telepathy-butterfly{u} 
  telepathy-core{u} telepathy-haze{u} telepathy-sofiasip{u} 
0 packages upgraded, 9 newly installed, 9 to remove and 0 not upgraded.
Need to get 17.1MB/19.7MB of archives. After unpacking 34.6MB will be used.
The following packages have unmet dependencies:
  libempathy30: Depends: libempathy-common (= 2.28.1.1-1+ppa9.10+1) but it is not installable
The following actions will resolve these dependencies:

Keep the following packages at their current version:
empathy [Not Installed]
empathy-common [Not Installed]
libempathy-common [2.28.1.1-1+ppa9.10+1 (karmic, now)]

Leave the following dependencies unresolved:
ubuntu-desktop recommends empathy
Score is -1

Accept this solution? [Y/n/q/?] 

Thanks for all the suggestions. I guess this should be reported as a bug to Empathy or Ubuntu?

---

### Post by Mornedhel on 2009-12-04
As others have said, the problem stems from your using the Empathy PPA. When a PPA breaks dependencies and a dist-upgrade asks to remove packages that should obviously not be removed (e.g. Empathy, in your case), you should either not proceed with the upgrade, or temporarily remove the PPA from your sources.

Since you already went ahead with the upgrade, I recommend you comment the Empathy PPA in your sources.list, reinstall what is needed, then re-add the PPA but don't do dist-upgrades (only upgrades) until the devs solve their dependency problem and the PPA is back to a consistent state.

---

### Post by David Oxland on 2009-12-04
Thanks Mornedhel
 I understand now.
 Empathy seems to be restored to it's operating state and I've rigged up a Stop button so I'm happy.
I've not uncommented the PPA yet; tempted to leave it commented out for a month or two (as long as it's working), so I don't make a mistake and mess it up again.

---

