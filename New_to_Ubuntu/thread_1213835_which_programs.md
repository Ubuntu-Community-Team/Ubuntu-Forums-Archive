---
title: "which programs?"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by minimad127 on 2009-07-15
[FONT=Times New Roman][SIZE=3]Ok I hope this is simple enough to answer but I will start with my situation[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I have been given a very old Dell x300 from a colleague of mine because windows was dead and wouldn’t even get passed the first boot screen so she has brought a new one and told me if I can fix it I can have it.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Anyways long story short formatted and installed Ubuntu everything boots up properly and everything seems to work that I want on it (wireless network/internet access etc) as it is going to be a ‘netbook’ as it is only a 1.4ghz cpu with 512mb ram and a 12” screen and will mainly be used by my wife and step daughter (12 years old) to go on utube, bebo, facebook and msn, and then watching movies and listening to music etc so that the main computer is free for gaming etc [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Now my question is (due to me having never used linux before) what pieces of software would you think I might need to install on it before I let them loose, being from a windows back ground and me having a couple of windows based computers on the network I am always concerned by security, however the way I read most of the security posts it seems the main concern is root kits is this correct or am I just reading the wrong posts? (by the way I have a hardware firewall on my router)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Any other potential software that might be useful for these sort of basic uses[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Cheers for any help and advice[/SIZE][/FONT]

[FONT=Times New Roman]
[/FONT]

---

### Post by binbash on 2009-07-15
You do not need to do anything.But instead of ubuntu install xubuntu (not a lot difference tho) because of 512 ram.

---

### Post by Tibuda on 2009-07-15
Read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by alexlafreniere on 2009-07-15
Every derivative of Ubuntu comes stuffed full of every program you could need for a general use computer like that. You don't really need to install anything unless you have some specific need for something. Ubuntu is also very secure, no unnecessary ports opened by default, immune to viruses, etc. Your fear of rootkits on Linux is unfounded, there are none in the wild. You're probably reading articles about researchers writing malicious programs in the lab, but it's nothing you have to worry about on a day to day basis. Good luck with your foray into Ubuntu, trust me it's addictive!

EDIT: Looking back, I shouldn't say Ubuntu is immune to viruses, you just won't find any out on the Internet. Hope that cleared things up.

---

### Post by scorp123 on 2009-07-15
> **minimad127 said:**
>  however the way I read most of the security posts it seems the main concern is root kits As a desktop user you're highly unlikely to ever run into these during your entire life time.

Root kits are only really relevant for server admins who run servers 24x7  which are non-stop connected to the Internet, and where 100's or 1000's of people login and logout day and night. Yes, there you might find a few "black sheep" who try funky stuff with root kits, backdoors, exploits, and what not.

But as I said: As a desktop user you're highly unlikely to ever run across one of those things.

---

### Post by DGortze380 on 2009-07-15
Start with the Ubuntu-Restricted-Extras package, and flash. The first is available through synaptic package manager or open a terminal and type: sudo apt-get install ubuntu-restricted-extras

Flash is a download: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Then do some web browsing and make sure you don't run across any missing plugins.

That's all I can think of.

---

### Post by DGortze380 on 2009-07-15
> **alexlafreniere said:**
> Your fear of rootkits on Linux is unfounded, there are none in the wild.

mmmm ... rootkits exist ...

You likely don't have to worry about them on a desktop machine behind a router with PAT ... but they certainly 'exist in the wild'

---

### Post by minimad127 on 2009-07-15
cheers all for the very quick responses 
 
will get flash for sure and is the 'restricted extras' a package of programs or is it codecs etc?

---

### Post by 3rdalbum on 2009-07-15
> **minimad127 said:**
> cheers all for the very quick responses 
 
will get flash for sure and is the 'restricted extras' a package of programs or is it codecs etc?

"ubuntu-restricted-extras" is what they call a *metapackage* - when you install it, it just installs a bunch of other packages. These include Flash Player, Java, multimedia codecs and some other useful stuff. I don't think any of it is actual end-user programs, just infrastructure.

Forget this discussion on viruses and rootkits :-)  If you have a hardware firewall on your network, then you're perfectly safe from rootkits. They are rare anyway and are usually contracted by having SSH installed, with a weak password, accessible from the Internet, and "allow root logins" enabled. Ubuntu doesn't have SSH server installed by default.

I can't think of anything else that you might want on Ubuntu - you could go to [www.medibuntu.org](www.medibuntu.org) and follow the howto there, which gives you easy access to DVD playback software and Google Earth.

---

### Post by Sef on 2009-07-15
> You do not need to do anything.But instead of ubuntu install xubuntu (not a lot difference tho) because of 512 ram.
Ubuntu runs just fine with 512 mb ram.   I have a computer with that amount of ram, and it works with no problem or slowness.

---

### Post by tarps87 on 2009-07-15
If you are looking at setting it up for someone else you may want to consider using some of sudo's functionality.

In short:
Sudo gives that user root/admin rights to run any programs assigned to that user in the sudo file, it the default install of Ubuntu this is all programs for admin user i.e. you

This link contains more detailed info:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)


> **Sef said:**
> Ubuntu runs just fine with 512 mb ram.   I have a computer with that amount of ram, and it works with no problem or slowness.

+1

---

