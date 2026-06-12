---
title: "How do I disable evolution services from loading?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by VitaminBB on 2009-04-30
I hate evolution ...

Let me be more specific, I hate that evolution has services that startup and I never ever use them.

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/evshot.jpg[/IMG]

These two services are always loaded and when I try to delete stupid evolution my computer wants to remove a ton of other things that I dont want to lose.

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/pic2.jpg[/IMG]

So evolution sucks badly and I hate it but I dont seem to have a choice but to let it exist on my computer but how do I deactivate these services so that nothing pertaining to evolution loads and wastes my memory?

Thanks ahead of time for the help ...

---

### Post by gunksta on 2009-04-30
Have you really stopped to consider how angry you appear to be about this? I'm not sure minor packaging bugs can ever really rise to the level of a "WTF" . . . some day something really screwy is going to happen with your computer and you'll have run clean out of novel exclamatory remarks.   :popcorn:

More to the point, what version of Ubuntu are you using. I do recall this was an issue on older versions of Ubuntu. New(ish) versions of ubuntu-desktop are not dependent on evolution or lib-evolution. You're right, it's an unnecessary hard dependency.

I suggest upgrading to a newer version of Ubuntu, where this packaging dependency bug has been repaired. I have a funny feeling you are running the current LTS, which I think does still include this but. Jaunty does not have this issue and I'm pretty sure Intrepid was clean as well.

If upgrading is not an option (which does happen for people), go to System, Preferences, Startup Applications. Here you can adjust what apps start automatically. Disable evolution alarm notifier and evolution won't auto start when you start Gnome. However, if you click on the clock applet in the panel, it will start up the evolution stuff to look for meetings and to do list stuff. Evolution is the default mail client of the Gnome desktop. Sorry.

However, if you upgrade and remove all evolution related packages, this little problem goes away entirely.

Or, you could just switch to a different desktop, like XFCE (Xubuntu) as this will not require evolution to be installed and it will not try to automatically start it up.

I hope one or more of these options helps.

---

### Post by gunksta on 2009-04-30
BTW. On most computers, 4 MB of RAM is . . . . irrelevant. I can think of lots of things running on most computers that waste more than 4 MB of RAM. For example, let Fire Fox run for a few days without shutting it down and you will waste way more than 4 MB of RAM!

---

### Post by Duskao on 2009-04-30
Just a heads up, Xfce uses thunderbird as the default email client.

---

### Post by VitaminBB on 2009-04-30
> **gunksta said:**
> Have you really stopped to consider how angry you appear to be about this? I'm not sure minor packaging bugs can ever really rise to the level of a "WTF" . . . some day something really screwy is going to happen with your computer and you'll have run clean out of novel exclamatory remarks.   :popcorn:

Been there, done that, old post

> More to the point, what version of Ubuntu are you using. I do recall this was an issue on older versions of Ubuntu. New(ish) versions of ubuntu-desktop are not dependent on evolution or lib-evolution. You're right, it's an unnecessary hard dependency.

Latest 9.04, the one screenshot with the WTF was from an older post of mine but the issue is still the same.

> If upgrading is not an option (which does happen for people), go to System, Preferences, Startup Applications. Here you can adjust what apps start automatically. Disable evolution alarm notifier and evolution won't auto start when you start Gnome. However, if you click on the clock applet in the panel, it will start up the evolution stuff to look for meetings and to do list stuff. Evolution is the default mail client of the Gnome desktop. Sorry.

Yup, went there, nothing mentioning evolution is listed, unless evolution is "tracker", thats the only entry that im not sure of and I suspect thats a searching service of some sort.

Thanks for the help but the version is the latest and evolution isent even mentioned under "startup applications" ...

Any other idea?

---

### Post by BGFG on 2009-04-30
try boot up manager
```

sudo aptitude install bum

```

---

### Post by gunksta on 2009-05-01
Hmmm. I can not reproduce what you are saying. If I try to remove evolution (via Synaptic) it offers to also remove:

