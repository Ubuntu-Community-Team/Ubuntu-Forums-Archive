---
title: "ubuntu suddenly restarts"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by rhuea on 2009-01-17
Another bug that was caught during the update in intrepid, my desktop suddenly restarts. what could be causing this?

---

### Post by aesis05401 on 2009-01-17
What are you doing when it restarts?  

Do you mean that everything goes away and comes back without a power cycle on the box, or does the whole computer power cycle?

---

### Post by doas777 on 2009-01-17
check your system logs for sign of an error. if there is no error, then it is likely a hardware problem, although kernel corruption could cause this kind of "black screen" shutdown.

Check your CPU and system temperatures, and unplug any unused peripherals that might be sucking power from the PSU. 

if you notice that the shutdown is tied to a particular kind of activity, then that may be a clue. a guy I know had problems about 20 min after surfing the web repeatedly. a new NIC fixed the problem.

good luck,
Franklin

---

### Post by rhuea on 2009-01-18
it just logs out, goes back to the login screen. i do not have that many periphals attached to my laptop. this started to happen after i updated my intrepid. I also have several other problems like my headset and external speakers stopped working (which is still unresolved), and my wireless was not disabled, which is now fixed.

---

### Post by doas777 on 2009-01-18
it logs you out? that is funny. disregard my post; your problem is definetly software. you may wanna check your auth.log for the last command run.

anyway, good luck

---

### Post by aesis05401 on 2009-01-18
> **rhuea said:**
> it just logs out, goes back to the login screen.

This is actually your windowing manager restarting.  This is probably a problem in you X configuration.  

You might start by checking your driver situation.  Maybe whatever upgrade you performed overwrote something?

Just to be clear... did you upgrade to Intrepid (if so, from what) or did you simply perform a package update in Intrepid?

EDIT: You might run this: sudo dpkg-reconfigure xserver-xorg

I don't know of any horrific side effects if this process fails so long as you back up your current config file before reconfiguring.  Someone more educated might jump in with advice, though.  You might want to google that sudo command for more instructions as many problems like the one you are describing seem to be solved in the X config.

---

### Post by rhuea on 2009-01-18
oh my, is this command safe? i've been using ubuntu for quite some time now and im afraid to loose my settings. is there an easier way? i upgraded to intrepid from hardy, but all problems started when i updated intrepid.

---

### Post by aesis05401 on 2009-01-18
> **rhuea said:**
> oh my, is this command safe? i've been using ubuntu for quite some time now and im afraid to loose my settings. is there an easier way? i upgraded to intrepid from hardy, but all problems started when i updated intrepid.


I would attempt to reapply any restricted drivers before running the command.  Then restart X manually with CTRL+ALT+BKSPC.  

If it bonks out again then ...  I see advice to run the reconfiguration just to see if it works so it shouldn't be too gnarly ;)  If you nano the xorg.conf you will see it is fairly straightforward.

I am told that backing up /etc/X11/xorg.conf secures you against disaster as you can get right back to where you are now by copying the backup back into place from a command line if X will not load at all.

Edit: hold on, I will try it right now :)

---

### Post by aesis05401 on 2009-01-18
OK, I not only tried it, but I have a new bug to report to someone :)

First I backed up my xorg.conf : 
```

sudo cp /etc/X11/xorg.conf ~/xorg.conf.knowngood

```

Then i ran the reconfiguration : 
```

sudo dpkg-reconfigure xserver-xorg

```

Aside from the first prompt (kernel framebuffer = no), I accepted all the defaults... And everything was fine. 

So the reconfigure process was nothing too scary, I just had to read the screens before each option, because I was unfamiliar with the terms in play.

To continue the experiment I intentionally fracked my xorg.conf and hit ctrl+alt+backspace. X offered to restore to a backup and failed, then offered a default configuration which got me into a loop of clicking 'OK' on boxes that just led back to the same starting point (I don't know if the loop was infinite as I didn't stick around that long ;) ) 

Never fear, yo, ctrl+alt-F2 from the fracked X screen got me a login prompt.

```

sudo cp ~/xorg.conf.knowngood /etc/X11/xorg.conf
sudo shutdown -r now

```

Good as new.

I could probably have hit alt+F7 to get out of the terminal, restarted X with ctrl+alt+backspace and been golden as well.

Long story short the worst that can happen is you are back where you started.

Edit: I should mention that your customised desktop settings don't live in X to the best of my knowledge... so the only danger in reconfiguring X is that you no longer reliably get a display or can't display at the proper resolution when in windowing mode.  Your terminal should always be available and a few keystrokes unwinds everything...

---

### Post by doas777 on 2009-01-19
just as an aside, in intrepid, 
```
dpkg-reconfigure xserver-xorg
```
doesn't seem to do much, except empty your xorg.conf of most of it's settings. Intrepid uses a new version of X11 that does not use the xorg for hardware info. all of it is autodetected. you can see the auto-detection information in the xorg.0.log if you so choose.

good luck,
franklin

---

### Post by rhuea on 2009-01-19
i've already tried to reconfigure it, doesnt say much about windowing or anything. just a bunch of keyboardstuff. I still didn't have the time to time trial my ubuntu now, but i hope it will not restart (go back to login) all of a sudden.

---

### Post by rhuea on 2009-02-05
Hi guys, after some time of observing, my laptop still automatically logs out. specially if im doing multiple tasks. how can i fix this. my external speakers is also still not working.

---

