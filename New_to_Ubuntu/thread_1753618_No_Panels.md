---
title: "No Panels"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-05-09
I have installed 11.04.

When I use classic setting everything works OK, but, when I switch to unity setting all I get is my desktop with no panels showing.

---

### Post by anaconda on 2011-05-09
What panels do you mean..  Unity doesn't have traditional panels. It only has the "launcher" on the left and unitys own top "panel".
 
did you know that you can start gnome-panel even when in unity?

just press Alt-F2 and type 
gnome-panel
and enter.

---

### Post by Robert1305 on 2011-05-09
Hi thanks for the reply.

I have nothing but my background pic showing, no launcher, no panel, no nothing .:confused:

---

### Post by pinballwizard on 2011-05-09
> **Robert1305 said:**
> Hi thanks for the reply.

I have nothing but my background pic showing, no launcher, no panel, no nothing .:confused:

So, you mean you have the perfect unity desktop? When you figure out how you did it, please let us know.

---

### Post by Robert1305 on 2011-05-09
> **pinballwizard said:**
> So, you mean you have the perfect unity desktop? When you figure out how you did it, please let us know.

Does this mean you do not like Unity. :)

---

### Post by fabricator4 on 2011-05-09
> **Robert1305 said:**
> Does this mean you do not like Unity. :)

One in four don't seem to like Unity.  One in four love it. The other half can't decide.  This is the perfect 1:1:2 spread of responses you will get if you ask any yes/no question of a large enough sample of humanity.

It seems you are having a perfect day. :-)

I'm in the first group btw.

If you want to use the old style Gnome desktop, when you get to the login screen click on your login name, then down the bottom panel select 'Ubuntu Classic'.

I've heard of a few people having the same problem as you (no launcher, no panel, no joy) but I'm not sure if anyone has found the solution.  It seems that the launcher application is not starting for some reason.  You could try looking in the logs for error messages, and Google for the problem - I found several bug reports in launchpad for this problem.

[This person]("http://ubuntuforums.org/showthread.php?t=1745485") had the same problem but found that Unity2d worked for them.  You'd probably have to apt-get Unity2d then reboot, then select Unity 2D on the login screen as above.

Chris.

---

### Post by TheNerdAL on 2011-05-09
Is unity 2D installed? Check synaptic.
Also check System Monitor to see if compiz is running.
Which 3D drivers have you installed?

---

### Post by fabricator4 on 2011-05-09
> **fabricator4 said:**
>  You'd probably have to apt-get Unity2d then reboot, then select Unity 2D on the login screen as above.


I should have said, Unity2D is buggy and leaks memory via the unity2d-places module.  The bug is marked critical and fix-committed, but as of right now the fix hasn't come through on any updates.

The kludge workaround is to kill the unity2d-places modules periodically.  The module will be re-started from scratch next time you search applications.

Chris.

---

### Post by Robert1305 on 2011-05-09
I can use 2d OK.

The new drivers message is that I have the latest driver and it is activated but not in use, being a total newbie not sure what this means.

And it says I need this to run unity. :confused::confused:

---

### Post by corncob on 2011-05-24
This just happened to me -- no top panel, no launchers on the side.  I couldn't open the terminal (ctrl-alt-t) or command line (alt-F2).  I pressed ctrl-alt-F1 to go to another terminal, logged in, and entered
```
unity --reset
```
After it finished I entered
```
sudo reboot
```
and everything seems to be back.  I guess I will have to stay out of ccsm as that's where it all started.

---

