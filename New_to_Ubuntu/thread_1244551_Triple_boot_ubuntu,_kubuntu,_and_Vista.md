---
title: "Triple boot ubuntu, kubuntu, and Vista?"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by designateduser on 2009-08-19
So I was over at my friends house and saw he was using Kubuntu, and honestly I loved it. However I still do like Gnome and would like to keep it so if I get stuck messing around with Kubuntu, or there is a program I need that is not for 64-bit (my current 9.04 ubuntu is 32-bit) I could boot into Ubuntu. How could I set my computer up so that I have my current partition (vista and ubuntu 9.04) but add Kunbuntu 9.04 to the list? I want to become windows-free but am afraid to let go, so if getting rid of Vista is an option, but I would prefer to keep it and triple boot. Any help is much appreciated.

---

### Post by theozzlives on 2009-08-19
> **designateduser said:**
> So I was over at my friends house and saw he was using Kubuntu, and honestly I loved it. However I still do like Gnome and would like to keep it so if I get stuck messing around with Kubuntu, or there is a program I need that is not for 64-bit (my current 9.04 ubuntu is 32-bit) I could boot into Ubuntu. How could I set my computer up so that I have my current partition (vista and ubuntu 9.04) but add Kunbuntu 9.04 to the list? I want to become windows-free but am afraid to let go, so if getting rid of Vista is an option, but I would prefer to keep it and triple boot. Any help is much appreciated.

Just do:
```
sudo apt-get install kubuntu-desktop
```
You'll get to switch between the two at the login screen. Kubuntu is just Ubuntu with a couple different apps and KDE.

---

### Post by SuperSonic4 on 2009-08-19
> **theozzlives said:**
> Just do:
```
sudo apt-get install kubuntu-desktop
```
You'll get to switch between the two at the login screen. Kubuntu is just Ubuntu with a couple different apps and KDE.

You may also install kubuntu to a partition like you did with ubuntu - this option has less clutter but the option I quoted allows easier switching

---

### Post by itdoesnot on 2009-08-19
wouldn't it still show all the kde applications even when using ubuntu (gnome)
i'm pretty sure it does (i installed xfce on a computer using gnome)
correct me if i'm wrong but gnome is built off gtk and kde off qt
either way, wouldn't his comp work slower if he's launching both gnome and kde apps
at the same time, since he's loading gtk and qt ?

---

### Post by dawynn on 2009-08-19
Unless there is a specific reason that you really want to eat up another big chunk of resources installing another system, just keep it at a double boot.  Linux and Windows.

Ubuntu basically gives you a Gnome front-end, Kubuntu gives a KDE frontend, but much of the background stuff (including all of the kernel, and xorg) are the same.  

I'm not sure how compatable the two are, so you may run into instances of competing packages, but I would simply go to synaptic and add the kubuntu-desktop to your current system setup.

That way from kdm or gdm or whatever login tool you're using (kubuntu-desktop will install kdm, ubuntu-desktop will install kdm, and the system will make you choose which will actually be used), you have the "option" of choosing a "session" "action" (look for key words like this on your login screen -- different screens call it different things).  From the login screen you then choose what GUI you will use.

If the Kubuntu / Ubuntu-desktop fight, you may also want to look for the kde / gnome metapackages.  These provide a slightly different selection of packages, but still provide the basic GUI's for you to choose from your login screen.

---

### Post by SuperSonic4 on 2009-08-19
> **itdoesnot said:**
> wouldn't it still show all the kde applications even when using ubuntu (gnome)
i'm pretty sure it does (i installed xfce on a computer using gnome)
correct me if i'm wrong but gnome is built off gtk and kde off qt
either way, wouldn't his comp work slower if he's launching both gnome and kde apps
at the same time, since he's loading gtk and qt ?

Yes it would, that's what I meant by more clutter.

I think it's marginally slower but negligibly so

---

### Post by dawynn on 2009-08-19
Depends on his PC.  I can run gtk and kde applications from my xfce mint setup on my Athlon classic 1.4 Ghz pc with not much difficulty.  Anything newer should have no problems with using both sets of applications -- even side by side.

Gnome and KDE used to fight a lot, but that was years ago.  Anymore, both fairly well support running applications from the other platform.  And frankly, you'll probably find yourself preferring applications from both camps.  I can't live without synaptic (gtk), but need my soundkonverter, and k3b (kde).  To each his own -- and Linux happily supports both no matter which platform you use.

---

### Post by Penguin Guy on 2009-08-19
> sudo apt-get install kubuntu-desktop
**Not** a good idea, I tried this and it causes all sorts of annoying problems. If you're going to have both KDE and GNOME, put them on separate installs.

As for the actual installation, it is pretty much the same as installing Ubuntu the first time round. If you can't do what you want to your partitions through the installer, you should check out GParted on the LiveCD: [COLOR="Green"]System -> Administration -> Partition Editor[/COLOR].

---

### Post by running_rabbit07 on 2009-08-19
If you want to give Kubuntu a try on your system without making all the changes you should consider running Kubuntu in Virtual Box. It is easy to set up and you can then have Kubuntu and Ubuntu running at the same time. I have Karmic running in Virtual Box while running Ubuntu Hardy as my primary system.

---

### Post by RyanVanDiemen on 2009-08-19
Well, I used to have both kde and gnome and for certain period even xfce. System was slower on OpenSUSE but on Ubuntu I didnt really feel the difference (application start is of course slower if you run it in non-native DE). I'd say just adding kubuntu-desktop is the best way for you if you really wanna just have the choice of both DEs.

---

