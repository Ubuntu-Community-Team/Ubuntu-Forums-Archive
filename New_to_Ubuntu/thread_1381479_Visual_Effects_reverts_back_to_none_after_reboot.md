---
title: "Visual Effects reverts back to none after reboot"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by argrzankowski on 2010-01-14
I have the NVIDIA driver activated and can run Visual Effects on "Extras" for an entire session.  But after reboot, hibernate, suspend, etc. it reverts back to no selection at all, while the driver is still active.

Is there a way to keep this from happening? I know that my video card--integrated on dell latitude d800--can handle the 3D, I'm doing it right now.

Information: (pertinent/not)
Dell Latitude D800
1.3 GHz Celeron
NVIDIA GeForce4 4200 Go
1.25 GB Memory
(If you would like more info just ask)

Thanks in advance.

--argrzankowski

---

### Post by Joe325 on 2010-01-14
How did you install the driver? Have you had a look at [envy]("http://albertomilone.com/nvidia_scripts1.html")
Seems the settings arent set in your xorg file

---

### Post by dmillerct on 2010-01-14
> **argrzankowski said:**
> I have the NVIDIA driver activated and can run Visual Effects on "Extras" for an entire session.  But after reboot, hibernate, suspend, etc. it reverts back to no selection at all, while the driver is still active.

Is there a way to keep this from happening? I know that my video card--integrated on dell latitude d800--can handle the 3D, I'm doing it right now.

Information: (pertinent/not)
Dell Latitude D800
1.3 GHz Celeron
NVIDIA GeForce4 4200 Go
1.25 GB Memory
(If you would like more info just ask)

Thanks in advance.

--argrzankowski

Try some of the work arounds listed in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/441993]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/441993")

---

### Post by ThePantryMaster on 2010-01-14
Try this

I'm assuming you're using compiz fusion, so go to the software centre, and look for 'compiz fusion icon'
Install it
Then go to startup apps under preferences
Click add
then under command put
> fusion-icon

Having the fusion icon up there stopped the desktop effects from going away for me.  Hope it works for you!

---

### Post by argrzankowski on 2010-01-20
Thanks. Workaround worked around.

---

### Post by Elie-M on 2010-05-01
I can confirm this too. it worked for me thx. Man ubuntu is really bugged in 10.04.....

---

### Post by dakkar9999 on 2010-07-01
Had that problem when I tried to install Docky.  Still get an error message about composite, but it works!

Thanks!

---

### Post by kenkaku on 2010-07-10
I had this problem and resolved it [so far??] without using the instructions in the workaround. However, there was a clue in the original post from the workaround which helped me.
"Setting the Visual Effects in System->Preferences->Appearance  to Normal or Extra works OK until I log out.  When I log back in the  Visual Effects setting has returned to None, ie: it's **setting was not  saved with the session**." (My emphasis)

In hind sight, I think my problem was just that the setting from the session weren't saving.


**The way I fixed this was:**
1. Get everything set up the way you like it. [e.g. Visual Effects set to Extra etc.]
2. Now, navigate to *Applications > System Tools > Configuration Editor*. [I'm running 10.04]

3. Once it's up, expand */apps/gnome-session* and click *options.*
4. Click the check box in the Value column for auto_save_session.

5. Make sure no programs are running.  [Unless you haven't added them to Startup Applications and want them to start every time you log in.]
6. Reboot.
7. Uncheck auto_save_session. [Well, unless you *want* to auto save every time you log out.]


If you end up saving something nasty/broken [this]("http://www.stroobant.be/the-dangers-of-save-session-in-gnome") might help; though I haven't tried it.


This seemed like more work than it needed to be. If anybody knows a way to just force a session save directly, that may be the way to go.

[]("http://www.stroobant.be/the-dangers-of-save-session-in-gnome")

---

