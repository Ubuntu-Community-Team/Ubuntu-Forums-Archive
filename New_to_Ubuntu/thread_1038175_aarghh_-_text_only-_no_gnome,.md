---
title: "aarghh - text only- no gnome,"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by plasmarox on 2009-01-12
Hiya, ive clearly done something fairly wrong, and done something thats buggered me up a bit.

When i turn my nb100 on, select windows, etc, ubuntu boots, BUT:

Gnome does not load, and i only get the terminal, as if the terminal was just full screen.

Earlier today, a friend of mine (Jammy) showed me how to get gnome back by typing something like:

```
 sudo c* 
```

I can't, however, remember the command!

Any ideas, and if so, how can i get gnome back everytime without doing this command?

Ta.

---

### Post by taurus on 2009-01-12
What happens if you run this command from a prompt after you've logged in with your username and password?

```
startx
```

---

### Post by ugm6hr on 2009-01-12
> **plasmarox said:**
> Hiya, ive clearly done something fairly wrong, and done something thats buggered me up a bit.

When i turn my nb100 on, select windows, etc, ubuntu boots, BUT:

Perhaps a little detail about what you were doing before this happened.

Have you just installed?  Or recent updates?

It appears that your Grub is pointing to the wrong place.

Was Gnome working before?

---

### Post by plasmarox on 2009-01-12
Aha, almost perfect!

When gnome appears, it says:
```
Applet user switcher has quit unexpectantly.
load / reload

```

As a consequence of that, my logout button has disappeared form the top-right corner (:s)

What can i do about this?

Why does it boot into terminal mode then?

Is there any way i can change this?

Sorry for all the questions :D

---

### Post by taurus on 2009-01-12
You probably need to reload GDM login screen again.

```
sudo /etc/init.d/gdm start
```
And if you want to add a logout button to your top panel, place a cursor on it and click the right button.  Then, go into Add to Panel... and look for the Log Out... option on the list.

---

### Post by plasmarox on 2009-01-12
@ugm6hr

Sorry, such a nub i am, didn't spot your reply! :D

I was trying to get my atheros wireless driver to work, and one day i turned it on and this thing happened. :@

Oddly enough, the wireless works flawlessly now XD

@taurus

Yes, ive done that :P

How do i get gnome to startup when i boot the computer up?

:@

---

### Post by taurus on 2009-01-12
Try rebooting and see what happens.

---

### Post by plasmarox on 2009-01-12
@taurus

I have, its just the same.

---

