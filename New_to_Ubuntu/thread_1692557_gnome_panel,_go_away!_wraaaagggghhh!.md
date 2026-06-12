---
title: "gnome panel, go away! wraaaagggghhh!"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by bprins on 2011-02-21
Hi!

I am trying to ditch the gnome-panels. I use awn (or cairo when I feel like it) and then the gnome-panels are pretty annoying. I am aware that since 10.10 they can't be deleted no more (at least not the top panel). 

What I did in the past, is open gconf-editor, go to:
1-desktop>gnome>session>required_components
2-remove the value for "panel" (leaving it blank)
3-logout > loging
done.

If I repeat this, I still get the gnome-panel after login.

Am I completely going nuts? Am I missing something here? I'm still pretty sure this worked before.

And why the hell did they make it so damn hard for people that like cairo/awn/docky?!

Hopefully you guys can push me in the right direction.

Thanks a lot in advance!

Bas

---

### Post by TeoBigusGeekus on 2011-02-21
You can add a startup script to your system
```
killall gnome-panel
```

---

### Post by Keiran230 on 2011-02-21
TeoBigusGeekus gave me an idea. **/etc/init.d** contains the scripts that instruct the system on what to start at boot time. If you find the file instructing the system to load the gnome panels, you should be able to just remove it there. [http://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/](http://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/)

Have a live disk ready if you're uneasy about editing these files, and remember to rename files to <name>.old instead of deleting them.

Edit: **sudo apt-get -y remove gnome-panel** may work too.

---

### Post by Dutch70 on 2011-02-21
> **Keiran230 said:**
> TeoBigusGeekus gave me an idea. **/etc/init.d** contains the scripts that instruct the system on what to start at boot time. If you find the file instructing the system to load the gnome panels, you should be able to just remove it there. [http://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/](http://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/)

Have a live disk ready if you're uneasy about editing these files, and remember to rename files to <name>.old instead of deleting them.

Wow, I must be missing something. Why doesn't right clicking the panel & selecting "delete this panel" work???

---

### Post by tea for one on 2011-02-21
> **Dutch70 said:**
> Wow, I must be missing something. Why doesn't right clicking the panel & selecting "delete this panel" work???

Yes, indeed, I was wondering why this would not be an acceptable solution?

---

### Post by bprins on 2011-02-21
Muhaha got it!

It's not the most brilliant approach, but it does the trick.

I started out with renaming my home folder, apparently that doesn't work well if you like to get back into gnome :).

So the second step was deleting .gnome2 .gnome2_private and everything that I could find that had any relation with gnome, and again:
```

gconftool-2 -s /desktop/gnome/session/required_components/panel -t string "avant-window-navigator"

```

Still no luck. Then I thought, lets do it the rough way. So I moved all profile folders into a backup dir:
```

sudo mv .* profile_backup

```

Logout > Login

Again:
```

gconftool-2 -s /desktop/gnome/session/required_components/panel -t string "avant-window-navigator"

```

Logout > login

And we've got a winner!

So I didn't really narrow it down to figure out which profile folder is causing the problem, but at least I got it working again! No more panels and without removing /usr/share/gnome-panel or removing executable bits etc.

I hope this is helpful for anybody who is running into the same problems.

Cheers,

Bas

---

### Post by stueyboy on 2011-03-06
Dunno if anyone is still looking for a solution to this but this link is a way easier method than above

[http://wawan-kurniawan.web.id/how-to-remove-gnome-panel-in-ubuntu-10-10/](http://wawan-kurniawan.web.id/how-to-remove-gnome-panel-in-ubuntu-10-10/)

---

