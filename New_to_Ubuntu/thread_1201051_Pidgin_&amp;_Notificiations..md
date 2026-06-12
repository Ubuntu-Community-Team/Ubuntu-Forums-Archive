---
title: "Pidgin &amp; Notificiations."
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Doman on 2009-06-30
I'm using the Facebook Chat addon for Pidgin which is ungodly handy, but all these people I don't often talk to but can't unfriend on FB keep signing in and out and cause that notificiation in the top right corner of my screen.  Pidgin lacks so many features it's driving me up the wall.  I can't customize what notifications I get per person, group, or even account.  Nor I can't set it up so my arrow keys don't make that obnoxious sound whenever I go to far up or down, not to mention keep with my habit of expanding groups with them, which doesn't work either.  I'm also very fond of an "offline buddies" thing, since I have no idea where it's keeping my chatlogs.  & I found out with my windows version it wasn't even logging them when it said it was.

If anyone knows ways to fix any of the above, that'd be fantastic.  If not, how can I make that notification window appear smaller and potentially somewhere else?

Thanks,
Doman

---

### Post by VCoolio on 2009-06-30
"an offline buddies thing"?? If you mean you want your offline buddies listed in the buddy window set your prefs in Buddies > Show

For notifications go to Tools > Plugins > Libnotify Popups, select and hit configure. Not too many options but you can uncheck notifications for buddies signing on / off.

You can find logs in ~/.purple/logs

---

### Post by Doman on 2009-06-30
That just throws an extra 500 people into my buddy list to sort through.  AIM has an "Offline Buddies" group thing.  Does pidgin have a plugin?

& that's just notifications on or off.  I'm looking for customization.  If I could make it so just certain people, certain accounts, or even certain services were differentiated that would be ideal.

& Thanks.

---

### Post by soapytheclown on 2009-06-30
in terminal type
```
sudo aptitude install pidgin-extprefs
```

Within the plugins and from what I remember theres an ability to make certain contacts always shown in the list. (i think this is what you want)

the Notifications thing is brand new for jaunty so the ability to customize is quite limited right now. You can turn them entirely off by disabling the libnotify popup plugin though.

---

### Post by Doman on 2009-06-30
Actually, I already have that and all it does is add them to the same list on an individual basis.  I want, like aim has, a whole separate group for offline users.  Thanks though.

---

