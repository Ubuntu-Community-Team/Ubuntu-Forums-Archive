---
title: "Disactivate Update Manager"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by ccaaee on 2011-07-24
Hi All

Ubuntu 11.04, acer aspire one, xfce
Every time I log in I get the Update Manager even though in the settings I've asked it not to check for updates.  I there a way of dis-activating this?

Thanks

Chris

---

### Post by mike555 on 2011-07-24
Updates are important , they are often for security ....... but you should be able to set it to notify you weekly instead of daily......

---

### Post by e79 on 2011-07-24
> **ccaaee said:**
> Hi All

Ubuntu 11.04, acer aspire one, xfce
Every time I log in I get the Update Manager even though in the settings I've asked it not to check for updates.  I there a way of dis-activating this?

Thanks

Chris

Why would you refuse to update your system as it fixes bugs, enhance security and so on ? These are not Windows updates that take ages to install and need a reboot each time... so I would strongly suggest that you simply click on the update manager and install them when there is some. Few clicks, few seconds = peace of mind of beeig protected/up-to-date.

Just my $0.02

---

### Post by amjjawad on 2011-07-24
This is a very bad idea!

---

### Post by Rex Bouwense on 2011-07-24
Agree with the three previous posts.  If you do not want to be bothered set the update manager to automatically download and install.  That way you will not have to be bothered.  I for one want to see what is being updated and the updates are not trivial.  Enjoy.

---

### Post by oldsoundguy on 2011-07-24
Just remember that the updates not only update your system and your security, but update every program you have activated within that system to include your browser, eMail client and so on. (everything you have grabbed from the repositories.)
The only thing it will not update is plug ins in your browser and eMail.  That will happen when you re-open them.

NORMALLY re-boot is only required if you get a KERNEL update.  So why not update?
This is NOT like Windows, where an update can (at very annoying intervals) bork a 3rd party program (SP 3 in XP did just that with the D-Link WIRELESS utility (Airplus.cfg .. a better utility than the Windows wireless manager by a MILE!) and where you have to re-boot and wait for crap to install on the shut down or power up OR BOTH.
(And then you have to go searching for your 3rd party program updates!!)

---

### Post by egalvan on 2011-07-24
> **oldsoundguy said:**
> 
NORMALLY re-boot is only required if you get a KERNEL update. 


And even these are disappearing with the latest routines that allow a kernel to be patched while running, and with no re-boot necessary. :P

---

### Post by amjjawad on 2011-07-24
Windows Update? O_o
One of the main reasons I switched to Linux is the Update thing in Windows. Can't even find a word to describe that.

---

### Post by Rex Bouwense on 2011-07-24
Be nice (Ha)  Some people haven't seen the light yet and perhaps never will.  Just trying to help the OP see the possible error of his desired outcome.

---

### Post by ccaaee on 2011-08-05
Thanks to everyone for the informative answers you sent

I guess I didn't ask the right question.  What I'd like to do is to decide when to update not whether it is a good or bad idea.  Every time I turn on my computer it starts the update manager.  Does anyone know how to disable this at startup?

Thanks again

Chris

---

### Post by amjjawad on 2011-08-05
> **ccaaee said:**
> Thanks to everyone for the informative answers you sent

I guess I didn't ask the right question.  What I'd like to do is to decide when to update not whether it is a good or bad idea.  Every time I turn on my computer it starts the update manager.  Does anyone know how to disable this at startup?

Thanks again

Chris

Note sure about Xubuntu but I hope this will help.

You can set it every two weeks but then how would you know if there is some important updates or there isn't?

When we said "it's a bad idea" we meant that the Update Manager is a reminder that should tell you it's time to update your system. Disabling it on startup or set it to remind you every two weeks for example is a bad idea. That's the point :)

---

### Post by jtarin on 2011-08-05
> **ccaaee said:**
> Hi All

Ubuntu 11.04, acer aspire one, xfce
Every time I log in I get the Update Manager even though in the settings I've asked it not to check for updates.  I there a way of dis-activating this?

Thanks

ChrisThere is no way to dis-activate anything.:P
Now if you want to talk about deactivate or disable....that's another story. What part annoys you the most?
You can turn off automatic-updates for good by going to Menu>system>preferences>sessions. All auto-started desktop settings are here.Beware...the previous post spoke the truth.....you have complete responsibility now. You can still manually update.

---

### Post by amjjawad on 2011-08-05
> **jtarin said:**
> You can still manually update.

```
sudo apt-get update
``````
sudo apt-get upgrade
```But then, how would you know there are some updates anyway? who will remind you? 
running the above commands every now and then? well, you had something "was" reminding you automatically :)

We have explained to you but as jtarin said, you're responsible for the consequences ;)

---

### Post by westie457 on 2011-08-05
> **ccaaee said:**
> Thanks to everyone for the informative answers you sent

I guess I didn't ask the right question.  What I'd like to do is to decide when to update not whether it is a good or bad idea.  Every time I turn on my computer it starts the update manager.  Does anyone know how to disable this at startup?

Thanks again

Chris

For that you have to disable the start up program 'update-notifier' though I am not going to explain what to do it is very simple to work out. After all I managed to find what to do in less than a minute. Your OS is doing it's best to protect you. You should really be doing more to protect it.
As has already been stated the updates are small in size and quick to install with few reboots needed. Unlike Windows where I have had situations where 1 update has taken 4 hours to install then had the restart issue with configuring the update during shut down and start up. A further 30 minutes without the use of the pc. Very annoying in my view.

So really leave the Update Manager and Update Notifier alone. They work properly.

---

### Post by scruffyeagle on 2011-08-05
> **ccaaee said:**
> Thanks to everyone for the informative answers you sent

I guess I didn't ask the right question.  What I'd like to do is to decide when to update not whether it is a good or bad idea.  Every time I turn on my computer it starts the update manager.  Does anyone know how to disable this at startup?

Thanks again

Chris

You should be able to set it as never checking for updates, via the Update program's controls. Even if that doesn't work, all you need to do is click the "Cancel" button on the box which pops up. Do that, and it goes away. Won't pester you again, that day.

Updating at the time of your choosing is easy. Open a terminal window, and type

```
sudo apt-get update && sudo apt-get upgrade
```

It will prompt you for your admin-eligible password (your only password, if you only have one user set up). Type it in, hit <Enter>, and it will do the rest automatically. To close the terminal, type "Exit" & hit <Enter>. Or just click on the close window button at the corner of the box.

---