[LIST]
[*]evolution-indicator
[*]evolution-plugins
[*]gnome-do-plugins
[*]libevolution-cil
[/LIST]
It does not try to remove ubuntu-desktop, Tracker, etc. And yes, Tracker is a service that indexes your files.

Don't waste your time with bum, evolution (and all it's related services) are user-land applications and are not started during the boot process. They are only started after you log in and bum doesn't work with those type of services. And, Thunderbird is not the default mail client for XFCE. XFCE does not have a default mail client. Thunderbird is the default mail client of Xubuntu. You can, if you want, install the XFCE desktop separately, without installing the rest of the Xubuntu dependencies. In my personal opinion, this works better and installs less cruft for circumstances where I want XFCE installed on a computer where I already have ubuntu-desktop installed.

Try this at the command-line:
```
sudo apt-get remove --purge evolution
```The computer will ask for your passoword. Before it actually does anything, it will tell you what it is going to do, since it will remove a few dependencies. Look over the list of things it offers to remove. If you're running the latest Ubuntu, it won't try to remove ubuntu-desktop or other importanr apps.

---

### Post by kansasnoob on 2009-05-01
You can remove evolution just don't remove the evolution-data-server-common package:

[ATTACH]111977[/ATTACH]

Or the language packs!

---

### Post by VitaminBB on 2009-05-02
> **kansasnoob said:**
> You can remove evolution just don't remove the evolution-data-server-common package:

[ATTACH]111977[/ATTACH]

Or the language packs!

What does the evolution-data-server do then?

---

### Post by VitaminBB on 2009-05-02
> **gunksta said:**
> Hmmm. I can not reproduce what you are saying. If I try to remove evolution (via Synaptic) it offers to also remove:

[LIST]
[*]evolution-indicator
[*]evolution-plugins
[*]gnome-do-plugins
[*]libevolution-cil
[/LIST]
It does not try to remove ubuntu-desktop, Tracker, etc. And yes, Tracker is a service that indexes your files.

Don't waste your time with bum, evolution (and all it's related services) are user-land applications and are not started during the boot process. They are only started after you log in and bum doesn't work with those type of services. And, Thunderbird is not the default mail client for XFCE. XFCE does not have a default mail client. Thunderbird is the default mail client of Xubuntu. You can, if you want, install the XFCE desktop separately, without installing the rest of the Xubuntu dependencies. In my personal opinion, this works better and installs less cruft for circumstances where I want XFCE installed on a computer where I already have ubuntu-desktop installed.

Try this at the command-line:
```
sudo apt-get remove --purge evolution
```The computer will ask for your passoword. Before it actually does anything, it will tell you what it is going to do, since it will remove a few dependencies. Look over the list of things it offers to remove. If you're running the latest Ubuntu, it won't try to remove ubuntu-desktop or other importanr apps.

Thanks, lots of good info here.

I did install bum but noticed there was no option to deactivate evolution ...

---

### Post by gunksta on 2009-05-04
> **VitaminBB said:**
> What does the evolution-data-server do then?

Evolution / Evolution data server are becoming increasingly important parts of the Gnome desktop. For example, empathy (a replacement for Pidgin) will use the evolution data server to sync your evolution contacts with your IM contacts. The idea is to integrate these services because they are so similar. The gnome-panel uses it to list tasks and appointments when you click on the clock.

There are lots of people out there that dislike/hate evolution and I hope the gnome-devs over at Novell give it a face lift. Many people to hate to hear this, but Evolution has a lot going for it, but the interface looks like a dated version of a MS product which doesn't do it any favors. I would like to see it ported to Webkit, include a tabbed interface and generally make the UI more gnome-like.

But the underlying technology, like the data server, are actually really neat systems. Ironically, these are the systems you are trying to turn off. I still think the easiest way to do this is through the Startup Applications dialog in the Settings Menu but I actually use Evolution, so I don't tend to do that.

---

### Post by callahanp on 2009-06-06
I'm trying to get rid of evolution mail.  
It's the default e-mail in firefox.  I want to use my own.

Is there a way to get rid of just evolution mail?

removing evolution seems to want to do too much.

