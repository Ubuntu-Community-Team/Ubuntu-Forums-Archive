---
title: "The Gnome Panel - weird issue or not!!!"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2010-05-23
i'm having trouble with Gnome Panel in my Lucid...

i wanted to remove all panels...
removed the bottom one successfully by right clicking...

unfortunately, now, the top one cannot be removed in the same way... the 'Delete Panel' option is disabled!!!

i read something about the gconf editor... did few things... still having trouble...

i uninstalled GNOME-PANEL from synaptic... still its there in my desktop!!!

now the main thing is, i can move this panel anywhere in the screen...

take a look at this picture and see for yourself... is this weird or not???

[IMG]http://lh3.ggpht.com/_CEPbkas_2SM/S_mOS1qmXUI/AAAAAAAACqA/gumUp2xAvLE/s400/Screenshot.png[/IMG]

how can i remove this panel???

---

### Post by -humanaut- on 2010-05-23
You'll probably have to purge the configuration files for the gnome-panel.

---

### Post by angry_johnnie on 2010-05-23
[you're on the right track about gconf-editor.]("http://ubuntuforums.org/showthread.php?t=1314315")

look at post #4

---

### Post by randolf_ambrose on 2010-05-23
> **angry_johnnie said:**
> [you're on the right track about gconf-editor.]("http://ubuntuforums.org/showthread.php?t=1314315")

look at post #4

you directed me to
> **mcduck said:**
> The only way to get rid of the panel, if you don't need it, is to remove it from your Gnome session through gconf-editor. Of course you can configure some other app to run in it's place if you want to. :)

Removing the last panel isn't possible, and as long as the panel is running as Gnome component it will automatically spawn back if you try to kill it.

So, if you want to remove the Gnome-panel from your desktop you need to start gconf-editor and then remove "panel" from the list in desktop/gnome/session/required_components list (and perhaps also unset the desktop/gnome/session/required_components/panel -key).

But if you are planning to just run some other panel or dock instead it would make sense the leave the panel in the session components, and then just set the desktop/gnome/session/required_components/panel to use whatever program you are planning to run. This would automatically start that app for you and also autospawn it back if it crashes or is killed.


the same thread i've followed before posting here...

i tried to remove 'panel' from 'required_components_list' but not possible... delete or right click doesnt work... may be i need to log in as root???

so i tried the second option, put awn as the value for panel... no issues as well as no change!!!

that first panel remains in my desktop!!!

---

### Post by randolf_ambrose on 2010-05-23
> **-humanaut- said:**
> You'll probably have to purge the configuration files for the gnome-panel.

:-k how to do that??? ;)

---

### Post by sgosnell on 2010-05-23
My question is 'why'.  Why do you want to remove all the panels?  That makes no sense to me, so please enlighten me.  I understand needing more screen real estate for a netbook, but I get that by making the panels autohide.  I don't see them until I need them, and I need them all the time.

---

### Post by angry_johnnie on 2010-05-23
quick and dirty fix i just though of:

```
sudo chmod a-x /usr/bin/gnome-panel
```

log out and back in.

the panel should be gone.

but then again, without a panel i think you won't have alt+f2.
not that you can't replace it with something else, like launchy or gnome-do, but still, just letting you know.

---

### Post by murderslastcrow on 2010-05-23
K, I've done this A THOUSAND TIMES. Just press Alt+F2, type gconf-editor, click the plus on desktop, gnome, then click ON session in the list on the left.

Now, in the list on the right, right-click required components and go to Edit Key. Then highlight panel and click remove, click okay.

You can always edit the gconf file itself with a text editor and delete the line yourself, just by Ctrl+F to find the line of text that matches.

I hope this helps.

---

### Post by murderslastcrow on 2010-05-23
Oh, RIGHT! And you'll want to pkill gnome-panel in the terminal or Alt+F2 run box, just in case your session is set to start up with the programs it ended with. That way it's guaranteed not to show up unless you start it, yourself.

