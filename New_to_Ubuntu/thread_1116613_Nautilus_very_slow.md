---
title: "Nautilus very slow"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by longtom on 2009-04-05
Hi,

In the last couple of weeks Nautilus is fustratingly slow.  Double click on a folder in the right window - nothing.  Double click again - ah - there it is.  Double click on the next folder...nothing...greying out - force quite.  Let's go again...

Installed some alternative file managers and they are all working just fine and as fast as can be expected.

However, I kind of grew fond of Nautilus...has anybody else experienced that problem and actually solved it without sacrificing compiz or anything else? (Yes I have read some of the threads dealing with similar problems - none seem to have a solution so far).

Any suggestions welcome.

---

### Post by ronocdh on 2009-04-06
Have you tried a simple reinstall?```
sudo aptitude purge nautilus && sudo aptitude install nautilus
```
Keep in mind that the **purge** command will get rid of any custom settings you have and restore it to defaults on the reinstall.

If you want to keep your custom settings, you can try```
sudo aptitude reinstall nautilus
```

---

### Post by MockY on 2009-04-06
Nautilus has never really worked perfectly for me. It's more of a rule than an exception that Nautilus completely freezes when transfering large files to a NAS or SMB share while trying to watch a Youtube movie, or simply rename files in another nautilus window. I have gotten used to wait to do anything at all while the file(s) are transfering unless I want to risk data loss.

Another annoyance is Bookmarks. If they are SMB shares, Nautilus returns a "Failed to mount" error if you click on the Bookmark via the menu. However, they work just fine within Nautilus. 

Yet another annoyance is the fact that white space is static. What I mean by that is that you can't use the lasso mechanism for highlighting files. Thunar does this beautifully. This is not a Nautilus error though, but yet a very annoying limitation. Also, you have to have white space in order to paste in anything into the folder you are currently browsing. So if you have List view, you need to change to Icon view if the window is fully populated, or go up a directory and choose "paste into folder".

Furthermore, auto-mount of SMB shares (as in browsing the network) hasn't worked since Gutsy (though it oddly enough has worked in all Beta releases since then, including Jaunty), but this is probably more a Samba issue than Nautilus.

If it wasn't for the fact that Nautilus is so integrated in Gnome, I would use Thunar for all my needs. I like Gnome as a whole however, so I don't really want to migrate to Xfce.

---

### Post by Yashiro on 2009-04-06
Have fun browsing Samba shares with Thunar.

---

### Post by MockY on 2009-04-06
Since I don't use Thunar on a rgular basis, I was not aware of this limitation. However, it looks like you can enable this ability.
Here is just one example: [http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

Hoping it will be included in future releases.

---

### Post by abhigyan91 on 2009-04-06
Also certain ftp sites on an intranet server cant be accessed using nautilus..ne solution to this?

---

### Post by longtom on 2009-04-07
I see - I am not alone...

@ronocdh

I will test your suggestions.  In the meantime I use Gnome commander - and I am actually impressed.

I no nonsense, fast and simple file mananger.  It has some optical bugs - but nothing show stopping.  And I love the keybord shortcuts!

---

