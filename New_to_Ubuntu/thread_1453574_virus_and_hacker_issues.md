---
title: "virus and hacker issues?"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by us11csalyer on 2010-04-13
Is there any anti virus software or firewall I should be running with Ubuntu?

I also backed up all my media to an external HDD. I did it in vista and formatted teh HDD to be FAt32. How do i access it in Ubuntu? Ubuntu says it is an unknown partition.

---

### Post by skyeric on 2010-04-13
give this a read --> [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by wojox on 2010-04-13
UFW - Uncomplicated Firewall is installed by default. You just need to turn it on: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by skyeric on 2010-04-13
this thread might have some interest to you as well

[http://ubuntuforums.org/showthread.php?t=1453548](http://ubuntuforums.org/showthread.php?t=1453548)

---

### Post by us11csalyer on 2010-04-13
Thanks for the links and replies.

---

### Post by skyeric on 2010-04-13
no worries i was thinking about the exact same thing when i first got ubuntu a few days ago

---

### Post by us11csalyer on 2010-04-13
> **skyeric said:**
> give this a read --> [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

So i went over this link. Windows Vista is stronger versus Ubuntu when it comes to preventing hacker? That is what I am getting but I must be missing something as linux is suppose to be only hack-able through root from my understanding. So isn't Ubuntu only hackable through root to?

---

### Post by skyeric on 2010-04-13
ubuntu can only have its system edited through root yes, whereas on windows altho a similar idea is in place due to so many of the programmes on windows requiring admin priviledges to run a potential hacker is likely to have access to everything straight up.

---

### Post by J V on 2010-04-13
> **Viruses**
Linux has almost no viruses, not that it's not a popular target, google, yahoo, and several other multi-million dollar targets run on linux.

If there ever was a serious Linux virus out there, to get it to actually work, you would need to:


[LIST]
[*]Log onto your email
[*]Open your email
[*] Download the attachment
[*]Find the attachment
[*]Right-click and go to properties
[*]Go to the permissions tab
[*]Check the box marked execution
[*]Run the application (It can now infect the files in the same directory as it is in)
[*]Input your password (It can now infect files over the entire system)
[/LIST]

 On windows, all you have to do is to log onto your email, windows does the rest automatically, which leaves you open to viruses.

If you are still worried you will actually do this whole list without wondering if its a virus, the Ubuntu wiki has a nice list of [currently known Linux viruses]("https://help.ubuntu.com/community/Linuxvirus"), and their trivial (sometimes whimsical) natures.

You might still however, want to scan for windows viruses, so you don't infect your friends/colleagues with files from your computer (Which is equally unlikely as you would have to deliberately copy it over to them)

For this purpose you should install "[ClamTK]("apt://clamtk")" (Click to install) which is an interface for "ClamAV", which can scan incoming and outgoing email, or in your case, specific files.

**Firewall**
Ubuntu comes with a fantastic firewall known as iptables. It is inactive by default, because no applications are "Listening" to the ports (Doorways) on your computer anyway, so there is no need for a firewall unless you install a server of sorts (And if you are installing servers you should know this already)

Iptables is actually very hard to configure, you need to edit configuration files, know the program, its just much more advanced. Luckily, there are tools that make this easy.

The most often advised firewall interface is "Firestarter", but nowadays its a bad idea to use it. It hasn't been developed for ages now, and because ufw (A command line configuration tool) is installed, Firestarter will conflict with already running services.

On top of that, while it runs, it runs as root, so if someone were to exploit a vulnerability in Firestarter, it would give them complete access to your system.

The current interface suggestion is "[gufw]("apt://gufw")" (Click to install) which, once again, is not a firewall, but a means to configure the default firewall.Copy&paste, I wish people would just google...

---

### Post by us11csalyer on 2010-04-13
Thanks.

---

### Post by Otis Spunkmiyer on 2010-04-13
Just turn the Firewall on.  (if it makes you feel comfortable)
And if you want you can get a free virus scanner from the built in Ubuntu software store.  (if it will make you feel better)

Other then that, continue your safe practices.  (no porn site's or opening dubious files, including unsolicited Emails)

And get set to enjoy a 'virus free environment'. (not to mention disk space saved from Windows, damn near every hour security updates)

---

### Post by us11csalyer on 2010-04-13
> **Otis Spunkmiyer said:**
> Just turn the Firewall on.  (if it makes you feel comfortable)
And if you want you can get a free virus scanner from the built in Ubuntu software store.  (if it will make you feel better)

Other then that, continue your safe practices.  (no porn site's or opening dubious files, including unsolicited Emails)

And get set to enjoy a 'virus free environment'. (not to mention disk space saved from Windows, damn near every hour security updates)

Disk space was never an issue for me. I had Windows 7 and long load time apps on a ssd and then had two internal 500GB drives, and a 1TB ext drive. My main reasons for moving to linux is virtually everything I need out of an OS can be done in linux without the hassle of window's demand for resources. Now to get Sims3, Stalker: call of pripyat, and a few other PC games to run in ubuntu :)

---

