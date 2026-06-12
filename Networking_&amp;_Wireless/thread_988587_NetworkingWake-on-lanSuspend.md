---
title: "Networking/Wake-on-lan/Suspend"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by TheSeanKelly on 2008-11-20
Hi all

I'm using intrepid on a dell latitude d820.

My end goal is to get wake-on-lan to work from a suspended state.  I've been reading lots of literature online and it seems like this has largely been unachieved to this point, but significant progress has been made and I have some ideas.

Firstly, wake-on-lan works perfectly fine with windows XP, so my bios supports it.  

I found this article:
[http://www.averyjparker.com/ubuntu-linux/](http://www.averyjparker.com/ubuntu-linux/)

In which the author claims to have got the feature to work.

> Here are the changes I made to make WOL from standby (S3) and Hibernate work.

I edited one of the hibernate/sleep scripts:

sudo pico /usr/lib/pm-utils/sleep.d/50modules

and commented out (*put a # in front of the lines) that say unload_network and invoke-rc.d networking restart (This prevents networking from being shut down at suspend/standby/sleep or hibernate and if we keep them from being shutdown, we shouldn’t need to restart them.)

Problem is, this line does not exist in my 50modules file.  I figure if there is a way to disable sleep.d from disabling networking moduels, wake-on-lan will work perfectly fine from a suspended or hibernated state.

Can anyone shed any light on this?!

Sean

---

### Post by TheSeanKelly on 2008-11-24
I'm going to hate myself forever for doing this...but...

bump!

---

### Post by Trebaruna on 2009-04-02
I realize this is a pretty old topic by now, but I am interested in exactly the same.
My desktop machine runs 8.04(.2), and it has the lines you mention sitting there in the script. My laptop runs 8.10 which apparently does not.
Perhaps someone will read this and find it useful :)

The good news is that my 8.04 machine does now wake from standby. There's no need to modify the /etc/init.d/halt script. In fact, if the author had read halt's manpage he'd discovered the -i flag is useless on Linux machines because the kernel does what that flag would do anyway, so also when it's not there.

The bad news is, of course, those missing lines. Judging from the script in 8.04, it looks at all the network interfaces, looks up what their module's name is and proceeds to unload those modules. Apparently we do not want that, so the line is commented out.

In 8.10 the suspend script unloads modules if A) they're specifically mentioned or B) they're network or USB modules. The file /etc/default/acpi-support specifies the list of modules you can whitelist so they don't get unloaded (it's MODULES_WHITELIST, I think the module names need to be space-separated, but try for yourself). 

Please note: I have not personally tried this, so I cannot guarantee that it will work. In fact, I cannot guarantee you won't make your computer shoot you in the face for doing this. However, I do think it's safe enough to try.

So, the upshot of this is:
0 - I don't know whether it works.
1 - go to /sys/class/net and find the interface you want/need.
2 - go to name_of_interface/device/driver and "ls -l" The file module turns out to be a link to the actual module. Note its name (bla../../module/this_part/)
3 - stick "this_part" into the file /etc/default/acpi-support: MODULES_WHITELIST="<insert here>"
4 - pray to the heathen gods for a working WOL.

Again, I hope this is useful but I make no claims to the workingness and/or not-blowing-your-computer-upness of this method.

---

### Post by rickwookie on 2009-04-02
> **Trebaruna said:**
> 3 - stick "this_part" into the file /etc/default/acpi-support: MODULES_WHITELIST="<insert here>"


I don't appear to have the file acpi-support anywhere.
Just upgraded to Jaunty and still don't have it.

My system resumes from S3 on WOL only once per boot, i.e. I boot, then 'sudo pm-suspend' then send a magic packet, and it rusumes, then I issue 'sudo pm-suspend' again, it suspends, but then won't respond to magic packets any more, it will only wake from keyboard or power button.

---

### Post by TheSeanKelly on 2009-04-02
Excellent, this solution works for me!!

Only issue I'm having now is that occasionally networking is disabled when resuming from standby, but I used to have this problem even without WOL.

---

