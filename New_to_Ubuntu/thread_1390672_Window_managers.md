---
title: "Window managers?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by pankirk on 2010-01-25
I almost completely feel like gnome isn't snappy enough for me. I come from a very stripped down version of windows XP which is designed to be very fast. But I'm looking for something even faster. I currently have Ubuntu 9.10 installed on my system and I'm looking for a way to install a window manager like fluxbox or blackbox.

My question is this:
Will I still be able to use all the programs I'm using in gnome? Like virtualbox, gftp, google chrome, openoffice, and all those goodies?

Also will all of these be uninstalled once I remove gnome?

And lastly, how do I completely get rid of gnome and all the other stuff it comes with and replace it with the window manager I chose?

Thanks a lot,
-P

---

### Post by Revolutionary101 on 2010-01-25
Yes you will be able to use all of the programs that you have installed. As far as I know Ubuntu will not let you completely remove gnome. I would suggest installing whatever window manager you would like and then just set it as your default session on the login screen.

I personally suggest using LXDE. Its fast and very responsive on my 4 year old laptop. To install it type this into terminal.

```
sudo apt-get install lxde
```

---

### Post by pankirk on 2010-01-25
Hi thanks for the reply.

I installed pekwm completely, I just need help on how to add it to my sessions menu.

Any help would be appreciated,

thanks!

---

### Post by ja660k on 2010-01-25
use fluxbox, all the cool kids use it...

sudo apt-get install fluxbox 

then when you login, go to sessions and click fluxbox.

visit...
[http://fluxbox.org/screenshots/](http://fluxbox.org/screenshots/)
so you can see what is possible before you install :)

---

### Post by baddog144 on 2010-01-25
You could give openbox a shot, or if you're feeling somewhat more adventurous, you could try a tiling wm such as xmonad or wmii or awesomewm ;)

---

### Post by pankirk on 2010-01-25
Wow!

I just installed fluxbox and I have honestly never seen anything like it. It's so... Minimal! I love it!

Too bad my internet decides it doesnt want to work when I have it on... Any ideas?

By the way, this is great! Just what I'm looking for! Snappy and efficient!

---

### Post by stoogiebuncho on 2010-01-25
> **pankirk said:**
> Too bad my internet decides it doesnt want to work when I have it on... Any ideas?

Do you know if it's loading your network manager?  Try pressing Alt+F2 and entering 
```
nm-applet
```

---

### Post by pankirk on 2010-01-25
Hi!

Thanks for the reply!

I just got the network manager to work :D

Now I have a world of customization ahead of me :)

Thanks everyone!!

---

### Post by stoogiebuncho on 2010-01-25
Glad it worked for you.  You may have to add that command to your startup applications so that it is loaded whenever you log in.

Have fun playing!

---

### Post by stanca on 2010-02-13
I'm glad too you're enjoing Fluxbox WM.You'll love it and never let it down.Trust me.;):P

---

