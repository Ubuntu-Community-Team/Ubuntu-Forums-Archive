---
title: "How do I close the black notification bubble?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by user1001 on 2010-05-26
Hi,
My question is already in the title :P
and also I don't know how to get the pidgin toaster notification thing to work, I checked the plugins but it wasn't there.

thanks.

---

### Post by Excedio on 2010-05-26
> My question is already in the title :PSelf-timed with no way to edit. But you can click through it like it's not there.


> and also I don't know how to get the pidgin toaster notification thing to work, I checked the plugins but it wasn't there.```
sudo apt-get pidgin-libnotify
```Go to plugins on Pidgin and enable. :-)

---

### Post by -humanaut- on 2010-05-26
I think all you have to do is click it. Do you want to disable it?

---

### Post by Excedio on 2010-05-26
> **-humanaut- said:**
> I think all you have to do is click it. Do you want to disable it?

Clicking it will not make it go away. It will fade out when the mouse hovers over it. Like I mentioned, you can click through it.

---

### Post by blchinezu on 2010-05-26
you can click through it.. can't actually close it
as for pidgin.. i recommend guifications... it's much more acurate than libnotify.. especially when there are more than 2 simultaneous notifications to display, it's also customizable (location, click action, skin, duration and others) install by: *sudo apt-get install pidgin-guifications* go to plugins (from pidgin) activate it and play with the options

---

### Post by user1001 on 2010-05-26
> **blchinezu said:**
> you can click through it.. can't actually close it
as for pidgin.. i recommend guifications... it's much more acurate than libnotify.. especially when there are more than 2 simultaneous notifications to display, it's also customizable (location, click action, skin, duration and others) install by: *sudo apt-get install pidgin-guifications* go to plugins (from pidgin) activate it and play with the options

Thanks for your suggestions =) guifications is good I'm using it now, but what do you mean by clicking through it

---

### Post by Merk42 on 2010-05-26
> **user1001 said:**
> Thanks for your suggestions =) guifications is good I'm using it now, but what do you mean by clicking through it

If there is something behind the notification, clicking the mouse will click whatever is behind the notification.

---

### Post by Excedio on 2010-05-26
> **user1001 said:**
> Thanks for your suggestions =) guifications is good I'm using it now, but what do you mean by clicking through it

Lets suppose you are viewing something that takes up your whole screen, and you have a notification bubble that appears below your system clock (upper right), but you need to click on something behind it. You do_not need to wait for the bubble to go away before clicking whatever is behind it. When your mouse hovers over the bubble it will fade slightly and you can "click through it."

Try it out.

Open a program that has some things that are click-able in the upper right portion of the window. Open a terminal and type this command:

```
notify-send "This Is A Notification Bubble" "Move The Mouse Over Me &  Click" -i /usr/share/icons/gnome/scalable/apps/im-yahoo.svg
```

---

### Post by user1001 on 2010-05-28
> **Excedio said:**
> Lets suppose you are viewing something that takes up your whole screen, and you have a notification bubble that appears below your system clock (upper right), but you need to click on something behind it. You do_not need to wait for the bubble to go away before clicking whatever is behind it. When your mouse hovers over the bubble it will fade slightly and you can "click through it."

Try it out.

Open a program that has some things that are click-able in the upper right portion of the window. Open a terminal and type this command:

```
notify-send "This Is A Notification Bubble" "Move The Mouse Over Me &  Click" -i /usr/share/icons/gnome/scalable/apps/im-yahoo.svg
```

Yes that's a nice feature but, what if i want it to completely disappear :S

---

### Post by oldos2er on 2010-05-28
> **user1001 said:**
> Yes that's a nice feature but, what if i want it to completely disappear :S

I uninstalled it because I don't care for its unconfigurability (if that's a word).

---

