---
title: "Change Network Location using Command Line"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by microserf on 2006-08-23
Hi

Is it possible to change my network location using the command line instead of using the GUI? (E.g. when X11 breaks after a broken X11 patch :-)

Thanks in advance

---

### Post by Original Brownster on 2006-08-23
Hi,
Do you mean change your IP using the command line, or something else?
You can edit the file /etc/network/interfaces if that is what you mean.


> **microserf said:**
> Hi

Is it possible to change my network location using the command line instead of using the GUI? (E.g. when X11 breaks after a broken X11 patch :-)

Thanks in advance

Regards

---

### Post by mpvano on 2006-08-23
I'm not sure what you mean by "change my network location"?

It sounds like you are actually asking how to do software updates and package maintenance from the command line. If that's what you want to know here are some pointers to the information you'll need:

The most common command line program for installing and removing packages is called apt-get. It's fairly easy to use, but complicated to understand. It is a front end for another program that actually does the work called dpkg. You can find more out about them by using the man command from a terminal window. Type

man apt-get

and 

man dpkg

to learn more.

You must have root privileges to instlal packages. Here's how you can update the package database (check for updates).

sudo apt-get update

then enter your password when prompted.

when that command finishes checking all the "repositories" all over the world for updates, you can use another command to install all pending upgrades. You are given a chance to reject the updates after they are listed by a prompt.

sudo apt-get upgrade

For example, the bad X11 update was replaced by another one that fixed the problems it created about 12 hours later. If you are still having trouble, you can fix your problem by running these two commands 

sudo apt-get update
sudo apg-get upgrade

I like putting them all on one line so they both run without waiting for me to type the second one. In Unix you can put a second command on the same line by separating it with a semicolon like this:

sudo apt-get update ; sudo apt-get upgrade

hope this gets you started, but you need to know that apt-get (and the rest of the "apt" suite of tools) are quite complicated to understand.

Here's another useful command:

apt-cache search xxxx

will search for packages containing xxxx (or whatever) in their names.

hope this gets you started....

Mario

---

### Post by microserf on 2006-08-24
Thanks for the replies, but that's not quite what I meant.

Ubuntu's UI has a 'network locations manager' (really only intended for laptops) which lets you define different locations that the machine will be used in and associated network settings for those locations (you can find this via System -> Administration -> Networking from an account with the correct priviledges, such as the first user account). When you move the laptop from the office to home, you simply choose the 'Home' location to get the network settings for the home network environment.

I was wondering if it's possible to do this via the command line (e.g. by a command that takes the name of the location as an argument).

---