So what exactly is evolution?

from projects.gnome.org/evolution:  "Evolution provides integrated mail, addressbook and calendaring functionality to users of the GNOME desktop. "

Note that gnome-desktop would be removed by the following command.

why is that?

-Pat
$ sudo apt-get remove --purge evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu-xdg desktop-base planner gthumb python-renderpm
  gstreamer0.10-plugins-ugly libdiscid0 cheese libots0 gnome-network-admin
  hardinfo gthumb-data gparted gnome-office libaiksaurusgtk-1.2-0c2a
  abiword-common abiword abiword-plugin-mathview latex-xft-fonts
  libaiksaurus-1.2-0c2a python-lxml swfdec-gnome python-reportlab-accel
  libsoup2.2-8 dasher libloudmouth1-0 link-grammar-dictionaries-en p7zip
  gnome-themes-extras gdm-themes abiword-help python-numpy arj
  gstreamer0.10-ffmpeg gnome-volume-manager libaiksaurus-1.2-data
  python-4suite-doc gnome-backgrounds dasher-data xfce4-icon-theme gok
  libgdome2-0 abiword-plugin-grammar libwmf-bin libswfdec-0.8-0
  python-uniconvertor imagemagick-doc liferea libgdome2-cpp-smart0c2a
  libsidplay1 swfdec-mozilla gnome-core gtk2-engines-xfce python-4suite-xml
  imagemagick liblink-grammar4 libgtkmathview0c2a gnome-accessibility inkscape
  python-reportlab serpentine sound-juicer libmusicbrainz3-6 gnome-vfs-obexftp
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  evolution* evolution-exchange* evolution-indicator* evolution-plugins*
  gnome-desktop-environment*
0 upgraded, 0 newly installed, 5 to remove and 6 not upgraded.
After this operation, 10.9MB disk space will be freed.
Do you want to continue [Y/n]? ^  

UM.. No not exactly....

---

### Post by philinux on 2009-06-06
Try running this.

```
sudo apt-get autoremove
```

> From man apt-get:-
autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.
The English is off but you get the drift.

---

### Post by linux6994 on 2009-06-06
Under Edit > Preferences > Advanced change the mailto: option?

---

### Post by Johan-Steyn on 2009-06-06
Hi, 

I tried uninstalling Evolution before and it also removed the gnome-desktop.

So, just to be sure, does the purge code: "**sudo apt-get remove --purge evolution**" also affect the gnome-desktop?

If not, what about ekiga?

Regards,

JS

---

### Post by pauna on 2009-06-06
> **gunksta said:**
> Evolution / Evolution data server are becoming increasingly important parts of the Gnome desktop. For example, empathy (a replacement for Pidgin) will use the evolution data server to sync your evolution contacts with your IM contacts. The idea is to integrate these services because they are so similar.

While this Ubuntu/Gnome INTERNAL integration sounds great, the current e-mail and calendaring usage patterns are moving forward to require heavy EXTERNAL integration with internet based services.

Evolution is a good IMAP client, but its **two-way** sync capabilities with for example Google calendar and network based task managers (RememberTheMilk etc) are very patchy or even non-existent. One-way sync sort of works, but that's practically useless. Evolution reflects the Old "single backend server storage" way of doing email and personal information management. It simply isn't true anymore.

So, I'm not using Evolution anymore. Sometime around 2001, when Evolution was still 1.0 or so, I actually used Evolution a lot and at that time it really was great.

---

### Post by Darwood on 2012-11-01
> **gunksta said:**
> I still think the easiest way to do this is through the Startup Applications dialog in the Settings Menu but I actually use Evolution, so I don't tend to do that.
Agreed. Don't forget some Evolution components are hidden so as per [http://ubuntuforums.org/showpost.php?p=11960777&postcount=2]("http://ubuntuforums.org/showthread.php?t=1985299") you will need to use the following command in a terminal to show all startup items.

     ```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

[]("http://ubuntuforums.org/showthread.php?t=1985299")

---

### Post by howefield on 2012-11-01
Old thread back to sleep.

---

