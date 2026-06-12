---
title: "UFW firewall blocking Evolution Mail"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by gilx on 2009-03-20
I recently started using the ufw firewall and everything seemed to be working ok with it until I tried using the evolution mail client.

Whenever I turn on my computer and start to use evolution I have to disable ufw, start evolution, then enable the firewall again.

```
sudo ufw disable
# Start evolution...
sudo ufw enable
```

If I don't do this I just get told that evolution can't connect to the IMAP server. However, having disabled/re-enabled the firewall once, if I close evolution and then open it later I don't have to go through the ufw disable/re-enable thing again. So, presumably, it must have remembered something.

It didn't seem hard to open a couple of ports for ssh and azureus/vuze so it must be something simple, but I can't see it.

I'm using Ubuntu 8.10 but am new to this whole ubuntu/linux thing so still learning. All help/advice is much appreciated.

Rob

---

### Post by lovinglinux on 2009-03-20
That is weird, because ufw does not block outgoing connections (as far as I remember). 

Do you have tested other firewall managers like Firestarter before using ufw? Maybe another firewall manager is loading after ufw and messing up with the iptables rules. 

This makes sense, because previous iptables rules would be overwritten once you restart ufw, so you don't have to go through the ufw disable/re-enable thing again. That would explain why Evolution works after restarting ufw.

---

### Post by gilx on 2009-03-20
You're right, I had tried Firestarter, but heard somewhere that it was out-dated and I since I am new to ubuntu, and felt like experimenting, decided that I would try something else ie ufw.

However, I thought I had removed Firestarter ```
sudo apt-get autoremove firestarter # This is what I did, I think
``` so I don't understand how it could still be interfering.

Thank you so far. Though I've no idea what would be the next step. :???:

---

### Post by lovinglinux on 2009-03-20
Try

```
sudo apt-get remove firestarter
```

or

```
sudo apt-get purge firestarter
```

The first one will only remove the application, while the second one will also remove config files.

The command you used is wrong. The autoremove option is used alone (as far as I know) to remove packages not used anymore by any applications.

To learn more about installation/removal commands run this:

```
man apt-get
```

The man command stands for manual. You can use man with any application, if they have a manual page.

---

### Post by gilx on 2009-03-20
Thank you. I realised it wasn't the old firestarter installation but MoBlock that was causing the problem. Used diff to compare the outputs of iptables -L before and after restarting ufw and it seemed obvious then.

Hadn't really appreciated the difference between apt-get autoremove and remove but tried as you recommended on MoBlock. After a bit of testing I'm fairly confident this has fixed the evolution problem.

Now to figure out how to get moblock and ufw to behave together.

Thanks for answering my question. Much appreciated.

---

### Post by lovinglinux on 2009-03-20
> **gilx said:**
> Thank you. I realised it wasn't the old firestarter installation but MoBlock that was causing the problem. Used diff to compare the outputs of iptables -L before and after restarting ufw and it seemed obvious then.

> **gilx said:**
> Now to figure out how to get moblock and ufw to behave together.

Moblock also creates rules for iptables (the firewall), but they are only for blocking IPs from an ip blocklist. You probably configure moblock to load too many lists and the IP of your mail provider was included in it. So, Evolution could not connect to the mail server because moblock was blocking it's ip address. 

This is simple to solve. Just add the ip of your mail provider to moblock's allow list. You can also specify an outgoing port to not be blocked by moblock (993 in this case). But since there is only one application and one server that you use with this port, then whitelisting the ip is the recommended procedure. I usually allow outgoing http and https ports in the moblock's config, because Firefox will connect to several IPs on these ports, so whitelisting every web site ip you visit is too much work.

You can use [mobloquer]("http://mobloquer.foutrelis.com/") gui to manage ip blocklists, whitelists and monitor blocked connections, until you are comfortable enough to control it by command-line.

To use moblock and ufw together, you must make sure that ufw starts before moblock. If you restart ufw after starting moblock, then it will override moblock's rules, turning it useless. That's why you were able to use Evolution after restarting ufw. 

You can learn more about moblock at [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)
and from the [General Moblock Thread]("http://ubuntuforums.org/showthread.php?t=803183")

> **gilx said:**
> Hadn't really appreciated the difference between apt-get autoremove and remove but tried as you recommended on MoBlock. After a bit of testing I'm fairly confident this has fixed the evolution problem.

Linux applications can share several libraries, so when you install a new software the system will check if all libraries that it requires (dependencies) are installed. If not, it will ask for installing them. When you **remove** an application, the system does not remove shared libraries. So, sometimes a few unused libraries are left on the system. The **autoremove** command (which should not be followed by any application name) will check if there are any libraries in the system that are not in use by any other application installed and will remove them. This is not actually necessary, unless you like to keep your system clean.

---

### Post by gilx on 2009-03-20
Thank you very much. Hopefully I will be ale to pass on similarly useful advice one day.

---

