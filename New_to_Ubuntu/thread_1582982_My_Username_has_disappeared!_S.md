---
title: "My Username has disappeared! :S"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by BJones007 on 2010-09-27
I seriously dunno what happened but I turned on my netbook today and my username just wasn't there. Screenshot below:

[IMG]http://bit.ly/9dS5vH[/IMG]

can anybody help me in getting it back there?

---

### Post by Soul-Sing on 2010-09-27
rightclick the panel: properties: "screen-points/pixels?"

---

### Post by BJones007 on 2010-09-27
> **leoquant said:**
> rightclick the panel: properties: "screen-points/pixels?"
I'm not seeing "screen points/pixels" only thing thas there is "orientation" and "size"

---

### Post by Bölvaður on 2010-09-27
right click on the panel, add panel item, look for... oh god I dont remember.. test some things out, you can remove them by right clicking them and click delete. but it was something like log out app or indication app....

---

### Post by ajgreeny on 2010-09-27
Right click the panel and add **Indicator-applet-session**.  That should get it back for you.

---

### Post by Soul-Sing on 2010-09-27
> **BJones007 said:**
> I'm not seeing "screen points/pixels" only thing thas there is "orientation" and "size"


ok, you could "play" with that.
or killall gnome-panel (it builds itself up)

---

### Post by BJones007 on 2010-09-27
Nah the indicator applet only shows this: [IMG]http://img256.imageshack.us/img256/4346/screenshot2dwb.png[/IMG]
  my username isn't showing

---

### Post by andrewthomas on 2010-09-27
> **ajgreeny said:**
> right click the panel and add **indicator-applet-session**.  That should get it back for you.
+1

or as a last resort you could

```
rm -r ~/.gconf/apps/panel
``` to restore the panel to the default state
You must log-out and back in for the changes to take effect.

---

### Post by BJones007 on 2010-09-27
> **andrewthomas said:**
> +1

or as a last resort you could

```
rm -r ~/.gconf/apps/panel
``` to restore the panel to the default state
You must log-out and back in for the changes to take effect.
Tried that countless times but all it does is reset the other applets, doesn't bring back my username. I guess I can't fix it :(

---

### Post by andrewthomas on 2010-09-27
post the output of 

```
aptitude search indicator-applet-session
```

---

### Post by BJones007 on 2010-09-27
> **andrewthomas said:**
> post the output of 

```
aptitude search indicator-applet-session
```
I got the following result in Terminal ```
 p   indicator-applet-session        - Clone of the GNOME panel indicator applet 
```

Dunno what that means, any other suggestions?

---

### Post by andrewthomas on 2010-09-27
> **BJones007 said:**
> I got the following result in Terminal ```
 p   indicator-applet-session        - Clone of the GNOME panel indicator applet 
```Dunno what that means, any other suggestions?
That means that it is not installed

```
sudo apt-get install indicator-applet-session
```

---

### Post by BJones007 on 2010-09-27
> **andrewthomas said:**
> That means that it is not installed

```
sudo apt-get install indicator-applet-session
```
Hmmm....ok. Am I gonna have to log out for the changes to take effect?

---

### Post by andrewthomas on 2010-09-28
Did it work?  If so, mark your thread as [SOLVED] with the thread tools menu

---

### Post by BJones007 on 2010-09-28
> **andrewthomas said:**
> Did it work?  If so, mark your thread as [SOLVED] with the thread tools menu
Nah it didn't work.

---

### Post by andrewthomas on 2010-09-28
I would try this 

```
rm -r ~/.gconf/apps/panel
```

one more time, since you, I presume, have not done it since installing the indicator-applet-session

---

### Post by BJones007 on 2010-09-28
> **andrewthomas said:**
> I would try this 

```
rm -r ~/.gconf/apps/panel
```

one more time, since you, I presume, have not done it since installing the indicator-applet-session
Ok I just did that, what now?

---

### Post by andrewthomas on 2010-09-28
try and log out and back in and see if the indicator is back

---

### Post by BJones007 on 2010-09-28
> **andrewthomas said:**
> try and log out and back in and see if the indicator is back
Nice work man, thanks.

---

### Post by andrewthomas on 2010-09-28
You are welcome.  Please mark the thread as [SOLVED] using the thread tools menu.

---

