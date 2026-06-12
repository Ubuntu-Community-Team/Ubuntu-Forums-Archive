---
title: "Short Freezes in Hardy"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by MercurySwitch on 2009-04-18
I have been searching for solutions to this problem on the ubuntu forums and on google.  If another thread exists please let me know.  

I upgraded to Hardy Heron about one week ago.  From the start every few minutes my computer freezes for about 1-5 seconds.  My system resources monitor shows my cpu reaching 100% use spikes.  I will remain connected to my network but the internet will stop, usually requiring I re-connect to my home network to get internet back.  This problem occurs when I stop typing or using the mouse for a short period, but will happen every 5 minutes regardless of use.  The freezes do not require me to reset or restart my computer, as most of the random freeze threads I've found discuss.  

If there are contents of any files or processes that I should list, please include a description of how to obtain the information, as I'm pretty new to linux.

---

### Post by rucadulu on 2009-04-18
If you can open a terminal window, it is under applications -> accessories. Then type in top, then do nothing on your pc and wait for the freeze to happen. When it happens hit printcreen  and post the screen shot or write down the top four or five processes shown by top. Post this to this thread as this well help me determine what might be causing the problem.

---

### Post by MercurySwitch on 2009-04-21
Alright, after extensive testing it seems this problem occurs when firefox is running.  I tested it for days as I know this problem has occurred outside of firefox before, but I believe I had been running firefox at least at one point during the sessions.  

I am going to test with another browser shortly and see if it's solely firefox or any browser that leads to this problem.

---

### Post by rucadulu on 2009-04-21
Good to see you are isolating the problem, let me know what you discover.

---

### Post by MercurySwitch on 2009-04-22
Alright, the problem still occurs with epiphany.  

I was having problems with this using update manager, but when my browser wasn't running the update manager seemed to work fine. 

Running top during crashes, last items listed:

firefox
xorg
kondemand


firefox
xorg
top


firefox
xorg
multiload-apple

---

### Post by Yashiro on 2009-04-22
Which plugins do you have installed for Firefox?

---

### Post by rucadulu on 2009-04-22
Have you tried uninstalling firefox and then reinstalling it? You most like have to use apt or synaptic package manger to remove firefox.

---

### Post by hansdown on 2009-04-22
There is a kernel bug.

[http://www.google.ca/search?q=kondemand&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=kondemand&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Not sure if this is helpful.

---

### Post by MercurySwitch on 2009-04-24
Not sure how to read the kernel bug information.  If you could explain what it said I would be grateful.  

This problem now occured while using Evice document viewer and no browser.  However, the browser had been active earlier in this session so I'm not sure if it's something that loaded at that time or not.

---

### Post by hansdown on 2009-04-24
I would need a brain transplant to understand that stuff.

Have you considered if this could be a hardware issue?

Could you post your system specs?

---

### Post by MercurySwitch on 2009-04-24
Acer Aspire 5610
Intel Dual Core 1.7gHz
2 Gb DDR RAM

If you could tell me how to find additional specs I will post them.  

I'm starting to wonder if this could be wifi-card related.  I had some problems with network manager on 7.10.

---

### Post by hansdown on 2009-04-24
I think I have your specs.

Hardware looks good.

Can you check system> preferences> power management?

See if the settings are set oddly.

---

### Post by MercurySwitch on 2009-04-24
Thanks for looking that up.  Looks dead-on.

---

### Post by MercurySwitch on 2009-04-24
AC Power
Actions
Sleep on inactive: Never
Lid closed:  Blank Screen
Display
Display sleep when inactive:  40 Minutes
Dim Display:  Unchecked

On Battery
Actions
Sleep on inactive:  Never
Lid closed:  Blank Screen
Power Critically Low:  Shutdown
Display
Display sleep when inactive:  15 Minutes
Reduce Backlight Brightness:  Checked
Dim Display:  Checked

General
Actions
Power Button:  Ask Me
Suspend:  Suspend
Notification Area
-Always display an icon
Extras
Use sound for error notification:  Checked

---

### Post by hansdown on 2009-04-25
Have these problems happened when you are on battery?

Power Critically Low: Shutdown.

May be a pointer.

---

### Post by MercurySwitch on 2009-04-26
Because it's a problem across multiple browsers, could it flash or java related?

---

### Post by hansdown on 2009-04-26
> **MercurySwitch said:**
> Because it's a problem across multiple browsers, could it flash or java related?

I've never seen that. There have been problems with the system monitor taking up alot of cpu.

Try uninstalling it, Just for a test.

[https://bugs.launchpad.net/ubuntu/hardy/+source/libgksu/+bug/206583](https://bugs.launchpad.net/ubuntu/hardy/+source/libgksu/+bug/206583)

---

### Post by MercurySwitch on 2009-04-26
Well, now the freeze happened when I started my computer and left it idle.  Logged in, but had not activated any program, although gnome-swallow mysteriously starts with boot now.

---

### Post by hansdown on 2009-04-26
Gnome-swallow has been known to be unstable.

[https://launchpad.net/ubuntu/+source/gnome-swallow](https://launchpad.net/ubuntu/+source/gnome-swallow)

---

### Post by MercurySwitch on 2009-04-26
Yeah, I ran it once yesterday as I didn't remember its function.  Since then it starts upon login.

---

### Post by HermanAB on 2009-04-26
Howdy,

One of the reasons for this problem is a bad CDROM device driver.  One of my PCs suffer from it. Unplug your CDROM cable and see whether the problem goes away.

---

### Post by MercurySwitch on 2009-04-26
Is there a way I can disable the DVD-RW or its driver without unplugging it?  I'm on a laptop.

---

### Post by HermanAB on 2009-04-26
You can try stopping the haldaemon service.  That should make the freezes go away.

```
ls /etc/init.d
```

then

```
sudo invoke-rc.d servicename start|stop
```

which is only a shortcut to

```
sudo /etc/init.d/servicename start|stop
```

---

### Post by MercurySwitch on 2009-05-16
I could not get the haldaemon service to stop.  It said service not found.  

The problem has now escalated to freezing when my computer is idle for just 20 seconds, which means that any pause to read a web page leads to a disconnect from the internet.  

I really don't know how to fix this, but it's making it near impossible to use the internet.  And the lag that happens every time the computer has to 'wake up' is infuriating.

---

