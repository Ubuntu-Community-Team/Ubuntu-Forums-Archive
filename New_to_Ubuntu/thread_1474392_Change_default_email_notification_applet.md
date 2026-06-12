---
title: "Change default email notification applet?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by spydeyrch on 2010-05-06
Hey guys, using ubuntu 10.04 x64 and loving it. I just want to change something and am not sure how to go about doing it. I don't like evolution and prefer thunderbird. I have installed thunderbird 3.0 and uninstalled evolution. Now, I have that envelope icon up in my notification area and I would like to like thunderbird to it just like evolution was before. I have my thunderbird accounts setup just fine and can access them via the thunderbird program.

The attached image should give you an idea of where I am looking at. Also, I don't need to change me defualt email client, as I only have one right now: thunderbird. What I need to change is the email notification applet and have it point to thunderbird. Thanks guys!!

-Spydey :lolflag:

---

### Post by nitstorm on 2010-05-06
Maybe [this]("http://ubuntuforums.org/showthread.php?t=301520") could help?

---

### Post by spydeyrch on 2010-05-06
> **nitstorm said:**
> Maybe [this]("http://ubuntuforums.org/showthread.php?t=301520") could help?

Thanks for the link but not exactly what I am looking for. I already know how to make the default app Thunderbird. But thanks! :p

What I need is either one of two things:

1.) make the email/envelope part of the applet go away completely, along with the chat bubble, the one over to the right (right next tot he shutdown/log-off/lock screen, etc. button). If I am going to send an email (without the email applet working the way I want it to), then I will just start it via my quick launch buttons. If I want to chat, I will do it by either the terminal or a keyboard shortcut, not by that annoying little chat bubble in the notification area. Also, if I want to check my facebook page, I will go through a web browser and not through gwibbler. I only check my facebook page like once every 9 months, seriously!

2.) If I can get the email/envelope applet to work correctly, then that would be great. But I still want to get rid of the chat bubble to the far right.

-----------

Things that I have tried and haven't resolved the issue so far:

I uninstalled evolution. The email/envelope icon was still present, still gives me three options: chat, email, social accounts. The chat and social accounts worked but the email didn't and I can't not find an options menu anywhere to link that email option, to thunderbird. If evolution is installed and I click it, it opens evolution, not thunderbird, even if thunderbird is set as my default email program. Also, if I uninstall evolution, the chat bubble menu, the one to the far right, still shows the email, chat, social accounts, and ubuntu one options, which I don't need because I don't use that little menu, I think it is a waste of space.

If I uninstall gwibbler, then in both the email/envelope applet and the chat bubble menu, only the chat option is available (in the chat bubble, ubuntu one is also available).

If I unlock and remove from panel the email/envelope, it also gets rid of the sound/speak icon, because they are linked to the same applet. Reason being that the email/envelope icon and the sound icon are part of the notification applet and if I try to remove the email part, the system thinks I want to remove the entire applet, not just the email part. Also, if I try to remove the chat bubble menu from the panel, it also gets rid of the user menu, because they are all built into one single applet, the user applet (I don't remember the exact name and I can't look it up as I am at work right now.) The user applet give us the shutdown, log-off, restart, lock screen, etc. options.

-------
So that is where I am at right now. Do you see my dilemma? My ideal results would be to get rid of both the envelope and chat bubble all together but any attempts at doing so via removing them from the panel also gets rid of the sound icon and the user icon, which I don't want.

Any ideas would be great!! Thanks a ton and sorry for the long post.

So what do you think?

-Spydey :lolflag:

---

### Post by tad1073 on 2010-05-06
> **spydeyrch said:**
> Hey guys, using ubuntu 10.04 x64 and loving it. I just want to change something and am not sure how to go about doing it. I don't like evolution and prefer thunderbird. I have installed thunderbird 3.0 and uninstalled evolution. Now, I have that envelope icon up in my notification area and I would like to like thunderbird to it just like evolution was before. I have my thunderbird accounts setup just fine and can access them via the thunderbird program.

The attached image should give you an idea of where I am looking at. Also, I don't need to change me defualt email client, as I only have one right now: thunderbird. What I need to change is the email notification applet and have it point to thunderbird. Thanks guys!!

-Spydey :lolflag:

here you go...

[http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html)

---

### Post by spydeyrch on 2010-05-06
> **tad1073 said:**
> here you go...

[http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html)

After looking at the link and the cli commands, I think that this will do it! Thanks a ton!!

Now, any idea on how I can get rid of the chat bubble on the right? Or possible do the same thing to it as to the envelope (i.e. as in what the link shows how to do)? Thanks a ton!

-Spydey :lolflag:

P.S. I will have to try this once I get home from work.

---

### Post by tad1073 on 2010-05-06
> **spydeyrch said:**
> After looking at the link and the cli commands, I think that this will do it! Thanks a ton!!

Now, any idea on how I can get rid of the chat bubble on the right? Or possible do the same thing to it as to the envelope (i.e. as in what the link shows how to do)? Thanks a ton!

-Spydey :lolflag:

P.S. I will have to try this once I get home from work.

right-click>remove from panel

---

### Post by spydeyrch on 2010-05-06
> **tad1073 said:**
> right-click>remove from panel

Yeah, I tried that one already. If I use the "remove from panel" option, it removes the entire applet, not just the chat bubble. So that means that my user menu (shut down/logout/change user/etc.) goes with it too as it seems that both are integrated into the same applet. I wish I could separate them, that would be nice. I really don't like all this default social/broadcasting stuff. If I wan't to let some know what I am thinking, I will email them or call them. If I want to use this broadcast stuff, I will install it. But I really don't want it as default.

But thanks for the suggestion.

Any other ideas for getting rid of the chat bubble? By the way, that is my own personal unofficial name for that menu. I don't like it!!!

-Spydey :lolflag:

---

