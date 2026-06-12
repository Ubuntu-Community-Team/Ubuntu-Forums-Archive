---
title: "Window decorations disappear constantly"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Jamppi on 2010-05-25
My Ubuntu has an annoying problem: after every few or more days when I log on, all of the windows start border-less. I then have to Google and fix it, but it never stays that way for long. 

Often it happens after the laptop has been in suspended state. I wonder if there is a connection?

Nevertheless, I am beginning to lose hope.

Picture:

[IMG]http://i783.photobucket.com/albums/yy119/evore1911/Screenshot.png[/IMG]

---

### Post by isaacj87 on 2010-05-25
What are you doing to fix it?

It sounds like Compiz is failing to start on boot/log in. I had this problem recently and just forced Compiz to start up automagically on log in.

---

### Post by Jamppi on 2010-05-27
> **isaacj87 said:**
> What are you doing to fix it?

It sounds like Compiz is failing to start on boot/log in. I had this problem recently and just forced Compiz to start up automagically on log in.

Usually the problem goes away when I reboot, (it starts with borders) but it is an annoying problem... never had this problem in Karmic.

I'd like to get rid of this problem.

---

### Post by wojox on 2010-05-27
You did the usual and checked in ccsm that the Window Decorations plugin was checked?

---

### Post by Jamppi on 2010-05-31
> **wojox said:**
> You did the usual and checked in ccsm that the Window Decorations plugin was checked?

Yes. This is as I opened it, I did not modify anything.

Only thing is that, every time this bloody thing happens, I open "Change Desktop Backround" and choose "Visual Effects" , it has all three options unchecked. When I choose Extra, nothing happens, except it unchecks Window Previews, Screenshot and few other options. I always have to recheck them.

Then I restart.

[IMG]http://i783.photobucket.com/albums/yy119/evore1911/Screenshot-1.png[/IMG]

---

