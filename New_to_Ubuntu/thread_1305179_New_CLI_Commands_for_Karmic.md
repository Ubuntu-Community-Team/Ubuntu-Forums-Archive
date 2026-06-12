---
title: "New CLI Commands for Karmic"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-29
Karmic ships with a much easier to use CLI interface, if you noticed like I did and were caught off-guard, here are the commands that have changed:

[COLOR="Red"]Commands that no longer work:[/COLOR]
   **- Anything with "init.d" in it, or services pertaining to "hal"**
EDIT: _Some_ of the "init.d" commands still work, but the "service" command also works with these. It is recommended to learn the "new" command, as init.d and hal is being slowly depreciated. (When I say "new" commands, I mean new to Ubuntu, anyway)

[COLOR="SeaGreen"]Remedies for these outdated commands:[/COLOR]
   **- If you need to stop/start GDM, or any other service, the command is simple:**
```
service gdm restart
```

This series of commands also works with any other init.d command you can think of. For example, this restarts the networking service:
```
service networking restart
```

[COLOR="Red"]To refresh Ubuntu's list of devices, the command ***used*** to be:[/COLOR]
```
sudo /etc/init.d/hal restart
```
**The command has now moved to this. Please note that you cannot use the command "restart" for the udev service. You will get a bizarre message if you try.**
```
service udev stop
service udev start

```

---

### Post by twright on 2009-10-29
You can also just use the start and stop commands to do this now

---

### Post by Shpongle on 2009-10-29
is there any documentation you know of that i can up on the changes ??

---

### Post by asuastrophysics on 2009-10-29
> **DillByrne said:**
> is there any documentation you know of that i can up on the changes ??

I have been googling for this all day, but haven't found an official ubuntu wiki with the list of changes. I might start one, or I could just make this guide very elaborate with the help of some experts :D

You can always run 
```
man service
```
To view everything about this new command. I will post on my thread a link to an Ubuntu Karmic CLI wiki, as soon as one becomes available.

---

### Post by KIAaze on 2009-10-29
The "service" command is not new.
I have been using it before.

Also, it's more Debian/Ubuntu specific, so be careful about using it in scripts. (OpenSUSE doesn't have it for instance if I remember correctly.)

And commands with "init.d" in them still seem to work for me.
At least:
```
sudo /etc/init.d/firehol restart
```
worked.

---

### Post by Shpongle on 2009-10-29
ok thanks man :-)

---

### Post by asuastrophysics on 2009-10-29
> **KIAaze said:**
> The "service" command is not new.
I have been using it before.

Also, it's more Debian/Ubuntu specific, so be careful about using it in scripts. (OpenSUSE doesn't have it for instance if I remember correctly.)

And commands with "init.d" in them still seem to work for me.
At least:
```
sudo /etc/init.d/firehol restart
```
worked.

Hey what is "firehol", anyway?
Can you restart that program by doing this: ?
```
sudo service firehol stop
sudo service firehol start
```

---

### Post by twright on 2009-10-29
> **asuastrophysics said:**
> Hey what is "firehol", anyway?
Can you restart that program by doing this: ?
```
sudo service firehol stop
sudo service firehol start
```
just use sudo restart firehol

---

### Post by KIAaze on 2009-10-29
> **asuastrophysics said:**
> Hey what is "firehol", anyway?
Can you restart that program by doing this: ?
```
sudo service firehol stop
sudo service firehol start
```

FireHOL is a firewall, or more precisely an iptables configuration tool: [http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)

And yes, the commands you gave work too.

edit:
> just use sudo restart firehol
Does not work for me.
```
sudo restart firehol
restart: Unknown job: firehol
```

Probably because firehol and other daemons use the System-V init instead of upstart.
```
$ man restart
...
       initctl allows a system administrator to communicate and interact with the Upstart init(8) daemon.
...

```

---

### Post by asuastrophysics on 2009-10-29
> **twright said:**
> just use sudo restart firehol

That "restart" command seems to be disappearing more and more everyday for common services. Furthermore, it seems to be totally random in how often it works for "service" "start/stop" commands:

Works Here:
```
jake@girdy-laptop:~$ sudo service udev restart
[sudo] password for jake: 
jake@girdy-laptop:~$ 

```

But Not Here:
```
jake@girdy-laptop:~$ sudo service gdm restart
jake@girdy-laptop:~$ 

```
^It LOOKS like it worked here, but honestly if GDM had restarted, it would have gone back to the login screen. Nothing happened when I issued this command.  :confused:

EDIT: For the record, I think the "gdm" command uses upstart too, but restart doesnt work for it ...weird. 

2ND EDIT: My Karmic upgrade failed, this is why I couldn't get gdm to restart using the "restart" command. It works now. ;)

---

### Post by lovinglinux on 2009-10-29
> **KIAaze said:**
> And commands with "init.d" in them still seem to work for me.
At least:
```
sudo /etc/init.d/firehol restart
```
worked.

I can't test it right now, but this was working a couple of days ago:

```
sudo /etc/init.d/kdm restart
```

---

### Post by The Cog on 2009-10-30
Try doing it from a tty console (Ctrl-Alt-F1) instead of from a GUI terminal window. I think that from a terminal window, the stop bit works, which kills the GUI, killing the window, killing the command before it can get round to starting gdm again. Or do it from inside **screen** so it doesn't die when its terminal is nuked.

---

