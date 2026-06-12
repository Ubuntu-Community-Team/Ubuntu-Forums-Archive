---
title: "Black screen with cursor, after log in"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by cosmicappuccino on 2009-02-08
Hi,

I'm a complete newbie with Linux.
I tried to install Ubuntu on an HP PC that's about 5 years old. The installation seemed to complete successfully (I got a popup saying it had completed, and asking me to confirm restart). After restart, I got the login screen, so I entered my username and password. Then, the screen went black. There is a normal white arrow-shaped cursor on the screen, which moves normally when I move the mouse.

Any suggestions, please?
Thanks very much...

---

### Post by cosmicappuccino on 2009-02-13
Please, anyone with any ideas at all? :confused:

---

### Post by HQNUS on 2009-02-13
Can you try , press ctrl + alt + backspace, and this will close your x server. Then you should be asked to login again. Then have a look at whether it goes right.

---

### Post by sydbat on 2009-02-13
When you reboot, the grub menu should appear for a couple of seconds. If not, press ESC. Choose "Try to fix X server". Let it do its thing. It will let you know when to "resume normal boot".

Let us know if this fixes the problem.

EDIT - HQNUS's suggestion might work too. Try it first.

---

### Post by cosmicappuccino on 2009-02-13
Thanks for your replies!

I tried a few things, as a result of which I ended up not even being able to get to the login screen. So, I reinstalled completely, and now am back to the original problem of logging in and getting a blank screen with a responsive arrow cursor.

---

### Post by cosmicappuccino on 2009-02-13
HQNUS's suggestion: I tried hitting Ctrl+Alt+Backspace, but nothing happened. I don't know if it's of any significance that I'm using a Mac keyboard - but I tried Ctrl+Cmd+Backspace, Ctrl+Opt+Backspace, and Opt+Cmd+Backspace, none of which worked.

sydbat's suggestion: The grub menu does show up, but I am not sure where to find "Try to fix X server". Could someone help me find this, please?

---

### Post by sydbat on 2009-02-13
> **cosmicappuccino said:**
> HQNUS's suggestion: I tried hitting Ctrl+Alt+Backspace, but nothing happened. I don't know if it's of any significance that I'm using a Mac keyboard - but I tried Ctrl+Cmd+Backspace, Ctrl+Opt+Backspace, and Opt+Cmd+Backspace, none of which worked.

sydbat's suggestion: The grub menu does show up, but I am not sure where to find "Try to fix X server". Could someone help me find this, please?Sorry...I thought I had put that in my post, then realized I forgot to!:)

When grub comes up, choose "recovery mode"...Try to fix x server is in there.

---

### Post by cosmicappuccino on 2009-02-13
Thank you sydbat! Unfortunately I'm still having problems...

I've gone into recovery mode, but I can't find "Try to fix X server" -- or any options to choose from, for that matter! :(

When I chose recovery mode and hit enter, I got a black screen, across which a lot of white text was written. Now, it's stopped writing, and I'm stuck on a screen that starts with:

" 00 79 05 e8 b4 0a 00 00 5b " ...

and ends with:

" *Skipping firewall: ufw (not enabled) "

:confused: Any further help would be much appreciated!

---

### Post by sydbat on 2009-02-13
Maybe I missed a step. It has been awhile since I had to fix x server. Anyone know what step I may have missed?

---

### Post by cosmicappuccino on 2009-02-13
I think I have found a thread which describes exactly the same problem as mine. It looks like there is a workaround, but I don't understand how to implement it! It would be really helpful if someone could explain step-by-step...

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850)
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434)

Thanks a lot...

---

### Post by cosmicappuccino on 2009-02-13
This is someone's workaround for the problem:

> My temporary workaround:
"Alt-Ctrl-F2" , "Login" by Textmode. "sudo rm /tmp/.X0-lock" , "startx" then it starts up OK, after that i "Enabled Automatic Login", under "System-->Administration-->Login Window".
My comuptor: Dell Latitude D520
(Also tried xserver-xgl)

The first thing I'm not sure about is: when do I press Ctrl+Alt+F2 ? I've tried it a few times and nothing happens. Could someone explain, please?

---

### Post by taconi on 2009-02-27
> **cosmicappuccino said:**
> This is someone's workaround for the problem:



The first thing I'm not sure about is: when do I press Ctrl+Alt+F2 ? I've tried it a few times and nothing happens. Could someone explain, please?

Press Ctrl+Alt+F2 (or F1) after black screen

Altough deleting X0-lock didn't work for me.Try the following:
After black screen:
. Ctrl+Alt+F1
. login as admin
. insert command: ```
sudo /etc/init.d/gdm restart
```
Hope this work for you. Hope someone find a permanent solution for this

---

