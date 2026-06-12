---
title: "initial security setup/concerns..."
date: 2011-03-29
forum: New to Ubuntu
---

### Post by RotorRick on 2011-03-29
n00b here again...ok, I understand that virus are not a concern in Linux at this time, but I'm wondering if I have to configure anything on my brand new Ubuntu install, for security reasons. Any ports open that need to be closed or anything? Firewall to be engaged?

I've got it using one password, is that generally sufficient for home/personal use? 

Thanks!!!

---

### Post by Dutch70 on 2011-03-29
Yes, you need a good strong password because that's how you get root access. No one can do anything to your computer without root access.

A firewall is a good idea if you're not behind a router.

---

### Post by Rubi1200 on 2011-03-29
> **Dutch70 said:**
> Yes, you need a good strong password because that's how you get root access. No one can do anything to your computer without root access.

A firewall is a good idea if you're not behind a router.
+1

Strong passwords, only install software from the official repositories, and keep the system updated. Do this and you should never have to worry.

For more on security, see here:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Lateralis on 2011-03-29
Ubuntu comes with the "uncomplicated firewall" but I believe it is switched off by default.  To see some help for the program you can search the internet or fire up a terminal (Applications -> Accessories -> Terminal) and type:

```

ufw --help

```

for a list of useful commands.  For more in depth information you can check out the firewall's manual page:

```

man ufw

```

The main commands you will probably want to use are

```

sudo ufw enable
sudo ufw disable
sudo ufw status

```

to enable, disable and check the status of ufw respectively.

---

### Post by Paddy Landau on 2011-03-29
> **Dutch70 said:**
> No one can do anything to your computer without root access.
Unless they have physical access to your computer, then they can get root access by rebooting into recovery mode. If data security is a requirement, ensure you encrypt your home folder, and no one can access the data without your password.

> **Lateralis said:**
> Ubuntu comes with the "uncomplicated firewall" but I believe it is switched off by default.
That's not quite correct. Linux comes with a firewall, which is always on. Any firewall program merely accesses the settings; uncomplicated firewall is merely one of the ways to change the settings.

The default settings are pretty open. However, the way Linux works, I am not aware of any need to change the firewall settings for normal desktop use.

---

### Post by sammiev on 2011-03-29
You can also use [GRC]("http://www.grc.com/intro.htm") to test if you have any open ports. GL :)

---

### Post by Paddy Landau on 2011-03-29
> **sammiev said:**
> You can also use [GRC]("http://www.grc.com/intro.htm") to test if you have any open ports. GL :)
Yes, but be aware that if you're behind a router, it tests your router and not you.

---

### Post by mcduck on 2011-03-29
> **Paddy Landau said:**
> 

That's not quite correct. Linux comes with a firewall, which is always on. Any firewall program merely accesses the settings; uncomplicated firewall is merely one of the ways to change the settings.

The default settings are pretty open. However, the way Linux works, I am not aware of any need to change the firewall settings for normal desktop use.

Well, that depends if you count the *tools required to create a firewall* as a firewall.

True, these are all built into Linux kernel itself (netfilter/iptables). But on the other hand they do absolutely nothing on their own. You still need to create the firewall rules with some way or other, and also a method for loading these rules on every boot. And for any type of advanced behavior you'll also need to add some program that changes these filtering rules based on different situations.

The correct thing to say would therefore be that Linux doesn't have a built-in firewall, it only has all the tools needed to create one. Pretty much any Linux firewall tool will add plenty of functionality that doesn't exist in the netfilter/iptables itself.

What comes to Ubuntu's default setup, there is no active firewall (as in "no rules for filtering any network traffic") unless you enable it yourself. On the other hand the default install doesn't have any running services that would listen for incoming network connections, so there really isn't anything that you'd need to filter either. In other words Ubuntu is safe without a firewall unless you install some server applications (and even then you'd only need a firewall if the server you run isn't supposed to be available from Internet, and lacks the necessary configuration options of it's own to limit incoming connections).

---

### Post by Dutch70 on 2011-03-29
This thread just gets better & better. :D

I just want to add that if you're concerned about banking or credit card info & such. It's a good idea to do all that from the live cd, that way there isn't any info left on your computer.

---

### Post by Lateralis on 2011-03-29
Thank you to Paddy Landau and mcduck for the clarifications!  :)

---

### Post by RotorRick on 2011-03-29
Ok, but this computer also still has XP on it, which I'll likely be using on some occasions, and so for that I'd like the Ubuntu side to not let malicious garbage infect the Windows side of things (too late?).

Windows might be a virus in and of itself (look how quickly it spawned in the 90's, you can't tell me it wasn't a virus!: LOL), but that's part of my concern.

---

### Post by Paqman on 2011-03-29
> **Dutch70 said:**
> 
I just want to add that if you're concerned about banking or credit card info & such. It's a good idea to do all that from the live cd, that way there isn't any info left on your computer.

Putting /tmp onto a ramdisk and switching to the guest account would also achieve this, as the guest account's home folder is spawned in /tmp.

---

### Post by Paqman on 2011-03-29
> **RotorRick said:**
> Ok, but this computer also still has XP on it, which I'll likely be using on some occasions, and so for that I'd like the Ubuntu side to not let malicious garbage infect the Windows side of things (too late?).


That would only work for some types of malware, and only if your Windows partition was mounted at the time (which it isn't by default). I would just take the normal precautions in Windows and not worry about the Linux side too much. Strong passwords, regular updates, and sticking to the repos for software should be sufficient.

---

### Post by mcduck on 2011-03-29
> **RotorRick said:**
> Ok, but this computer also still has XP on it, which I'll likely be using on some occasions, and so for that I'd like the Ubuntu side to not let malicious garbage infect the Windows side of things (too late?).

Windows might be a virus in and of itself (look how quickly it spawned in the 90's, you can't tell me it wasn't a virus!: LOL), but that's part of my concern.

As the Windows viruses don't work on Linux, they *can't* infect your Windows partition on their own. :D

The only possibility is that if you download an infected file, copy it to Windows partition, boot into Windows and run it there, it might of course cause problems. But on the other hand the antivirus application you run on Windows should catch it at that time, just like it would if you downloaded the file when running Windows.

---

### Post by RotorRick on 2011-03-29
You know, I'm liking this Linux thing more and more...


Thanks again!:popcorn:

---

