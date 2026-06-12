---
title: "volume button"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by dzon65 on 2009-10-31
Does anyone know how to add a volume button(icon) to the panel in 9.10?

---

### Post by PorkyPie on 2009-10-31
Right-click on the panel, and click "Add to panel". Then, type "volume" in the search box, you'll see it there.

---

### Post by dzon65 on 2009-10-31
That's what it should do,but,it doesn't.It isn't in the list also.

---

### Post by humphreybc on 2009-10-31
The volume icon is now included in the "Notification Area" applet in Karmic, instead of having its own standalone applet.

You should be able to add that to your panel. If you do, and the volume still doesn't show up, then we've got a problem :)

---

### Post by dzon65 on 2009-10-31
Yep,you're wright.But,is there a way to get rid of that bluetooth icon?

---

### Post by humphreybc on 2009-10-31
You can go to System > Preferences > Startup Applications and disable bluetooth running at startup (if you don't use it).

I don't have bluetooth on my laptop, so I have never seen this icon.. I think the above should remove the icon but not sure.

If you feel confident, you can go into Synaptic Package Manager and have a look at removing some bluetooth packages... but, be careful, I know that there is one (bluez-gnome I think) that has a lot of dependencies. I think "ubuntu-desktop" might be one, which you certainly do NOT want to remove!

---

### Post by dzon65 on 2009-10-31
Yeah,could do that but I do use bluetooth.So,that's not an option.It's a bit strange though that the ubuntu-guys bundled those items.

---

### Post by humphreybc on 2009-10-31
Are you sure there isn't a setting somewhere in the bluetooth options regarding when to show the icon?

---

### Post by dzon65 on 2009-10-31
Not quite sure.You can turn bluetooth off,which will change the icon,but there will remain....an icon.Ah well,can't have it all.Thanks for the replies man.

---

### Post by humphreybc on 2009-10-31
Great Success!!

System > Preferences > Bluetooth

---

### Post by dzon65 on 2009-10-31
Yes.You can indeed turn it off.In the mean time I've tried to work with this bluetooth.It's a piece of c...Every time I wanna send or receive something another icon is added and I can't take it away unless I reboot.Used to have something in 8.10,worked like a charm but it's not available anymore.It was really easy to work with.One just had to click it once to send or receive through bluetooth.I've installed 9.10 yesterday and I'm having quite some issues with it.

---

### Post by dzon65 on 2009-10-31
What the f....!? I added my mobile to my bluetooth,opened files that are on my mobile and now all files are gone (on my mobile)!!!

---

### Post by Darce on 2009-10-31
Ouch !

Sure you didn't CUT and paste ?

---

### Post by dzon65 on 2009-10-31
Absolutely sure.This standard bluetooth is acting really weird.There are now several semi transparent icons on the panel.And,like I said,no way to delete them,except rebooting.
In 8.10 I used to have gnome bluetooth tools,which was really no-nonsense nice.A pitty it's no longer available.

---

