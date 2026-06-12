---
title: "Geeks of War OR: How I learned to stop worrying and love Dial-a-Geek computer support"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by Phayder92889 on 2008-01-06
My family is in a transitional phase, right now. I'm getting ready to graduate and go off and join the Navy, thereby removing my physical geek aura from the area, likely to cause massive problems in the household computers the moment I leave.

My Grandma and little Brother both got new computers for Xmas, courtesy me, with Feisty and SSH preinstalled. My mom's still on Win2K, but she's good enough to fix most of her own problems.

Basically, the setup was supposed to work like this: I get an email / text message / phone call / hand-written note / message in a bottle from my family, informing me of a 'puter error, I SSH into my personal box, then SSH into the offending system and fix the issue at hand.

I made the mistake of informing the rest of my family about this...

My grandmother lost her ever-loving s#^% all over me and my mom, accusing me of spying on her computer and stealing her passwords and all of this other stuff. (WTF?!? I made it excessively difficult to access anything but Solitaire and Firefox, what else could she be doing? I'm pretty sure the US Gov't doesn't hide the launch codes on the computers of tech-illiterate, xenophobic, racist old women, but I could be wrong...)

Enter: Dial-A-Geek. (I don't actually know which representative firm he was from, but it was a local one, and it fits.)

He starts off by doing... something... to disable my access to my grandmother's computer. It responds to ping, can SSH to my box, but I can't do the reverse. NMap doesn't see it as alive, all ports appear blocked, and I'm starting to get rather frustrated with the ever-loving gall of this hosebox and whatever it was that he did.

I'm relatively certain that he didn't do anything too arcane or obscure, as he needed a GUI to attempt to fix my grandmother's wireless NIC, but he could've ham-handedly thrown together a few basic commands that destroyed my efforts of good-will and generosity.

My mom's pissed, saying that if it breaks, I should let her spend her money on some half-wit to pretend to fix it. I disagree, simply because of principal and my intolerance of anyone else trying to admin my network. (It's a rather common malady, I'm sure of it...)

What I ask of you, the Populi Internetus, is this: How do I un-f&$% the system so I don't have to go interrogate him with a tire-iron and a tall italian guy named Guido who likes to watch.

---

### Post by mannih2001 on 2008-01-07
Sounds like he made her unistall openssh-server?

---

### Post by heindsight on 2008-01-07
> **mannih2001 said:**
> Sounds like he made her unistall openssh-server?

Either that, or he just deactivated sshd (by moving /etc/rc2.d/S??sshd to /etc/rc2.d/K??sshd).

---

### Post by Phayder92889 on 2008-01-08
*Facepalm*

duh... Sorry, I'm an idiot in regards to obvious things. I checked on SSH's installation status, but apparently forgot the whole server aspect of it all. Thanks, though.

erm... Nmap still isn't showing anything on her machine, and it's not responding to ping. How do I fix those issues (If it shows the same problem after I reinstall the server, I'll let y'all know)

---

### Post by heindsight on 2008-01-08
If it's not responding to pings, he might have set up iptables to drop pings. Perhaps iptables is also blocking incomming connections, does nmap show the ports as closed or filtered?

You can check iptables rules using ```
sudo iptables -L
```

---

### Post by Phayder92889 on 2008-01-15
```
ls -a /etc/rc2.d
.                            S19cupsys         S25bluetooth
..                           S20apmd           S30gdm
README                       S20apport         S89anacron
S05vbesave                   S20hotkey-setup   S89atd
S10acpid                     S20makedev        S89cron
S10powernowd.early           S20nvidia-kernel  S98usplash
S10sysklogd                  S20powernowd      S99acpi-support
S10xserver-xorg-input-wacom  S20rsync          S99laptop-mode
S11klogd                     S22consolekit     S99rc.local
S12dbus                      S24avahi-daemon   S99rmnologin
S12hal                       S24dhcdbd         S99stop-readahead

```

```

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

those are the verbatim responses. openssh-server is installed, and the latest version.

Her machine doesn't even respond over 127.0.0.1 to ping, ssh, nothing, but I can still SSH into my own machine. This is surreal...

Nmap says that all ports are closed, and that the host isn't even up, but it still grabs a DHCP address from the router upstairs, giving me at least an IP to work with. I'm baffled, to say the least.

---

### Post by kvonb on 2008-01-15
-

---

### Post by heindsight on 2008-01-15
> **Phayder92889 said:**
> ```
ls -a /etc/rc2.d
.                            S19cupsys         S25bluetooth
..                           S20apmd           S30gdm
README                       S20apport         S89anacron
S05vbesave                   S20hotkey-setup   S89atd
S10acpid                     S20makedev        S89cron
S10powernowd.early           S20nvidia-kernel  S98usplash
S10sysklogd                  S20powernowd      S99acpi-support
S10xserver-xorg-input-wacom  S20rsync          S99laptop-mode
S11klogd                     S22consolekit     S99rc.local
S12dbus                      S24avahi-daemon   S99rmnologin
S12hal                       S24dhcdbd         S99stop-readahead

```

Well, according to this, sshd is not being started at boot.
```
sudo update-rc.d ssh multiuser 16 84
sudo invoke-rc.d ssh start
``` should fix that.

It is possible that the kernel is dropping all ping packets.
You can check this by doing:
```
cat /proc/sys/net/ipv4/icmp_echo_ignore_all
```
if that outputs 1, then the kernel is dropping pings
you can enable pings again using:
```
echo 0 | sudo tee /proc/sys/net/ipv4/icmp_echo_ignore_all
```
If this is the reason why it's not responding to pings, then have a look at /etc/sysctl.conf
this probably contains a line like:
```
net.ipv4.icmp_echo_ignore_all = 1
```
comment that out.

---

