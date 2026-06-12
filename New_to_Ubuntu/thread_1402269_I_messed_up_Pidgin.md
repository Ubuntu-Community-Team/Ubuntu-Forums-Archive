---
title: "I messed up Pidgin"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Hman242 on 2010-02-08
Somehow today I messed up Pidgin and now the interface looks like a bucket of *** and I can't for the life of me find how to change it back. [Here]("http://img268.imageshack.us/img268/4273/screenshot4da.png") is what is looks like.

---

### Post by semi_fiction on 2010-02-08
What plugins do you have enabled?

---

### Post by Hman242 on 2010-02-08
Only Lipnotify Popups and Nautilus Integration.

---

### Post by warfacegod on 2010-02-08
Did you change your system theme?

---

### Post by Hman242 on 2010-02-09
Nope. I went to messenger and it seemed like I had right clicked and opened up a small menu. It only had one option, I accidently clicked it and now Pidgin looks weird.

---

### Post by warfacegod on 2010-02-09
Click Tools in the buddy list, select Preferences, and set the themes to default.

---

### Post by peace.gangsta on 2010-02-09
will ```
pidgin --reset
``` work ?
Try it...

---

### Post by Hman242 on 2010-02-09
Doesn't work.

pidgin: unrecognized option '--reset'

I have the theme set to default.

---

### Post by woodmaster on 2010-02-09
```
sudo apt-get remove purge pidgin
sudo apt-get install pidgin
```

---

### Post by warfacegod on 2010-02-09
> **woodmaster said:**
> ```
sudo apt-get remove purge pidgin
sudo apt-get install pidgin
```

Doing this will probably work but will force the OP to renter all of his contacts.

By the way, do you really have only 2 *MB* Of RAM?

---

### Post by Hman242 on 2010-02-09
I think he meant GB :P
I tried entering that in the Terminal, but it said 

E: Couldn't find package purge

---

### Post by pedro3005 on 2010-02-09
I think it should be either:
```
sudo apt-get purge pidgin
```
or
```
sudo apt-get remove --purge pidgin
```
Correct me if I'm wrong though.

---

### Post by Hman242 on 2010-02-09
They both got rid of Pidgin, but when I reinstall it, it still has that interface. Isn't there a way to change it back using Pidgin?

---

### Post by warfacegod on 2010-02-09
> **Hman242 said:**
> They both got rid of Pidgin, but when I reinstall it, it still has that interface. Isn't there a way to change it back using Pidgin?

I'm going to bet Pidgin is using your system theme.

---

### Post by Hman242 on 2010-02-09
Let's just say it is. If it was, how would I change it back?

---

### Post by semi_fiction on 2010-02-09
You would have to change your system theme.

---

### Post by warfacegod on 2010-02-09
System> Prefs.> Appearance> Theme tab

---

### Post by Hman242 on 2010-02-09
I tested it, it looks like this with the other themes I try. This isn't it.

---

### Post by warfacegod on 2010-02-09
Try changing the system Theme and Rebooting. If that doesn't work, I give up.

---

### Post by Hman242 on 2010-02-09
Then give up, because it didn't work. The solution has to be in Pidgin, that's were the problem originated.

---

### Post by warfacegod on 2010-02-09
Sorry to bail on you but I'm out of ideas. I'm going to PM someone that I think knows more about Pidgin than I do.

---

### Post by Hman242 on 2010-02-09
Thanks man. As long as I can get this resolved I should be happy. I would've posted in the Pidgin forum, but I don't think they have one.

---

### Post by Leppie on 2010-02-10
try renaming your pidigin settings file:
```
mv ~/.purple/prefs.xml ~/.purple/prefs.xml.old
```

@wfg, you've been busy i see ;)

---

### Post by Hman242 on 2010-02-10
Leppie, why is it that you and you alone are the one that is able to solve me problems? Thanks man.

---

### Post by Leppie on 2010-02-10
> **Hman242 said:**
> Leppie, why is it that you and you alone are the one that is able to solve me problems? Thanks man.
not sure i'm the only one who can solve your problems. anywyas, you're welcome ;)

---

