---
title: "A Sudden Improvement in Graphics - Why?"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-07-05
Hi all,

Computer Intel Core i7 2600, 4GB DDR3, 1TB HDD, Radeon HD 5770 HDMI

I am at present using Natty in Classic mode. I don't know what is going on but from time to time there is a sudden improvement in the clarity of the graphics. This typically occurs at the same time there is a change in the background picture. This improvement doesn't last however, when there is a change of user the graphics clarity reverts back to the rather dull (No Effects) style.

The same thing would happen when I was running Classic (No Effects) Mode.

Is there a way to retain the improved graphics permanently? They are a great improvement.

Footnote - I have just tried logging on to Unity and found that graphics (Except for those down the left side) were no better.  

Thank you - :P

---

### Post by OldBoy44 on 2011-07-05
Hi again,
Sorry about posting so soon, but should I try loading the Proprietary Driver ?
If so, do I need to disconnect the open source driver and if so how ?

Thank you, :)

---

### Post by grahammechanical on 2011-07-05
I do not remember ever disconnecting the open source driver. I just activate the recommended proprietary one. Things will most probably work better. I do not think the open source driver is sufficiently advanced to provided enhanced video effects.

Regards.

---

### Post by sandy8925 on 2011-07-05
when you say clarity you mean it becomes clearer? could be that for some reason the entire screen is being blurred by default? maybe it's some compiz setting?

---

### Post by OldBoy44 on 2011-07-05
Hi and thanks Graham and Sandy,

I loaded Proprietary Driver however unfortunately no change.

By improved clarity I mean all graphics become much sharper and clearer.

I have never played with compiz - I don't know how!

Thanks guys, :)

** Edit: Another thing - The symbols for such things on the Top Panel as log-out and Weather change.
     ie - from memory, log-out CHANGES to a walking figure. - I really am not going mad - I swear this really happens from time to time - I have searched high and low on the internet to no avail!
I have a strange feeling that I am dealing with a very unusual problem here, I will be surprised if I get a definitive answer!
I realize now that I should have taken a screenshot which I will do, if or when this strange (to me) occurrence happens again - I will then attach the screenshot to this thread.

---

### Post by OldBoy44 on 2011-07-14
Hi all,

Well it has taken a week to reoccurr but at last it has - now this may be normal graphics for 11.04 Classic, but can somebody explain the difference in the first two screenshots against the last two. I expect current graphics will disappear within half an hour. How can I have these graphics all the time in classic mode ? Have a close look at the differences some of which are -

1. Differences in files on desktop plus shape and color of mp3 files.
2. Dots on logon  more pronounced.
3. Differences in color and shape of icons in Top Panel.
4. Changed graphics Ub-1 to Ub-7
5. Improved general clarity.

Like I say, maybe I am a nut and these graphics are normal for Classic mode - If so, how do I get them permanently ?  Cheers,  :)

---

### Post by wildmanne39 on 2011-07-14
Hi, I think this link is what you need to get you fixed up.
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

---

### Post by OldBoy44 on 2011-07-14
Thanks a lot wildmanne39 - I feel a bit of a fool now! :)

---

### Post by OldBoy44 on 2011-07-14
Say wildmanne39, I don't know how to replace that line.

Do I simply enter as it is in the terminal ?
That is enter the three lines in terminal ?

Thank you.

---

### Post by wildmanne39 on 2011-07-14
> **aussiebean said:**
> Say wildmanne39, I don't know how to replace that line.

Do I simply enter as it is in the terminal ?

Thank you.Hi, open the terminal and copy and paste this into it.
```
gksudo gedit /etc/xdg/autostart/gnome-settings-daemon.desktop
```
That will open gedit go to this line Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
and replace it with Exec=bash -c "sleep 5; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"
then save and close gedit and restart.

---

### Post by OldBoy44 on 2011-07-14
wildmanne39 - You are a gentleman and a scholar - Many thanks -  :D

---

### Post by OldBoy44 on 2011-07-14
I don't know what I am doing wrong but get this error message -

```


(gedit:3045): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3045): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.L46DYV': No such file or directory

(gedit:3045): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3045): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.RMQ7XV': No such file or directory

(gedit:3045): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


```

I am set up for 6 users - 3 seem to work.

---

### Post by OldBoy44 on 2011-07-14
I tried altering some spaces and now none of users are in better graphic mode!  :(

---

### Post by wildmanne39 on 2011-07-14
Hi, you should have only needed to do that once and all users should have been fixed, as for changing spaces, as long as you know what you did change it back to the way it was when you had three users working. Did you restart your system after the change was made the first time?

---

### Post by OldBoy44 on 2011-07-14
Yes I did - not all users were working then.

I'll try again.

---

### Post by Quackers on 2011-07-14
I get those errors when saving gedits on fresh installs.
I run ```
sudo mkdir -p /root/.local/share
``` which quiets things down. After running that you may have to save the file you changed once again.

---

### Post by OldBoy44 on 2011-07-14
Thanks Quackers! :)

---

### Post by Quackers on 2011-07-14
No problem :-)
It plagues me with every new install of Natty and Oneiric - I thought it was just me :-)

---

### Post by OldBoy44 on 2011-07-14
It now at present works for four of the six users! :confused:

---

### Post by wildmanne39 on 2011-07-14
Hi, sorry I am out of ideas, but quakers is much more experienced then I am so he might have a solution.

---

### Post by OldBoy44 on 2011-07-14
No worries wildmanne39, I really appreciate your assistance! :D

---

### Post by OldBoy44 on 2011-07-14
New information -

I found that ALL  users were O.K. after being logged on for about 18 seconds!

Should I change the 5 in line to 20 ? or some other number ?

Thanks in advance. :)

---

### Post by wildmanne39 on 2011-07-14
Hi, you can try it, if needed you can always change it back.

---

### Post by Quackers on 2011-07-14
Sorry guys, I only have one user for a reason :-)
You lost me a few posts ago!

---

### Post by OldBoy44 on 2011-07-14
Hi Quackers and wildmanne39

Changing number from 5 to 20 resulted in 4 of the six users logging on to better graphics virtually straight away, with the other two improving after about 20 seconds. At least I am getting improved graphics - I can live with the delay unless you come up with anything else to try! I am rapt - thanks very much guys - :p

Perhaps I should mark as solved unless I hear from you shortly!

Thanks again guys - your help is very much appreciated!

---

### Post by wildmanne39 on 2011-07-14
Hi, glad to help but I am out of ideas on the rest of the users.

---

