---
title: "WLAN not working, LAN not working, sudo not working!"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by doyenne on 2005-11-04
During the setup process, a LAN was not accessible, so I skipped network configuration. A WLAN was accessible, but I'll have to install ndis-wrappers before it will work.

Now the problem is: to download ndis-wrappers, I need an internet connection. However, the LAN is not working when I plug the laptop in. In this forum I read that I could use ifconfig, but then I get:
```
ifconfig eth0 up 192.168.0.1
SIOCSIFFLAGS: Access denied
SIOCSIFADDR: Access denied
SIOCSIFFLAGS: Access denied

```
Obviously, I need to have root priviliges. However, su cannot be used by default in Ubuntu, so I need to use sudo:
```
sudo ifconfig eht0 up 192.168.0.1
sudo: unable to lookup *computername* via gethostbyname()

```
Gnome suggests to add *computername* to /etc/hosts, but that leads of course to:
```
echo 127.0.0.1 *computername* >> /etc/hosts
bash: /etc/hosts: Access denied

```
So... I need to change /etc/hosts to be able to use sudo, but I need to use sudo to be able to change /etc/hosts...???

Well... I now really don't know what to try next! Anybody who can help me?

---

### Post by PaganHippie on 2005-11-04
You can load ndiswrapper from the installation CD

---

### Post by doyenne on 2005-11-04
How can I do that? It seems I need root priviliges for that.

I tried```
apt-get install ndiswrapper-utils
E: Could not open locking file '/var/lib/apt/lists/lock' - open (13 Access denied)
E: Could not lock "list directory" 
*(English version guessed, my Dutch install says "lijst-map vergrendelen")*
```And when I use *sudo*, I get again ```
unable to lookup *computername* via gethostbyname()
```

---

### Post by PaganHippie on 2005-11-04
Run apt-get from within sudo (sudo apt-get install ndiswrapper-utils), or better yet use synaptic to install it. sudo gives the following command temporary root permissions.

Once ndiswrapper is installed, go to your Gnome System menu, select Administration, then Networking. Much easier than trying to do it all from the command line. (Sorry, I don't speak, read, or write Dutch. It's a disease of we Americans, although some of us are conscious enough to be chagrined about it. ;))

Or, if you're so inclined, you could do it all from iwconfig & ipconfig. 'man iwconfig' & 'man ipconfig' will tell you more than I possibly could, there. Speaking from personal experience, though, once you have the wifi driver installed through ndiswrapper, the gui Networking utility is *much* less painful to work with.

---

### Post by Greyhair on 2005-11-04
" How can I do that? It seems I need root priviliges for that "

sudo passwd root

---

### Post by doyenne on 2005-11-04
Thanks for your reply again. It seems I am running into a vicious circle.
```
$ synaptic
*(message window opens)*
You must run this program as root.
$ sudo synaptic
sudo: unable to lookup *computername* via gethostbyname()
$ 
```
BTW, starting synaptic via the application menu from the GUI, has *nothing* as result. That's why I tried starting it from the commandline, hoping to get a meaningful error message.

As for now, I am longing for the good old time when I could simply use su! Personally, I really don't understand why sudo needs to lookup *computername*.

Is there no option to, for example, (I am really guessing) startup from a Knoppix live CD and then change the root password on the hard disk, then restart Ubuntu and use su?

---

### Post by doyenne on 2005-11-04
[QUOTE=Greyhair]sudo passwd root[/QUOTE]
```
$ sudo passwd root
sudo: unable to lookup *computername* via gethostbyname()
```

---

### Post by PaganHippie on 2005-11-04
If running synaptic from within the menus doesn't work, then your Ubuntu installation is seriously messed-up, and I'd suggest re-installing it from scratch. Don't try to repair your install, rather back up any data files you can't live without, reformat the hard disk, and scrap it and start over. Something is *way* not right here.

-----
[edit]

An afterthought: check to be sure the CD/DVD you installed Ubuntu from is not corrupt. Garbage In/Garbage Out, as they say.... ;)  It may be necessary to work from another copy to get a clean install.

---

### Post by doyenne on 2005-11-04
[QUOTE=PaganHippie]If running synaptic from within the menus doesn't work, then your Ubuntu installation is seriously messed-up, and I'd suggest re-installing it from scratch. Don't try to repair your install, rather back up any data files you can't live without, reformat the hard disk, and scrap it and start over. Something is *way* not right here.[/QUOTE]
Mmmm. The installation has just finished without any error messages. I did the following:
[LIST]
[*]boot from install cd
[*]leave all install options to the default (except language)
[*]skip network installation (as no LAN was available)
[*]boot
[*]login
[*]have the problem ascribed above
[/LIST]

Well, then I'm afraid that installing Ubuntu without current network connection is not possible.

---

### Post by PaganHippie on 2005-11-04
Hmm....

Unless the install CD you are working with is corrupted, I'm at a loss here. After a clean install, synaptic should work at least well enough to allow you to install ndiswrapper from the CD and get your wlan working.

Anyone else have any ideas?

-----
[edit]
Just out of curiosity, what sort of hardware are you working with?  Motherboard, CPU, RAM, WiFi adapter, and so on?

---

### Post by doyenne on 2005-11-07
Finally I solved the problem. The reason why synaptic was not working from the menu is clear: it uses sudo and sudo did not work because it could not resolve *computername*.

I booted and selected recovery mode from the GRUB menu. Ubuntu started in single user mode and after booting I was root. I entered the following commands:
```
passwd   (so, as from now, I will be able to do a su from the command prompt)
echo 127.0.0.1 *computername* >> /etc/hosts
reboot
```
After rebooting, everything works just fine. I can use su (which I like very much), sudo works and I can start synaptic right from the menu.

All repliers: thanks for the help! I'll now try to do the real work: installing ndis-wrappers and have my wifi (Belkin) pcmcia card working.

BTW, it embarrased me that it is that simple to log in as root. Just select recovery mode from the boot menu and you get it - without Ubuntu asking for the root password. I used to run Mandrake Linux (now Mandriva) which asked for the root password. Any idea how I can change this so that users need the root password for recovery mode?

---

### Post by caseyboardman on 2007-01-28
I caused myself the same problem when "cleaning up" my hosts file.  Thanks for solving the problem, it workd prefect.

---