### Post by Legendary_Bibo on 2010-05-31
It happens to me half the time I boot up. If you have the compiz fusion icon (which you should get if you don't after this ordeal) you can right click and click on 'reload window manager'

If not open terminal and type this in or copy and paste

```
compiz --replace
```

If that doesn't do anything you'll have to revert to metacity then change it back to compiz

```
metacity --replace
```

---

### Post by Jamppi on 2010-05-31
After I choose Extra on the Visual Effects and restart, the borders are back on, but all of my previous settings are gone.

I have to go through the process of setting them again every 3 days.

Is there a solution, please?

[IMG]http://i783.photobucket.com/albums/yy119/evore1911/Screenshot-2.png[/IMG]

[IMG]http://i783.photobucket.com/albums/yy119/evore1911/Screenshot-3.png[/IMG]

---

### Post by Jamppi on 2010-05-31
> **Legendary_Bibo said:**
> It happens to me half the time I boot up. If you have the compiz fusion icon (which you should get if you don't after this ordeal) you can right click and click on 'reload window manager'

If not open terminal and type this in or copy and paste

```
compiz --replace
```If that doesn't do anything you'll have to revert to metacity then change it back to compiz

```
metacity --replace
```

I will try that next time his happens.... I'll post the results here.

Thx for advice!

---

### Post by Legendary_Bibo on 2010-05-31
> **Jamppi said:**
> After I choose Extra on the Visual Effects and restart, the borders are back on, but all of my previous settings are gone.

I have to go through the process of setting them again every 3 days.

Is there a solution, please?

[IMG]http://i783.photobucket.com/albums/yy119/evore1911/Screenshot-2.png[/IMG]

[IMG]http://i783.photobucket.com/albums/yy119/evore1911/Screenshot-3.png[/IMG]
Yeah it happens to me too when I turn off the effects. Did you try my suggestion? Also you can attach photos so that we don't have to look at the big images across our screens.

---

### Post by realzippy on 2010-05-31
Great,I am not alone!
Had this issue on 2 Lucid machines,both 195.36.15+compiz+emerald.Sometimes also gnome panels not loaded...
Amazing randomness;sometimes it works,sometimes autostart workarounds are ignored.Weird...

Disabling *autologin* solves this problem here,on both machines.

---

### Post by ElSlunko on 2010-05-31
Same issue here but I think mine stems back to karmic. Anywho, compiz --replace fixes it for me.

---

### Post by Jamppi on 2010-05-31
> **realzippy said:**
> Great,I am not alone!
Had this issue on 2 Lucid machines,both 195.36.15+compiz+emerald.Sometimes also gnome panels not loaded...
Amazing randomness;sometimes it works,sometimes autostart workarounds are ignored.Weird...

Disabling *autologin* solves this problem here,on both machines.

I am not using autostart. I made 2 accounts, one for me and the other for my wife. This BS usually happens when she is logged in, I log her out and log myself in. Then it Ubuntu starts without the decorations. Then I have to fiddle with the settings, check Extra, then restart and put all of the settings again until next time.

Karmic was much more stable... good thing I didn't upgrade my work pc to Lucid, I'd have lost my mind by now.  :guitar:

---

### Post by ElSlunko on 2010-05-31
> **Jamppi said:**
> I am not using autostart. I made 2 accounts, one for me and the other for my wife. This BS usually happens when she is logged in, I log her out and log myself in. Then it Ubuntu starts without the decorations. Then I have to fiddle with the settings, check Extra, then restart and put all of the settings again until next time.

Karmic was much more stable... good thing I didn't upgrade my work pc to Lucid, I'd have lost my mind by now.  :guitar:

Takes 2 seconds to type compiz --replace. I do it with gnome-do. Could try it with alt+f2. Yeah it's not an excuse but just memorize the simple command so you don't have to google it next time.

---

### Post by realzippy on 2010-05-31
I have *compiz --replace* in autostart (needed for FSAA to work btw.)
Yesterday again lost borders.Added emerald --replace (anyway loaded in ccsm,but who knows these days) -in karmic no probs- and it seemed to work...
Today again,no window decorator loaded...  :confused:
Disabled autologin seems to help,*Jamppi* discouraged me,we will see.

So which video driver/window decorator are you all running?2.6.32-22-generic?

---

### Post by launchy on 2010-05-31
if u have ubuntu tweak installed try going to session control and replace gnome-wm with compiz --replace. And make sure under window management everything under window decoration and compositing manager (ubuntu tweak as well) is unchecked.

---

### Post by Jamppi on 2010-06-03
compiz --replace   works.

Thanks.

---

### Post by Derspankster on 2010-06-05
I'm affect as well but only occasionally. I may boot a dozen times successfully but then have it happen. I have the Compiz Fusion icon installed so I simply reload the GTK window manager from there. But, it is annoying. 

I autologin. have not tried turning that off but as it such a random issue it might take me awhile to confirm that manually logging on is a fix.

---

### Post by Frogs Hair on 2010-06-05
I had a slight problem with this when using Emerald . Emerald has a known bug in 10.04 so I removed it until  
it is more stable . Many people are having this problem without using Emerald , so I think I just got lucky.

---

### Post by nekr0z on 2010-10-13
I have this behaviour since upgrade to Maverick. No autologin, no emerald, nothing. compiz --replace obviously helps, but is there a way to fix this thing once and forever, please?

---

### Post by yurx cherio on 2011-05-31
To fix the problem I do this. I go to Compiz configuration and uncheck "Windows Decorations" then wait a few seconds then check it back.

It is very annoying.

---

### Post by Fercho on 2011-07-22
> **yurx cherio said:**
> To fix the problem I do this. I go to Compiz configuration and uncheck "Windows Decorations" then wait a few seconds then check it back.

It is very annoying.

Try restoring to default the option "Command" in "Windows Decorations". I was having the same problem after upgrading to Ubuntu 11.04 and I restored that option (default is /usr/bin/compiz-decorator ) and borders do not disappear any more.

You've probably solved this already, but maybe this helps somebody else.

---

### Post by sturdy on 2011-07-25
I'm having a similar problem...when I boot I have no window decorations, top title bar or window borders, and strange behavior. This first began immediately after install of 11.04 with the classic desktop but was okay with Unity. Yesterday my Unity was trashed so I reverted to the classic desktop and found this thread. If I run compiz --replace, the missing windows items are replaced but fails again on reboot. Here seems to be the problem: When I run compiz --replace this message is left in the terminal...

"Couldn't find a perfect decorator match; trying all decorators
Starting unity-window-decorator" 

Any ideas? Thanks in advance.

---

### Post by megaDee on 2012-03-14
Hi,

I have the same problem. I manage to bring it back by typing unity --reset but the problem keeps coming back. I have the feeling it occurs especially when using Firefox (11) and opening pop-ups but this might be just perception.

11.10 auto upgraded from Ultimate Edition 2.8, not autologin, CompizConfig, no Emerald

Any ideas? Even radical ones like reinstalling my Ubuntu?

--m

---

Edit: I tried the suggestion by [Fercho]("http://ubuntuforums.org/member.php?u=119118") and I think it works. So far the window decorations didn't disappear.

---

