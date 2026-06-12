---
title: "Get output of what Ubuntu is currently doing?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by danill2008 on 2009-11-04
Im just interested : Is there a way to get the output in terminal of what your computer is currently doing and also to let it keep going on?

---

### Post by bobtfish on 2009-11-04
Try the terminal command "top".
From the man page:
" The  top  program  provides  a dynamic real-time view of a running system.  It can display system summary information as  well  as  a list  of  tasks  currently being managed by the Linux kernel."

---

### Post by philinux on 2009-11-04
> **danill2008 said:**
> Im just interested : Is there a way to get the output in terminal of what your computer is currently doing and also to let it keep going on?

Also system>admin>system monitor

---

### Post by Penguin Guy on 2009-11-04
I'm not sure what exactly you mean, if you want the alternative of [COLOR="Green"]gnome-system-monitor[/COLOR] then you should try the [COLOR="green"]top[/COLOR] command.

---

### Post by ukripper on 2009-11-04
you can use htop, top,:

To install htop just run in terminal:
```
sudo apt-get install htop
```

and then to view current system state:```
htop
```

---

### Post by danill2008 on 2009-11-04
> **Penguin Guy said:**
> I'm not sure what exactly you mean, if you want the alternative of [COLOR=Green]gnome-system-monitor[/COLOR] then you should try the [COLOR=green]top[/COLOR] command.

That lists the processes. I want to see what it does, by that I mean, is there no way to see what your computer is doing e.g starting this, running this application etc. in verbose mode. Almost like running the screenlet "Output"....

---

### Post by stderr on 2009-11-04
You can launch apps via the terminal and see its stdout and stderr that way (e.g. start a terminal and type the following to launch rhythmbox, then switch back to the terminal too see any debug output). 

```
rhythmbox
```

You can also look at the system logs with something like this (Ctrl+C to exit):

```
tail -f /var/log/syslog
```

What in particular do you have in mind?

edit: From your description, getting a process list (with e.g. top) sounds exactly like what you want... you can see what's running, what's eating CPU, what's doing a lot of I/O (reading/writing files), what's using a lot of RAM, nice levels, etc. etc. In terms of giving the same data in a more human-centric format, I'm afraid I've no clue. Personally I would advise using top (as I do): it tells you almost everything you need to know.

---

### Post by Ant59 on 2009-11-04
The GNOME System Monitor is like the Task Manager process list of Windows. This shows you what processes your PC is running. If you want to get an output from a specific program, you'd have to run it from the terminal in verbose mode.

---

### Post by danill2008 on 2009-11-04
> **stderr said:**
> You can launch apps via the terminal and see its stdout and stderr that way (e.g. start a terminal and type the following to launch rhythmbox, then switch back to the terminal too see any debug output). 

```
rhythmbox
```You can also look at the system logs with something like this (Ctrl+C to exit):

```
tail -f /var/log/syslog
```What in particular do you have in mind?

I want to do the same as what "Output" does in Screenlet Manager. It shows me my eth0 is down etc. That would be great, but I want it to be continues and also do it through terminal without running "Output"

---

### Post by ukripper on 2009-11-04
> **danill2008 said:**
> I want to do the same as what "Output" does in Screenlet Manager. It shows me my eth0 is down etc. That would be great, but I want it to be continues and also do it through terminal without running "Output"

I think you need nagios - [http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html](http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html)

It gives you realtime monitoring of your system. I monitor servers with nagios.

Better option for you will be use munin. Easier to setup - [http://www.debuntu.org/how-to-monitoring-a-server-with-munin](http://www.debuntu.org/how-to-monitoring-a-server-with-munin)

---

### Post by stderr on 2009-11-04
> **danill2008 said:**
> I want to do the same as what "Output" does in Screenlet Manager. It shows me my eth0 is down etc. That would be great, but I want it to be continues and also do it through terminal without running "Output"

Just installed Screenlets; Output just seems to list messages for me. Cross-reference your end and see if it's the same.

```
tail -f /var/log/messages
```

---

### Post by danill2008 on 2009-11-04
> **ukripper said:**
> I think you need nagios - [http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html](http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html)

It gives you realtime monitoring of your system. I monitor servers with nagios.

Better option for you will be use munin. Easier to setup - [http://www.debuntu.org/how-to-monitoring-a-server-with-munin](http://www.debuntu.org/how-to-monitoring-a-server-with-munin)

Ok thnx, I will try that. Does somebody know what command, service or program " Output runs? It states here in OutputScreenlet's About that it is a "A screenlet that displays output from any unix command" Any ideas what it runs or uses?

---

### Post by danill2008 on 2009-11-04
> **stderr said:**
> Just installed Screenlets; Output just seems to list messages for me. Cross-reference your end and see if it's the same.

```
tail -f /var/log/messages
```

Nope, I tried that it just says something about pulseaudio, while my output displays eth0 is up at 100Mbps. full duplex. I even tried running virtualbox, that shows under output, but also nothing under ouput. I wonder what command ouput uses....

---

### Post by stderr on 2009-11-04
Hmm it's probably kern.log then:

/var/log/kern.log

---

### Post by danill2008 on 2009-11-04
> **stderr said:**
> Hmm it's probably kern.log then:

/var/log/kern.log

Thank you! That worked great and thnx to everyone else who helped me....
Btw How do I mark this thread as solved?

---

### Post by stderr on 2009-11-04
No problem: you've got me using those Screenlets too now!

---

### Post by danill2008 on 2009-11-04
> **stderr said:**
> No problem: you've got me using those Screenlets too now!

Yes they work like a charm...

---

### Post by stderr on 2009-11-04
> **danill2008 said:**
> Btw How do I mark this thread as solved?

You're not the only one who got confused on that one... [http://ubuntuforums.org/showthread.php?t=1265602]("http://ubuntuforums.org/showthread.php?t=1265602")

---

### Post by danill2008 on 2009-11-04
> **stderr said:**
> You're not the only one who got confused on that one... [http://ubuntuforums.org/showthread.php?t=1265602](http://ubuntuforums.org/showthread.php?t=1265602)

Ahh, thnx very much. Long live ubuntu!

---

