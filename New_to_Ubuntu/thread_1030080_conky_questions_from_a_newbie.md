---
title: "conky questions from a newbie"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Hume's doona on 2009-01-04
i'm currently trying out kde vs gnome, so i have both installed.

i'm trying to set up conky to monitor the performance with each.

so far i have only done the obvious```

sudo apt-get install conky
```

so it's the 'out of the box' version.

for now i want to know a few basic things

1. how do i 'attach' it to the desktop so it runs like a desklet?
2. how do i add programs to the list such as gimp, kino and other multmedia programs to monitor the individual usage of these?
3. how do i monitor a 3g network connection? the base has a network monitor but it doesn't register my 3g usb connection?
4. i'd like to keep it transparent

i think that's all for now

thanks
dan

---

### Post by northern lights on 2009-01-04
[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/")

---

### Post by the yawner on 2009-01-04
Conky's a little complex and would need some tweaking to suit your needs. I'd suggest you copy a basic .conkyrc for a basic setup. I got mine from gnome-look. For more help on some specific features you require, this [thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky") is mighty helpful.

---

### Post by Hume's doona on 2009-01-04
ok, i think i can do that... but my conkyrc file isn't where that site said it would be (i followed the link to the utter newb installation [http://linuxowns.wordpress.com/2008/01/18/conky/](http://linuxowns.wordpress.com/2008/01/18/conky/) )

it also had a link to the thread here.

i just can't find the file to edit it (it's there b/c i ran it)

can i do a search somehow with konsole?

---

### Post by adult swim on 2009-01-04
it should be a hidden file called .conkyrc in your home folder.  to view hidden files hit ctrl+h
to find from konsole
```
ls -a
```

---

### Post by MenZa on 2009-01-04
I'm not sure if conky creates a .conkyrc file in your Home folder at first---rather, I think I recall it using a sample config in /usr/share/conky or similar. It'll check if ~/.conkyrc exists or not, and if not, it'll fall back to the sample config.

---

### Post by the yawner on 2009-01-04
Actually, on a new installation, you would need to create one. Just save it as .conkyrc in your home folder. (The dot (.) is to keep the configuration a hidden file)

---

### Post by Hume's doona on 2009-01-04
aha, found it.

so i open with an editor, which would be kommander editor for kde?

sorry to be so daft

---

### Post by adult swim on 2009-01-04
i think in kde youll need to run kate

---

### Post by Hume's doona on 2009-01-04
i feel clever now ;)

i used this post [http://ubuntuforums.org/showpost.php?p=1648563&postcount=7](http://ubuntuforums.org/showpost.php?p=1648563&postcount=7)
as it has all that i want, i can change the colours myself, but if anyone knows how to add the 3g monitor to it that would be a big help

---

### Post by Hume's doona on 2009-01-04
i worked it out if anyone reads this looking for an answer.

i just had to change the variable of the address to 
```
lo
```

thanks everyone!

---

