---
title: "How do I install for security? iptables etc."
date: 2010-01-04
forum: New to Ubuntu
---

### Post by greenleaves123 on 2010-01-04
I want to install iptables as a firewall. I'm a little paranoid about security, especially since I surf some questionable sites sometimes. Do I use FireStarter? I tried to find it in Add/remove programs, but I couldn't find it. How do I get it? Do I need it?

Also I just read about rootkit and cracking, how do I detect or prevent that?

---

### Post by bobin on 2010-01-04
Synaptic package manager > Firestarter


Linux generally is generally rather safe as it is deaf to external connections. But then again prevention is better than cure.

---

### Post by ramjet_1953 on 2010-01-04
By default, iptables is installed and all ports are closed, so your system is secure.

If you need to do any port forwarding, you can download one of the GUI's for iptables.
 
As far as rootkits are concerned, you can install either [COLOR="Red"]rkhunter[/COLOR] or [COLOR="Red"]chkrootkit[/COLOR] using Synaptic Package Manager.

Regards,
Roger:)

---

### Post by greenleaves123 on 2010-01-04
Thanks

I just installed Firestarter, but it says there is no Internet connection and the firewall won't start. What do I need to do?

---

### Post by greenleaves123 on 2010-01-04
> **greenleaves123 said:**
> Thanks

I just installed Firestarter, but it says there is no Internet connection and the firewall won't start. What do I need to do?

Oh nevermind, I figured it out, I selected the wrong connection.

---

### Post by greenleaves123 on 2010-01-04
> **greenleaves123 said:**
> Oh nevermind, I figured it out, I selected the wrong connection.

Do I need to do anything about rkhunter? I can't find it. I installed it but I don't know where it is.

---

### Post by s.fox on 2010-01-05
Hello,

[This ]("https://help.ubuntu.com/community/InstallingSecurityTools")community wiki page lists some security tools that are in the repositories.  

-Silver Fox

---

### Post by Methuselah on 2010-01-05
You might also want to check this thread out as the poster had similar questions and got answers to many.
[http://ubuntuforums.org/showthread.php?t=1371178](http://ubuntuforums.org/showthread.php?t=1371178)

---

### Post by 3rdalbum on 2010-01-05
> **greenleaves123 said:**
> I want to install iptables as a firewall. I'm a little paranoid about security, especially since I surf some questionable sites sometimes.

You seem to be a bit hazy on what a firewall is.

A firewall stops other computers from being able to contact programs running on your computer that are listening for incoming connections. By default, unless you run Transmission (bittorrent client), or you enable Remote Desktop, or you install some other server programs, there is nothing on your computer that listens for incoming connections.

So a firewall will be of no use unless you install some server services - and even then, you will usually WANT other computers to be able to contact those services, which a firewall would prevent.

Most people have a firewall in their modem/router anyway, that will protect their whole network. If you have one of these modems or routers, then a personal firewall will be totally useless.

Questionable websites will attempt to use Javascript to confuse your web browser and trick it into running commands. This Javascript comes down through the connection that YOU establish. Plus, there are no reported Firefox scripting exploits in the wild. Plus, scripting exploits will probably only work on one operating system at a time, and it's usually not Linux.

In short, a firewall will not protect you any more than the default installation of Ubuntu.

> Do I use FireStarter? I tried to find it in Add/remove programs, but I couldn't find it. How do I get it? Do I need it?

Don't use Firestarter - it's basically unmaintained, not user friendly, and contains several known bugs that will never be fixed. If you need a personal firewall, use GUFW to set it up.

> Also I just read about rootkit and cracking, how do I detect or prevent that?

Rootkits enter through either known security flaws in server software, or through a poorly-secured installation of server software. In short, unless you're running an FTP server/web server/Samba server/SSH you're not going to get a rootkit. If you want to run those server programs, then read up online about how to properly lock them down, and make sure they stay up-to-date with your Update Manager.

---

