---
title: "Can't log in to xfce"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Famicommander on 2009-12-18
I'm running Xubuntu 9.10 32 bit. When I boot my system and try to log into an xfce session, the screen just refreshes and I end up back on the login screen.

So I tried and xterm session and I was able to boot xfce via this command:
```
sudo startxfve4
```

And it gave me this:
[[IMG]http://i126.photobucket.com/albums/p81/nintendowarrior/th_Screenshot-8.png[/IMG]](http://s126.photobucket.com/albums/p81/nintendowarrior/?action=view&current=Screenshot-8.png)

I took a screen shot because it wouldn't let me copy/paste.

Anyway, how might I go about fixing those errors so I can boot normally again?

---

### Post by oOarthurOo on 2009-12-18
You should not be able to log into 'x' via sudo, which leads me to believe something is wrong with your user account. 

Try adding a usr via console (VT1), log in as your own user, then sudo adduser, follow the prompts. Once the user has been setup with name and password, switch back to x (VT7) and try logging in with the new user. 

If that works then its safe to say your user config is corrupted. Also, make sure in the login gui setup that you are not allowing yourself to log in to x as root.

---

### Post by pio2pio on 2010-03-12
I have the same problem with logging me out from xfce4.

I logged in to xterm then run startxfce4 command successfully ending with the very similar screen as Famicommander.

Therefore I created a new account by adduser <user_name> and using the new user credentials it logged me in properly.

The question is what's wrong with my previous account?

On the last session i before the problem occurred I changed:
1) panel, adding terminal luncher
2) resolution but it seemed work ok

Many thanks

[]("http://ubuntuforums.org/member.php?u=690246")

---

### Post by pio2pio on 2010-03-12
Recently I solved this by deleting /~/.ICEauthotity 

From other threats I found that sudo can change permission on the above file causing access denied in log:

xfce4-session: Unable to access file /home/piotr/.ICEauthority: Permission denied


So further they advice to use the below instead of sudo:

gnome - gksu, 
kde - kdesu
[xfce]("http://www.mail-archive.com/pkg-xfce-devel@lists.alioth.debian.org/msg05939.html") -Xfce isn't quite as together as Gnome and KDE so there's [no gksu equivalent for it]("http://www.mail-archive.com/pkg-xfce-devel@lists.alioth.debian.org/msg05939.html").

---

### Post by JKyleOKC on 2010-03-12
> **pio2pio said:**
> 
[xfce]("http://www.mail-archive.com/pkg-xfce-devel@lists.alioth.debian.org/msg05939.html") -Xfce isn't quite as together as Gnome and KDE so there's [no gksu equivalent for it]("http://www.mail-archive.com/pkg-xfce-devel@lists.alioth.debian.org/msg05939.html").This is NOT correct. Both gksu and gksudo work properly in Xubuntu, which uses the xfce manager.

As noted earlier in the thread, the damage happens because sudo changes the current user temporarily to be root, with the result that files modified using it may have their permissions changed. Both gksu and gksudo operate a bit differently and take into account the permissions problem.

---

