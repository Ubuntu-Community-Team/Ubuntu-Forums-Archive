---
title: "cryptkeeper replacement on Natty?"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by AustinBjorn on 2011-05-02
Hi! Is there a replacement for cryptkeeper in Unity (Natty), I know I can mount on the console with encfs but I'm looking for a GUI tool.

Thanks!

Austin

---

### Post by KL_72_TR on 2011-05-02
I went: Ubuntu Software Center > Cryptkeeper 
There it was: EncFS system tray applet for GNOME
Sorry if I'm giving wrong answer.

---

### Post by Paraplegic Racehorse on 2011-05-26
There is no replacement for Cryptkeeper in 11.04. It available via Software Center. However, it steadfastly refuses to display in the top bar (Unity) without working some cli magic.

The change to Unity robbed us of our ability to EASILY and INTUITIVELY manage how we want our desktop(s) to look and function.

It should appear just fine in all the other desktops, and probably also Classic, but I haven't tried it.

The cli magic is in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071/comments/8"). Unfortunately, the bug was incorrectly filed in the Cryptkeeper bug lists, rather than the Unity big lists.

I will be changing desktops as soon as I figure out the best way to go about doing so without adding lots of bulk in the form of duplicate functionality apps (text editors, file managers, etc) or losing any more usefulness of Gnome than has been imposed by the switch to Unity.

---

### Post by metasoarous on 2011-06-05
This is a documented bug -

[https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071)

If you follow that link, you will find another link that lets you indicate that this bug affects you. You can also subscribe to updates.

Basically, the issue is that cryptkeeper is set to display on the gnome system tray. If you are running 11.04 with Unity though, there is no gnome and thus no gnome system tray. So there is no place for the gui to display itself. This is affecting other system tray type apps as well, so we're not alone. 

Someone who commented on the launchpad thread mentions that there might be a way to "whitelist" it so that it will display in the unity tray, but I haven't tried it - I'll probably just mount from terminal. It'll definitely be nice to get this back and running again. 

Cheers

Chris

---

### Post by metasoarous on 2011-06-05
I ended up trying the fix that you posted to, Paraplegic, but that has made the environment fairly buggy. The launcher pops up behind windows now, and windows are stuck on one of my two screens and can't move between (dual monitor).So, I don't think that is a viable workaround. Manually mounting from the command line seems like a better option for someone not afraid of CLI.

Chris

---

### Post by mcduck on 2011-06-05
> **metasoarous said:**
> This is a documented bug -

[https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071)

If you follow that link, you will find another link that lets you indicate that this bug affects you. You can also subscribe to updates.

Basically, the issue is that cryptkeeper is set to display on the gnome system tray. If you are running 11.04 with Unity though, there is no gnome and thus no gnome system tray. So there is no place for the gui to display itself. This is affecting other system tray type apps as well, so we're not alone. 

Someone who commented on the launchpad thread mentions that there might be a way to "whitelist" it so that it will display in the unity tray, but I haven't tried it - I'll probably just mount from terminal. It'll definitely be nice to get this back and running again. 

Cheers

Chris

Actually, there *is* Gnome, and there *is* the notification area, just like before.

Unity just runs on top of Gnome (as a Compiz plugin), and the notification area uses a whitelist to tell which icons are allowed. Apart from the panels, the desktop environment in 11.04 is still just a normal Gnome 2 desktop.

Just install dconf-editor (included in "dconf-tools"-package) and add your programs to the white list or set it to 'all'. The relevant key is *desktop/unity/panel/systray-whitelist*.

(and yes, Cryptkeeper works fine in 11.04. :))

---