### Post by Trebaruna on 2009-04-03
> **TheSeanKelly said:**
> Excellent, this solution works for me!!

Only issue I'm having now is that occasionally networking is disabled when resuming from standby, but I used to have this problem even without WOL.
Very glad it's working!

I've seen this issue on my laptop as well, but I haven't looked into it at all. I'd recommend trying to see if a manual configuration is more robust, so you can disable Network Manager altogether. You can specify interfaces and IP addresses (or DHCP) in /etc/network/interfaces
The process isn't terribly difficult, but you'll need to search the web/forums to find guides and examples, because I don't know the syntax very well.
Also, perhaps you can see if there's a bug report, and if not, make one? ;)

[quote=rickwookie]I don't appear to have the file acpi-support anywhere.[/quote]
According to aptitude the package acpi-support is not installed automatically, and this package provides that file. Try installing it and see if the file appears. Perhaps the packages acpid and acpi will also benefit you? Check their description to see whether you need/want them. I don't know when I installed them or why exactly, to be honest.
I'm afraid I have no idea why it would only resume once. I suggest looking around to see if this is a known bug.

---

### Post by rickwookie on 2009-04-04
> **Trebaruna said:**
> According to aptitude the package acpi-support is not installed automatically, and this package provides that file. Try installing it and see if the file appears. Perhaps the packages acpid and acpi will also benefit you? Check their description to see whether you need/want them. I don't know when I installed them or why exactly, to be honest.
I'm afraid I have no idea why it would only resume once. I suggest looking around to see if this is a known bug.

I installed the acpi-support package using aptitude, but looking at /etc/default/acpi-support is see that MODULES_WHITELIST is under the section marked:
```
#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#
```
and since above that is:
```
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"
```

and I've been using:
```
sudo pm-suspend
```
to sleep, I'm not sure that it's going to help.

I suspect that the network modules being unloaded/loaded is controlled by config files for pm-utils, but they seem to be scattered all over the place (/usr/lib/pm-utils/ and /etc/pm/) and I can't follow them.

The fact that it works once surely means that something is set up correctly at boot time that isn't re-set during a resume from suspend.

BTW my network connection always functions correctly after a resume from sleep (either the first WOL one, or via the power button).

---

### Post by Trebaruna on 2009-04-05
Hmm, it also has those lines in 8.10 it seems.
Keep in mind you can use Synaptic to see what files belong to a given package. Right-click the package you're interested in and select the Installed Files tab for a list.

I'm afraid I cannot offer you any more...

---

### Post by P4man on 2009-04-12
Im having the exact same problem. WOL works fine when the machine is turned off. It works ONCE when it it is in suspend,  after typing:
 
sudo ethtool -s eth2 wol g

Second time, after being woken from suspend, it wont wake up again. Unless I type in that command again. 

So this should be simple to solve, I probably just need to have that command somewhere in a script that is run each time when the machine resumes, but Im too much of a newbie to know how or where to do that.

Can anyone help?

also, Im looking for a way to have the machine wake up for printing (its used as printserver) without having to type a wakeonlan command on the client from which I want to print. Is that possible somehow?

---

### Post by durand on 2009-04-13
> **Trebaruna said:**
> I realize this is a pretty old topic by now, but I am interested in exactly the same.
My desktop machine runs 8.04(.2), and it has the lines you mention sitting there in the script. My laptop runs 8.10 which apparently does not.
Perhaps someone will read this and find it useful :)

The good news is that my 8.04 machine does now wake from standby. There's no need to modify the /etc/init.d/halt script. In fact, if the author had read halt's manpage he'd discovered the -i flag is useless on Linux machines because the kernel does what that flag would do anyway, so also when it's not there.

The bad news is, of course, those missing lines. Judging from the script in 8.04, it looks at all the network interfaces, looks up what their module's name is and proceeds to unload those modules. Apparently we do not want that, so the line is commented out.

In 8.10 the suspend script unloads modules if A) they're specifically mentioned or B) they're network or USB modules. The file /etc/default/acpi-support specifies the list of modules you can whitelist so they don't get unloaded (it's MODULES_WHITELIST, I think the module names need to be space-separated, but try for yourself). 