However, you might wanna' get Gnome-DO or Kupfer to make your life easier- you can't run Alt+F2 without gnome-panel on.

---

### Post by randolf_ambrose on 2010-05-23
> **sgosnell said:**
> My question is 'why'.  Why do you want to remove all the panels?  That makes no sense to me, so please enlighten me.  I understand needing more screen real estate for a netbook, but I get that by making the panels autohide.  I don't see them until I need them, and I need them all the time.


:p

simple answer 1 = i like animated buttons...
simple answer 2 = i always loved blank desktop... i've even disabled my desktop!!!
simple answer 3 = last time i did autohide and put moved that panel from top to left, i never got it back even on mouse hover!!!

honest/rude answer = panels reminds me of the taskbar in windows...

:P

---

### Post by murderslastcrow on 2010-05-23
I'm totally the same way- every few months, I get sick of not having the whole screen for my applications (I'm not even on a netbook).

So I proceed to use Gnome-DO, a dock, or screenlets to manage my windows, or even just Alt-Tab. Once you get the hang of different ways to open programs, it can become much more convenient than taking up an extra 40-50 pixels with panels and the such. Of course, you can just auto-hide, but that gets annoying if you're in a work-intensive program and suddenly a panel jumps in your way.

---

### Post by randolf_ambrose on 2010-05-23
> **murderslastcrow said:**
> K, I've done this A THOUSAND TIMES. Just press Alt+F2, type gconf-editor, click the plus on desktop, gnome, then click ON session in the list on the left.

Now, in the list on the right, right-click required components and go to Edit Key. Then highlight panel and click remove, click okay.

You can always edit the gconf file itself with a text editor and delete the line yourself, just by Ctrl+F to find the line of text that matches.

I hope this helps.

tried my best on that... no option to REMOVE... do i have to log in as root??? to have that privilege???

i've been to almost all entries in gconf file to see anything can be done about this... 

when i got hopeless, i decided to start a thread!!!

