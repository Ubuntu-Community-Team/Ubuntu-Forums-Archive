---
title: "Root login problem"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by bcmillerFFD on 2010-01-05
While logged in as root I was using Firefox and also making a change to Panel properties.  Things hung up and I wound up shutting down.  Next time I logged in as root the panels appeared but nothing on them: Applications/Places/System/etc.

I pressed Ctrl Alt Delete/Shutdown and got this message:
A program is still running:  Panel not responding

There was no way to use System Monitor or do anything else so I clicked the "Shutdown Anyway" button.

Thanks for any suggestions.

Nu to Ubuntu,

---

### Post by Old_Grey_Wolf on 2010-01-05
Do you really mean that you were logged in as root? Or did you use sudo?

If you were logged in as root, you will not get much help on this forum.

Running as root is not a topic that we discuss here. Running as root introduces security problems, and increases the potential to really mess up your system.

---

### Post by x33a on 2010-01-05
You shouldn't really need to log-in as root on an ubuntu machine. And, as the above poster already said, it is against the forum policy to discuss about login as root.

Are you facing the problem while logged in as a normal user?

Also, running firefox or any browser as root is very dangerous and is discouraged.

---

### Post by bcmillerFFD on 2010-01-05
That's right.  I'm new to ubuntu, just installed it yesterday.

Yes I was logged on as root, didn't know about the sudo command.

---

### Post by bodhi.zazen on 2010-01-05
> **Old_Gray_Wolf said:**
> If you were logged in as root, you will not get much help on this forum.

> **x33a said:**
> And, as the above poster already said, it is against the forum policy to discuss about login as root.

Just for clarification, there are times when running as root is required, and for those (rare) occasions, running as root or setting a root password is supported on these forums.

This is very rare and in the vast majority of support requests setting a root password is not required.

Logging if to gnome as root and running network aware applications, such as firefox, is considers a significant security risk and are **strongly** discouraged.

The "problem" and source of confusion on the forms policy arises when people teach new users how to set a root password or run gksu nautilus, or worse how to log into gnome/KDE/Xubuntu as root, without explaining how Ubuntu is configured, how to use sudo, how to understand Linux permissions, or the potential risks of running as root, in terms of security, potential data loss, or potential damage to system files. Irresponsible use of the root account can cause problems ranging from minor glitches to changes in system files not easily reversed (requiring re-installation) to data loss.

The policy is that we ask you to teach new users how Ubuntu works and how to use sudo, and how to "properly" administrate their systems. This is the crux of the forums policy.

---

### Post by isaacalves27 on 2010-01-15
Hi :)

I have been using Ubuntu just for a couple of mounths now.

I have probably the same issue that was already posted...

1 -  i was not loged as root I was just working as usuak with my own user and then some security updates were delivered. I was asked to insert teh root password to install.. i did it. 

Afterwards the OS asked to be restarted what I did.

When logged in back I opened the browser and the browser was permanently offline.. had not the option to go back or forwrd on my navigation the address bar was always empty..

2 - reinstalled firefox several times with different packet managers: aptitude, synaptic... no luck

3 - checked some forums  and some other people had the same issue.. I figured out it was some kind of permissions issue and did

sudo firefox

Bling :D i have all my bookmarks and teh browser is running as a charm..!

I didnt new it is not so good to run the browser as root.. 

Any ideas of what could be preventing my user to access all the brpwser settings as before?

Thanks follks!

---

### Post by SuperSonic4 on 2010-01-15
```
sudo chown -R user:group /home/user/.mozilla
```

needless to say user is your username and group is often your username too

---

### Post by lisati on 2010-01-15
FYI: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by isaacalves27 on 2010-01-15
Thank you so much to you both for your prompt answers :) they did the trick (im not lsaunching firefox as root anymore)

just to small things:

1 ) firefox is now on verison 3.0 (and im not being able to upgrade it)
2) When i start it firefox is always offline.. What could be causing it?

Thanks for your help guys!

---

