---
title: "Changes made in gconf-editor not taking effect"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by de_island on 2011-04-23
I rather having my window buttons on the right hand side after a lifetime of using Windows, so I used the following fix to change the orientation:

**Move window buttons to the right side:**[INDENT][B]1. open gconf-editor from terminal
2. apps->metacity->general
   change button_layout value to :maximize,minimize,close[/B][/INDENT]This worked fine at first, but they seem to have switched back to the left after a few weeks. Possibly because I tried a few new themes, but I haven't found a way to return it to the right by going down that road.

I tried using the config editor again and put in exactly the same thing, but it didn't change it at all. I then changed it to values that didn't make any sense, and it accepted them and kept working fine.

Does this mean that there's a problem with gconf-editor, or is it something else that I can't see?

I've had a look through various forums and no-one seems to have mentioned this problem, so any help would be appreciated

---

### Post by earthpigg on 2011-04-23
hi,

it sounds like you have something else conflicting with your metacity settings.

first few possibilities that jump to my mind:

have you turned compiz ("desktop effects") on since then, or changed compiz settings?

using emerald compiz themes?

have you installed the fusion icon? (if you don't know what it is, that would be a no :P )

EDIT: does running "metacity --replace" in a terminal fix it?

---

### Post by ajgreeny on 2011-04-23
One way to stop this happening when you play around with themes, after changing the button placement is to make a new theme with customisation of the separate parts, but choosing one of the buttons on the right parts (I can't remember where they are set, and I'm using lxde at the moment).  Save the new theme, and you can always go back to it when you mess around with others.

---

### Post by de_island on 2011-04-23
Earthpig, your "metacity --replace" idea caused the window bar to completely disappear, the keyboard stopped working and I wasn't able to click anything other than the active window. So I wouldn't recommend anyone else doing that. Thankfully it was ok after a forced reboot.

I did change the desktop effects settings, but then I changed them back. Do you think that had an impact?

---

### Post by 5149.5 on 2011-04-23
Sometimes when I am goofing around in Compiz the window decorator gets changed. If you look at Windows decorator, the "Commnd" may get changed to something other than what you had. I have Compiz set the way I like, so I just click the reset button on the far right and I get my windows decorations back.

---

### Post by earthpigg on 2011-04-24
> **de_island said:**
> Earthpig, your "metacity --replace" idea caused the window bar to completely disappear, the keyboard stopped working and I wasn't able to click anything other than the active window. So I wouldn't recommend anyone else doing that. Thankfully it was ok after a forced reboot.

wow, that seems very odd. that tidbit is [very often given]("http://www.google.com/search?hl=en&client=ubuntu&hs=OOs&channel=fs&q=+site:ubuntuforums.org+%22metacity+--replace%22") and has generally worked for me.

i'm sorry it didn't work out for you.

---

### Post by andrewthomas on 2011-04-24
> **earthpigg said:**
> wow, that seems very odd. that tidbit is [very often given]("http://www.google.com/search?hl=en&client=ubuntu&hs=OOs&channel=fs&q=+site:ubuntuforums.org+%22metacity+--replace%22") and has generally worked for me.

+1  

I can see where 
```
compiz --replace &
```can make the window decorations disappear, but not 
```
metacity --replace &
```

---

### Post by de_island on 2011-04-24
> **earthpigg said:**
> 
i'm sorry it didn't work out for you.

I'm not blaming you for anything malicious at all, Earthpig. Far from it.

I appreciate your suggestions about looking at compiz and the window decorator, but I can honestly say that I have no idea how to run or even find those and a pretty thorough Google search wasn't much of a help.

Some help for a serious beginner?

I'm also gonna point you to the fact that changes made in gconf-editor aren't having any effect. Even when I change the values to complete gibberish. Should that be happening if it's just a problem with window decorator et al?

---

### Post by JKyleOKC on 2011-04-24
> **de_island said:**
> I'm also gonna point you to the fact that changes made in gconf-editor aren't having any effect. Even when I change the values to complete gibberish. Should that be happening if it's just a problem with window decorator et al?I'm using Xubuntu, which has a different window manager, and don't use gconf-editor to change its configuration, so this may be a total red herring. However many of the configuration settings are done only at the time you log on, so after making a change you may need to log out and back in before the change can take effect.

No need to reboot; just use the "quit" button and select "Log Out" as the action, then sign back in.

Hope this helps!

---

### Post by de_island on 2011-04-24
> **JKyleOKC said:**
> 
No need to reboot; just use the "quit" button and select "Log Out" as the action, then sign back in.

Hope this helps!


I'm afraid not. As soon as you input the value for the key and then press "ok", the change is supposed to take effect. That's how it worked for me the last time I did it, and I've even shut down the laptop three or four times since the problem first occurred.

---

### Post by Krytarik on 2011-04-24
May it be that you run 'gconf-editor' as root, with gksu/gksudo/sudo?
If so, that would change the config of root, not yours.

Also, if you are interested in a nice, little options GUI to change the button order, see my earlier post:
[http://ubuntuforums.org/showthread.php?p=10115757#post10115757](http://ubuntuforums.org/showthread.php?p=10115757#post10115757)

Greetings.

---

### Post by de_island on 2011-04-24
> **Krytarik said:**
> May it be that you run 'gconf-editor' as root, with gksu/gksudo/sudo?
If so, that would change the config of root, not yours.

Also, if you are interested in a nice, little options GUI to change the button order, see my earlier post:
[http://ubuntuforums.org/showthread.php?p=10115757#post10115757](http://ubuntuforums.org/showthread.php?p=10115757#post10115757)

Greetings.

You sir, are a God. Thank you very much.

I'm going to mark this as solved since it solved my immediate problem, but can anyone see a solution to my problem with gconf-editor?

---

### Post by Krytarik on 2011-04-24
> **de_island said:**
> You sir, are a God. Thank you very much.

You're welcome!
> **de_island said:**
> but can anyone see a solution to my problem with gconf-editor?
What exactly do you mean?

---

### Post by de_island on 2011-04-24
When I go into gconf-editor, metacity, etc. and change the key value, it has no effect. I can't use it to change the side that the window buttons are on, or the order or remove any of the buttons.

If I input complete gibberish into the field, then it still doesn't change anything.

This isn't how it should act, and it isn't how it used to work just a few weeks ago.

---

### Post by Krytarik on 2011-04-24
Did you notice that? How about that?
> **Krytarik said:**
> May it be that you run 'gconf-editor' as root, with gksu/gksudo/sudo?
If so, that would change the config of root, not yours.


---

### Post by de_island on 2011-04-24
> **Krytarik said:**
> Did you notice that? How about that?

That's how I normally run it. It's the way I've always done it, so no change there.

---

### Post by Krytarik on 2011-04-24
> **de_island said:**
> That's how I normally run it. It's the way I've always done it, so no change there.
Maybe you didn't understand: You should *not* run 'gconf-editor' as root, otherwise you change the settings of root, not yours!

---

### Post by de_island on 2011-04-24
> **Krytarik said:**
> Maybe you didn't understand: You should *not* run 'gconf-editor' as root, otherwise you change the settings of root, not yours!

Gotcha. I did indeed misunderstand. I didn't think that there was any difference between the two. The problem only occurs when running it as root, but it's fine otherwise.

Thanks, Krytarik. I can now consider the thread fully closed. :)

---

