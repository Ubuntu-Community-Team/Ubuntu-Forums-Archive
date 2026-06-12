---
title: "How do I update to the next version of Opera once I installed it from Opera's website"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by metalaxesucks on 2009-09-07
I want to install Opera to Kubuntu 9.04; the only thing that is stopping me is not knowing how to update to the next version of Opera once it comes out.
For example, Opera is now at 10.00, but once 10.01 comes out I'm going to want to update to it for security purposes. Do I just do an install over the last version in order to update it, or do I have to uninstall the older version first?
Thanks!

FYI: I don't see the latest version of Opera (or any version) in the repositories, otherwise I would install it from there.

---

### Post by Claus7 on 2009-09-07
Hello,

it would be pretty easy, really! When the new version is out, at the time you are browsing with opera, a message will appear telling you exactly that. The only thing you have to do, is to go to opera's web site, download the new version's deb file, and install it to your computer. Nothing more, nothing less. 

Regards!

---

### Post by Achilles124 on 2009-09-07
nope, it isn't in the repositories. You can download the deb-file. You can install it then on your system. 

When opera is upgraded to 10.1 or something like that, then remove opera from your system, then download the deb-file from the opera-site and install it on your system.

That is the way it works.

---

### Post by metalaxesucks on 2009-09-07
Ok, I've got two answers, one says I just install the next version & nothing more, the other one says I have to uninstall the previous version before I install the next version. Which one is it? And if I have to uninstall the previous version before I install the next version, how do I uninstall the previous version (what's the command)?

---

### Post by Perfect Storm on 2009-09-07
Check this; [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)
You'll get the latest through your package manager + notify when there's a newer version.

---

### Post by Cheezespread on 2009-09-07
To Remove Opera

How have you installed Opera ?. From Synaptic or using Apt in terminal?

1.In Synaptic you can search for Opera and it would show the installed software . You can mark it for removal and apply.

2. In terminal

sudo apt-get remove --purge <packagename> ( of Opera installed)

No idea about first question though.

---

### Post by mbzn on 2009-09-07
Download the new version from the opera website, (.deb). and open it. No need to uninstall the oter one.

---

### Post by longtom on 2009-09-07
> **Artificial Intelligence said:**
> Check this; [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)
You'll get the latest through your package manager + notify when there's a newer version.

That is the best way to do it.  I used Opera 10 Beta and once 10 came out it downloaded and installed like any other update - Bob's your uncle...

---

### Post by Claus7 on 2009-09-07
Hello,

> **metalaxesucks said:**
> Ok, I've got two answers, one says I just install the next version & nothing more, the other one says I have to uninstall the previous version before I install the next version. Which one is it? And if I have to uninstall the previous version before I install the next version, how do I uninstall the previous version (what's the command)?

In the older versions this was what it was required for you to do so. Since you are referring to version 10 onwards (and even some versions before) you to not need to bother about uninstallment. 

> **longtom said:**
> That is the best way to do it.  I used Opera 10 Beta and once 10 came out it downloaded and installed like any other update - Bob's your uncle...

I do not think that you have to bother about that. In gnome for me, I didn't have to bother at all. I'm running opera 10 since its alpha release and when beta was out first and then the final release I was informed in both situations about it. And I did the installation of the newest versions as I have mentioned.

Regards!

---

### Post by 3rdalbum on 2009-09-07
When you install the .deb package of Opera, it automatically adds the Opera repository for Ubuntu. So when a new stable release comes out, you will recieve it in your system's Update Manager.

---

