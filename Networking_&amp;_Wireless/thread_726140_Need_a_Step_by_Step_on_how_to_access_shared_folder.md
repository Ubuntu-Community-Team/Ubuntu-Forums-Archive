---
title: "Need a Step by Step on how to access shared folders on a XP machine from Ubuntu"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by Ubobtu on 2008-03-16
Today I set up Samba on my Ubuntu machine.

[COLOR="Green"]**[SIZE="3"]I can access shared folders that are on my Ubuntu computer from my XP Pro computer just fine.[/SIZE]**[/COLOR]

[COLOR="Red"]**[SIZE="3"]I cannot access shared folders that are on my XP computer from my Ubuntu computer[/SIZE]**[/COLOR]. When I try to it will ask me for a password that I simply do not have, nor do I remember ever making one.

Now I have tried looking up this question on various sites, and the answers are not clear and are full of jargon that has made it totally confusing.

I am not an expert on Ubuntu or networking, so all Im asking is a simple step by step on how to do this:

[SIZE="4"]
How can I access those shared files on my XP computer from my Ubuntu computer without having to have a password. Or what is this password that is being asked for and where could it be found?[/SIZE]

Thanks for any help you can give.

---

### Post by EvilMarshmallow on 2008-03-16
I know it's elementary, but did you try just leaving it blank?  If you don't have an XP password set up you might get away with that.  Your User ID should be whatever name your account on the xp box uses (what appears on the "Welcome Screen" when you first boot your XP box?).  If you never, ever set up an account, even one with your name and a blank password, it's probably "administrator".  That's an incredibly unsafe, but unfortunately quite popular, thing to do.

Also you might want to check the permissions on the shared folders in XP.  On the security tab, make sure that one of the groups listed is "Everyone" and give it the access you desire.

---

