---
title: "Deus Ex seems to glitch when effects are on..."
date: 2009-03-20
forum: New to Ubuntu
---

### Post by food789 on 2009-03-20
I have the newest version of Wine. I installed Deus Ex. The install went fine. The problem is that if I have effects either Extra or Normal, the games graphics look all glitchey and unplayable.

Is there a way to either fix that problem or is there a way to create some type of script that changes the effects to off?

---

### Post by kidux on 2009-03-20
There was a thread awhile back that explained how to set games up to run in their own X session without a DE/WM. I'll see if I can find it because it ran beautifully. It's basically a sh script that launches the game via wine on a different X server, and it bypasses all the problems associated with compiz/desktop effects.

---

### Post by BDNiner on 2009-03-20
Or you can turn the effects off while playing the game and turn the on when you are not playing.

---

### Post by food789 on 2009-03-20
> **BDNiner said:**
> Or you can turn the effects off while playing the game and turn the on when you are not playing.

The only problem with this is it gets annoying to have to continuously go to that menu and change it...

---

### Post by BDNiner on 2009-03-20
Yeah i can see that, but since they both use your 3d graphics card then performance is going to suffer when both are running. Maybe you can upgrade your video card to better handle the load. 

I have heard of what kidux mentions where you have the games start on a separate X server but the problem is you only have a limited amount of power from your graphics card. So even if you put compiz to sleep on one x server and play the game on another you will still have a decrease in performance.

---

### Post by food789 on 2009-03-20
> **BDNiner said:**
> Yeah i can see that, but since they both use your 3d graphics card then performance is going to suffer when both are running. Maybe you can upgrade your video card to better handle the load. 

I have heard of what kidux mentions where you have the games start on a separate X server but the problem is you only have a limited amount of power from your graphics card. So even if you put compiz to sleep on one x server and play the game on another you will still have a decrease in performance.

I don't really mind because Deus Ex is an old game, so any decrease in performance can easily be fixed by a decrease in quality (which I don't mind at all).

---

### Post by SentientFluid on 2009-03-20
> **food789 said:**
> The only problem with this is it gets annoying to have to continuously go to that menu and change it...

```
sudo aptitude install fusion-icon
```
That will install an icon to your systray that will allow you to control Compiz with a right-click.  Run it with ```
fusion-icon
``` or add it to your login items so it's running when you log in.

---

### Post by BDNiner on 2009-03-20
Here is the forum topic from a while ago on how to accomplish running the game on a separate X server.

[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)

---

### Post by kidux on 2009-03-20
> **BDNiner said:**
> Here is the forum topic from a while ago on how to accomplish running the game on a separate X server.

[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)
Thanks for finding that. I got sidetracked with work, lol!

---

### Post by food789 on 2009-03-21
I couldn't get the separate X server to work...

I've been trying to get the fusion-icon to work however when I attempt to run it via Terminal it gives me this error message:
[QUOTE=Terminal]steve@steve-laptop:~$ fusion-icon 
* Using the GTK Interface
* No module named pygtk
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
steve@steve-laptop:~$ 
[/QUOTE]
I have pygtk though. I can't get PyQt4 to work 'cause it gives me a different error...

Help?

---

### Post by SentientFluid on 2009-03-21
> **food789 said:**
> I couldn't get the separate X server to work...

I've been trying to get the fusion-icon to work however when I attempt to run it via Terminal it gives me this error message:

I have pygtk though. I can't get PyQt4 to work 'cause it gives me a different error...

Help?

From [http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/#comment-487](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/#comment-487)

> Solved my problem. My pygtk library seems to run only under python2.5, whereas the #!/usr/bin/env python in the fusion-icon python scripts points to a lower version. So I grabbed the fusion-icon source from git, edited the files in src/ to start with the line “#!/usr/bin/env python2.5&#8243; and installed from source. Hope that helps someone.

---

### Post by food789 on 2009-03-21
Ok, I did that. Now I tried to run fusion-icon and I get a slightly different error message:
[QUOTE=Terminal]steve@steve-laptop:/usr/bin$ fusion-icon 
* Using the GTK Interface
*** No module named compizconfig**
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
[/QUOTE]
So now I need compizconfig...

This is confusing :confused:...

---

### Post by food789 on 2009-03-21
Bump...

](*,)

---

### Post by hypocratus on 2009-03-21
You could try:
sudo apt-get install python-compizconfig
if you don't already have it installed.

---

