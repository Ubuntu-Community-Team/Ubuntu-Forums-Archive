---
title: "Please help!  Can't log in, I messed something up!"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-09-10
I made a big mistake.  I was trying to get rid of wine, so I ran ```
sudo apt-get purge wine*
``` using the * was a BAD idea.  I hit enter and I noticed it started uninstalling a lot more than just wine, such as compiz programs and other settings.  I immediately did ctrl-c and then closed out of terminal and everything was working.

Now, I restarted my laptop and I can not login.  First off, I have auto-login enabled and it brought be to the regular login screen; that worried me.  I enter in my username and password and the screen flashed black, and then goes directly back to the login screen.

I can however boot into recovery console, and also I can login via non-GUI terminal (ctrl-alt-F2), but I can't log in graphically (ctrl-alt-F7).  Is there a way I can undo or revert back to where I was?  when I login via the terminal and then try to switch to the graphical (F7), it does not switch.  It seems to get stuck in /etc/init.d somewhere as if something is trying to or isn't starting up.

Please give any advice possible or let me know if you need more information.

Thank you!

---

### Post by ranch hand on 2010-09-10
The first thing to do at a time like this is to remember to breath.

The next thing to do is to go to recovery and run the "dpkg fix broken packages" option.  This may well fix it.

When you use apt-get you always should get a chance to approve the process.  Did this happen for you?  If not I would like to know and you should file a bug.

If it did, smack yourself up side the head.  When I do something like the command you used I copy/paste the read out of what will be done to gedit so I can pread it out and actually see what the devil is going to be removed.

I am glad I am not the only one good at self inflicted wounds.

---

### Post by x C0MMAND0 x on 2010-09-10
> **ranch hand said:**
> The first thing to do at a time like this is to remember to breath.

The next thing to do is to go to recovery and run the "dpkg fix broken packages" option.  This may well fix it.

When you use apt-get you always should get a chance to approve the process.  Did this happen for you?  If not I would like to know and you should file a bug.

If it did, smack yourself up side the head.  When I do something like the command you used I copy/paste the read out of what will be done to gedit so I can pread it out and actually see what the devil is going to be removed.

I am glad I am not the only one good at self inflicted wounds.

1. Yes I ran dpkg fix broken packages; same error

2. It did give me a chance to approve and I rushed through it like an idiot

3. I did smack myself in the head.

Any other ideas on what to do / how to fix it?

I figure, worst case scenario is mount my HD externally and copy all of data over and reinstall, but I reallllly don't want to have to go that...

---

### Post by Elfy on 2010-09-10
You could try installing (assuming you have ubuntu) ubuntu-desktop from recovery.

See what it says it is going to install - hope the list is as long as the one you saw before.

---

### Post by nothingspecial on 2010-09-10
At the console

```
sudo less /var/log/apt/term.log
```

That will show you what you`ve done and hopefully you will be able to fix it

---

### Post by ranch hand on 2010-09-10
In that case I would return to recovery and use the "root with network" option and;
```

apt-get update

```
even though what you did probably has it up to date and then;
```

apt-get install ubuntu-desktop

```
If it returns that this is already installed;
```

apt-get install --reinstall ubuntu-desktop

```
and then;
```

dpkg --configure -a

```
and;
```

dpkg-reconfigure -a

```
Hopefully that will set things back where they should be.  If not I am stumped too.

---

### Post by x C0MMAND0 x on 2010-09-10
The problem is I'm at my University right now and it requires a login in order that the Internet may be used...so even if I connect via ethernet port I can't login to the website with my credentials and authenticate the session, so I guess I will have to wait until I am at home before I can go into recovery with root network access...

---

### Post by nothingspecial on 2010-09-10
Unless there is some free wifi somewhere near

```
ifconfig wlan0 up
iwconfig essid *network_name*
iwconfig key *passphrase*
dhclient
```

---

### Post by x C0MMAND0 x on 2010-09-10
> **nothingspecial said:**
> Unless there is some free wifi somewhere near

```
ifconfig wlan0 up
iwconfig essid *network_name*
iwconfig key *passphrase*
dhclient
```

There is a wireless network availible which is unsecure, but after you connect and try to go to a webpage it redirects you to a website where you have to enter in a username and password, and then you can browse the internet, which normally isn't an issue, but I don't know A) how to connect to that wireless network (name is UofM) and B) once I am "connected" how I would enter in my University username and password in order to be able to run the commands I need to, so I guess I will have to wait until I get home (unfortunately that is about 4 hours from now)

---

### Post by nothingspecial on 2010-09-10
> **x C0MMAND0 x said:**
> There is a wireless network availible which is unsecure, but after you connect and try to go to a webpage it redirects you to a website where you have to enter in a username and password, and then you can browse the internet, which normally isn't an issue, but I don't know A) how to connect to that wireless network (name is UofM) and B) once I am "connected" how I would enter in my University username and password in order to be able to run the commands I need to, so I guess I will have to wait until I get home (unfortunately that is about 4 hours from now)

I don`t think Ubuntu comes with a text browser, so you maybe out of luck.

elinks (a nice easy one) is always in the list of packages I install first.

My thinking, if I trash my system, which I have done, away from home, I can still access the web.

---

### Post by x C0MMAND0 x on 2010-09-10
> **ranch hand said:**
> In that case I would return to recovery and use the "root with network" option and;
```

apt-get update

```
even though what you did probably has it up to date and then;
```

apt-get install ubuntu-desktop

```
If it returns that this is already installed;
```

apt-get install --reinstall ubuntu-desktop

```
and then;
```

dpkg --configure -a

```
and;
```

dpkg-reconfigure -a

```
Hopefully that will set things back where they should be.  If not I am stumped too.

Thank you!  I love you in a complete plutonic strictly thank you for fixing my computer kind of way.  I am posting this from within Ubuntu as it is fixed!

---

