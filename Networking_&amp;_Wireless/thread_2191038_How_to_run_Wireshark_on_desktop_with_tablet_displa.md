---
title: "How to run Wireshark on desktop with tablet display manager (Ubuntu 12.04, x64)?"
date: 2013-11-30
forum: Networking &amp; Wireless
---

### Post by noloader on 2013-11-30
Hi All,

I'm running Ubuntu 12.04 (x64). I installed Wireshark with apt-get.

When I go to Ubuntu Button -> Search "Wireshark" -> Wireshark, the wireshark program launches. Unfortunately there's no interfaces to sniff. That's because Wireshark needs to be run as root.

In the past, I would just go to the menu item and add 'gksudo' to the launch command. I can't figure out how to do it with Ubuntu's nifty tablet display manager (which I believe is called Unity, adds no value to a desktop computer, and slows down workflows because of all the extra taps/clicks required).

Additionally, when I find Wireshark under recently used applications, I cannot right click it to bring up properties. Right clicking just launches the application again.

How do I launch Wireshark as root using Ubuntu's nifty tablet display manager?

Thanks in advance,

Jeff

---

### Post by The Cog on 2013-11-30
How about pressing Alt-F2 and typing **gksudo wireshark** into the popup box.

It sounds as though you don't like Unity. You may find it worthwhile to try Xubuntu, Lubuntu or Kubuntu. They are all quite different, to Unity and to each other.

---

### Post by noloader on 2013-11-30
Thanks Cog.

> How about pressing Alt-F2 and typing **gksudo wireshark** into the popup box.
Well, that's not really efficient. Ideally, I should be able to fix the problem once instead of working around it countless times.

> It sounds as though you don't like Unity.
Yeah, I'm not a big fan of the tablet display managers on the desktop. I can't stand the latest from Ubuntu, Fedora or Windows. I think they were all smoking crack or on some other drug when they decided it was a good idea.

Worse, you can't remove Unity and install a normal desktop manager for the desktop computer (been there, done that, and broke everything).

> You may find it worthwhile to  try Xubuntu, Lubuntu or Kubuntu.
> They are all quite different, to Unity  and to each other.
In this case, I need to use the same platform as the person having the trouble.

Personally, I use Mint Linux. Its got a normal desktop manager and its in my backyard (University of Maryland).

Jeff

---

### Post by pbrane on 2013-11-30
do this:
in a terminal run,
[FONT=courier new]sudo dpkg-reconfigure wireshark-common[/FONT]

choose yes to allow non superusers to capture packets

Then in users and groups (or whatever the unity equivalent is) add yourself to the wireshark group.

Now you will be able to capture packets, i.e., the interfaces will show up in wireshark. It's basically the same procedure for most (all?) debian based distros regardless of the desktop.

---

### Post by noloader on 2013-11-30
> in a terminal run,
[FONT=courier new]> sudo dpkg-reconfigure wireshark-common
Perfect, thanks.[/FONT]

---

### Post by The Cog on 2013-12-01
Thanks, pbrane. I know there was some command-line stuff to allow use of wireshark without sudo, but couldn't remember what it was. 
I don't understand why the wireshark group isn't created (without any users) as wireshark is installed. It seems an obvious thing to do, to me.

---

