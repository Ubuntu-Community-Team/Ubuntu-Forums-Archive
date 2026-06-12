---
title: "themes messed up"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by DarinB on 2010-06-13
i just did a clean install of lucid LM 9
my themes are messed up.
i have been transferring the .themes folder for years. And now i don't have any icons just gray folders and small font. 
how can i purge it and get back the original themes????
every theme i pick says missing engine whether gtk+ clearlooks which i can not find on gtk2 and it does not help i think it is time to clear out the old stuff how do i do it?

---

### Post by radddi on 2010-06-13
I had a similar problem when I used the same Home partition from my previous 8.10 install for Lucid.

Create and login to a new user. If everything is normal, then your old settings have messed up the GUI. However, the way I got around that is by migrating to a new user altogether and transferring only the options I needed - documents, browser settings and WINE dir. I don't know if that's applicable to you.

.:CheerS:.

---

### Post by DarinB on 2010-06-13
ouch that seems like a massive amount of work...ok i will try. some times i can by login in again get my theme back but still most of my themes have the crap old gray folders and ugly blue box trash can i will see what to do i wish there was a better way. 
thanks it is a great idea.

---

### Post by Deadite81 on 2010-06-13
Before you do anything drastic, if it's just your themes you probably just need to install a package or two.  You mentioned "Clearlooks".  Ubuntu 10.04 uses a new theme engine "Murrine".  Getting the other engines is simple and should fix your problem:

```
sudo apt-get install gtk2-engines
```

After you put that in a terminal or search Synaptic Package Manager and install it that way your themes should work.

---

### Post by Deadite81 on 2010-06-13
I'm also a little confused...
> how can i purge it and get back the original themes????Simply delete your ~/.themes folder (or its contents) if you want to get rid of your user themes.  
Any themes in /usr/share/themes that **you put there** just delete them; if you used apt/Synaptic to install them uninstall them that way (if you used apt/Synaptic though, you'd have the correct engines already).

The "original themes" are there, unless you removed them.  I assume you mean the ones that came with your new install.  Just open your appearance properties, however you do that in Mint, and change it back.

---

### Post by DarinB on 2010-06-13
that did the trick and i add from synaptic clearlooks awesome thanks. lets see what happens....one thing is when i boot up i use not log in and it gives me the old generic look if i restart x    ctrl alt backspace and log in it is fine but that is a pain i will check it now.

---

### Post by DarinB on 2010-06-13
boot up with auto log in still causes the theme to be wrong then when i restart x it comes back but slowly.
any ideas????

---

### Post by DarinB on 2010-06-13
ok i just log in with a password and my themes seemed to work 
BUT    when i use auto log in they get messed up and i get a generic folder icons and small generic fonts in my applications. 
No idea why...

---

### Post by Deadite81 on 2010-06-13
Sorry for not replying sooner!  In Ubuntu 10.04 I cannot get the auto-logon to work correctly.  I have tried the built in login manager and the 3rd party tool GDMsetup2 (I think that's what it was called, I've since uninstalled it) and it just seems to screw my system up in various ways.

This behavior may be a bug, I don't know.  I gave up and just settled for the standard login (with a much less purple background).  To me it's silly to have a login for a single home user on a desktop, and it should be much easier to get rid of it and still have admin privileges.

Other tools that allow you to alter your login settings are Ubuntu Tweak and Ailurus, if your interested (can't guarantee their effectiveness :)).

Beyond that I don't know.  The tools that are supposed to log me in automatically packaged with this OS did not work at all for me, still asking for my password **after **my desktop loads.  This is no good and defeats the purpose.  If this is happening to you I can see how this would make some things not load correctly.  Your themes should load correctly regardless, however; I do not know what could be causing that.  It wouldn't be a bad idea to check your logs with the log viewer to see what is reported by your system about themes and permissions. (~*/.xsession-errors* and */var/log/messages *should shed some light on the situation.) 

If when you log in it doesn't offer you administrative permissions at all, that's a whole other problem.  My recommendation is to disable auto-login until someone else more knowledgeable chimes in or you find a solution/bug report elsewhere.
(If you find something in your logs that is questionable post it and I will try to help.  I wouldn't mind a solution to this myself.)

---

### Post by DarinB on 2010-06-13
thanks for the info on auto log in I am now loging in with password thats life in the ubuntu world. better than full reinstalls when window gets a massive virus every 3 or 4 months.

---

### Post by Deadite81 on 2010-06-13
> thats life in the ubuntu world
You said a mouth full!

I love my Ubuntu and I've been Windows free for about 6 months.  Ubuntu is free and a lot of good people put a lot of hard work into it....BUT these little things are what make new converts give up and switch back.  They simply shouldn't exist.  Especially not an LTS release.  Not trying to go off topic with the thread, just sayin' :).

---