Please note: I have not personally tried this, so I cannot guarantee that it will work. In fact, I cannot guarantee you won't make your computer shoot you in the face for doing this. However, I do think it's safe enough to try.

So, the upshot of this is:
0 - I don't know whether it works.
1 - go to /sys/class/net and find the interface you want/need.
2 - go to name_of_interface/device/driver and "ls -l" The file module turns out to be a link to the actual module. Note its name (bla../../module/this_part/)
3 - stick "this_part" into the file /etc/default/acpi-support: MODULES_WHITELIST="<insert here>"
4 - pray to the heathen gods for a working WOL.

Again, I hope this is useful but I make no claims to the workingness and/or not-blowing-your-computer-upness of this method.

Works perfectly, thanks!

I'm trying to take this one step backwards and WOL my old computer which only supports APM. Would it be possible if I suspend it with apm -s?

---

### Post by P4man on 2009-04-14
To answer my own question: I had to put a little script in
/etc/pm/power.d/

```
#!/bin/bash
#
# enables WOL (hopefully)

ethtool -s eth2 wol g
```

And make it executable.
That made WOL work after a resume.

Then I added the same command to 
/etc/rc.local

to make it work on first boot.

Almost there, now all I need is to find a way to have clients send a magic packet to the printserver each time they print something.

---

### Post by durand on 2009-04-14
Maybe you could have a script which checks the print spool every few seconds and sends the magic packet signal if there is something in the queue? The problems with this method are that you would need the script on all the computers that will be printing...

---

### Post by P4man on 2009-04-14
its a home lan, so installing it on every machine is no problem, and I dont see a way to avoid that anyway. No one but the client would know there is something to print. A bigger problem is that my scripting skills are close to nill :) But it sounds like a good idea

---

### Post by durand on 2009-04-14
I would write the script but I have no idea how the spool works. I think that when you queue something it goes into /var/spool/cups but I can't really test that. There might also be a cups app that allows you to check..Maybe if you found what that was, I could write that script. We could even get it to suspend the print server when it has finished it's job via ssh.

---

### Post by P4man on 2009-04-15
thanks for the offer, Ill look into it.. but Im still struggling with the printing. If I print through samba,  it seems to work (except some clients won't find the samba printer), but if I print through "ipp" (cups I think) and the print server is suspended, the clients become unresponsive when opening a print dialogue, I guess looking for the printer which is no longer reachable, and once they finally give up searching, they can not print "offline".. that sucks, I have to solve that first.

As for waking up the print server, for now i just made a panel starter on each client that sends the magic packet. I guess that will do for now. This is going too much off topic anyhow, Ill send you a pm if I need a hand with the script :)

---

### Post by TheSeanKelly on 2009-06-07
This fix still works for me in Jaunty, for what it's worth.

---

### Post by TheSeanKelly on 2009-06-07
I should have specified; it works for suspend, NOT for shutdown.  Strange.  Anyone know how to do a similar whitelist of the module for shutdown?

When I power the computer off, the network card light remains on.  However, it does not respond to the magic packet.

It DOES respond to the magic packet for a very short time after shutdown, but then I presume it turns itself off after a while.

---

### Post by TheSeanKelly on 2009-06-07
I lied.  I appear to still be getting the issue where it works for about five minutes after suspend/power off, and then stops for no reason.

Any ideas?

---

### Post by TheSeanKelly on 2009-06-26
I'm still struggling with this issue.

I think the problem might lie in WHAT command is being used to suspend the machine?  Will pm-utils work, whereas pressing "suspend" in gnome will not, etc?  If this is the case, how would I either change the default command run by gnome, or enable a similar fix for whatever script gnome uses to suspend?

---

### Post by uJoe on 2010-04-02
Check out this thread for wake up after power off. This worked for me.

[http://www.linuxquestions.org/questions/showthread.php?p=3921202#post3921202](http://www.linuxquestions.org/questions/showthread.php?p=3921202#post3921202)

---