:(

---

### Post by randolf_ambrose on 2010-05-23
> **angry_johnnie said:**
> quick and dirty fix i just though of:

```
sudo chmod a-x /usr/bin/gnome-panel
```

log out and back in.

the panel should be gone.

but then again, without a panel i think you won't have alt+f2.
not that you can't replace it with something else, like launchy or gnome-do, but still, just letting you know.


result:
> chmod: cannot access `/usr/bin/gnome-panel': No such file or directory

i had done a complete removal of gnome-panel from synaptic and rebooted!!!

this thing is still in my desktop...

for the moment i've hidden it... but... why is it so damn hard to remove such a silly thing!!! :P

---

### Post by randolf_ambrose on 2010-05-23
> **murderslastcrow said:**
> I'm totally the same way- every few months, I get sick of not having the whole screen for my applications (I'm not even on a netbook).

So I proceed to use Gnome-DO, a dock, or screenlets to manage my windows, or even just Alt-Tab. Once you get the hang of different ways to open programs, it can become much more convenient than taking up an extra 40-50 pixels with panels and the such. Of course, you can just auto-hide, but that gets annoying if you're in a work-intensive program and suddenly a panel jumps in your way.

definitely... 

i wonder how i forgot to mention how annoying is the autohide option!!! that also reminds me of windows taskbar... :P

---

### Post by randolf_ambrose on 2010-05-23
holy #####.................

this shows that i'm a total noob...

now i cant log into my lucid...

i think i did something wrong in gconf...

now i cant log in... keep on asking me to enter passcode...


removing gnome-panel removes gnome desktop too huh... hi hi hi... 

now what shall i do to get my desktop back??? be able to log in???

---

### Post by randolf_ambrose on 2010-05-23
please someone help me...

how can i get back to my desktop???

i'm not able to log in!!!

---

### Post by gmxgeek on 2010-05-23
Boot into the recovery console and reinstall gnome-panel and gnome-desktop

---

### Post by randolf_ambrose on 2010-05-23
> **gmxgeek said:**
> Boot into the recovery console and reinstall gnome-panel and gnome-desktop

thanks...

that worked...

i had lost my x-configuration too...

just reinstalled display driver and after a reboot, everything works fine...

but that PANEL is still there...

now that i know what would go wrong, i'm gonna keep trying!!!

hope someone will help me remove this panel from my desktop!!!

---

### Post by HooieH on 2010-05-23
I have successfully removed my gnome-panel with cairo-dock.
Open Configuration editor navigate -desktop -gnome -session   required components and in the panel field place the application your using to replace it mine was cairo-dock. Next go to your start-up applications find and if you find gnome-panel make sure it is unchecked. then restart as far as getting your desktop back try rebooting in recovery mode and see if that works.

---

### Post by Daniel1994 on 2010-05-23
If you're looking for a really clean and efficent desktop, you shoud try out openbox(or any of the other *boxes).

Maybe it's not what you're looking for, but I thought I should mention it.

If you wanna try it:
```
sudo apt-get install openbox
```

then select "openbox" under "session"(or something) before you log in.

PS: make sure you open a terminal and type:```
nm-applet & exit
``` after you log in, or else you won't get internet access.

---

### Post by angry_johnnie on 2010-05-23
i think we may be up to something here...

i ran apt-get remove gnome-panel just to see what it does.

it tells me:

```
The following packages will be REMOVED:
  gnome-applet-globalmenu gnome-applets gnome-globalmenu gnome-panel
  gnome-session gnome-swallow-applet indicator-applet indicator-applet-
  session indicator-me ubuntu-desktop

```

yours might have been different, as i have installed some things you may not have, but the key thing is it removes gnome-session.


so it makes sense that you couldn't log in after that.

which takes me to my next assumption (that's all it is, really :p)

after you removed gnome-panel, and tried gconf-editor and all that, you didn't log out or restart your computer, did you?  so these processes kept running, and then, when you did restart, you found out you didn't have a gnome-session.

so, i still think you could just disable gnome-panel's executable properties.

you won't remove your gnome-session
you won't mingle with gconf settings

then, after you do log out, and back in, you will find gnome-panel is gone.

i just did this, to prove it.

it works, trust me.

i like gnome-panel, but i disabled it just to be absolutely sure it would work (of course i enabled it again, but then, i've proved it works).

---

### Post by sgosnell on 2010-05-23
If you really, really don't want panels, why not install Crunchbang?  Or Lubuntu?  Or almost anything else.  Gnome desktop was never designed to work without panels, but there are a number of variants that are.

---

### Post by angry_johnnie on 2010-05-23
> **sgosnell said:**
> If you really, really don't want panels, why not install Crunchbang...?


True.  :-)

Or, you could just install openbox, or xmonad, or you name it, on top of your regular ubuntu, and then just run the xsession of your choice.

But then again, if you want ubuntu + gnome + no panel, it's your choice. ;)

---

### Post by theozzlives on 2010-05-23
It used to be schemas > desktop > GNOME > session, but for some reason Lucid disabled it so I don't know. The devs are taking away alot of "freedoms" we used to have.

---

### Post by angry_johnnie on 2010-05-23
> **theozzlives said:**
>  are taking away alot of "freedoms" we used to have.


nah, i wouldn't say they're taking freedoms away :p

they just keep making it trickier and trickier.
it's kinda fun, though, having to learn all these little details all over again...

---

### Post by HooieH on 2010-05-23
I have successfully removed my gnome-panel with cairo-dock.
Open Configuration editor navigate -desktop -gnome -session required components and in the panel field place the application you want like cairo-dock -c

Here is my Desktop notice no panel

---

### Post by sgosnell on 2010-05-23
Don't get me wrong, I'm not trying to tell anyone how they should do things, I'm just trying to learn the whys of this.  There are lots of ways to do things, and I haven't tried nearly all of them, so I like to learn about different methods.  I don't see the point in this method, but I would like to know why people want to do it, maybe there's a better way.  Are there benefits other than just personal preference?

---

