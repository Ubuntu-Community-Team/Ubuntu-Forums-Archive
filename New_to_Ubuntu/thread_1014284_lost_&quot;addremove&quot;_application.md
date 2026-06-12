---
title: "lost &quot;add/remove&quot; application"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by megatotz on 2008-12-17
[SIZE="2"]probably a stupid question...
i had some problems with my software sources and synaptic package manager- they froze when opened and would not respond.
 i searched for a solution online and it was suggested to uninstall and reinstall the synaptic package, which sorted out that problem but since then my "add/remove" application has disappeared from the applications bar and i cannot seem to find it anywhere... 
is there an easy way of getting it back???
:confused:[/SIZE]

---

### Post by SunnyRabbiera on 2008-12-17
well you really dont need add/remove if you got synaptic running.
Synaptic does the exact same job as add/remove only add/remove is a more beginner oriented application.
Consider this a blessing, as I find new users depend on add/remove too much and I rather them use synpatic instead,
Synaptic is easy enough to understand even for a beginner I think, heck its because of synaptic that I got into linux... its so easy :D

---

### Post by HotShotDJ on 2008-12-17
When you removed synaptic and then reinstalled, it is likely that the Add/Remove Applications software was removed as well.  Go into Synaptic Package Manager and search for gnome-app-install.  If it is not installed, then install it.  This should get you fixed up.

---

### Post by jerome1232 on 2008-12-17
Try it like this

System->Prefrences->Main Menu

Scroll to the bottom (right hand pane) select "new seperator", then select "new item"

input this

Name: Add/Remove...
Command: /usr/bin/gnome-app-install
Comment: Install and remove applications

Now I'm not using a default icon so I have no idea where the default one is, prbly /usr/share/pixmaps or something you'll have to search around.

hope that helps.

---

### Post by SunnyRabbiera on 2008-12-17
> **HotShotDJ said:**
> When you removed synaptic and then reinstalled, it is likely that the Add/Remove Applications software was removed as well.  Go into Synaptic Package Manager and search for gnome-app-install.  If it is not installed, then install it.  This should get you fixed up.

Indeed, but really its up to you.
Personally I would not bother reinstalling add/remove as I personally find synaptic a better application and I also find it very easy to use.
Add/remove is a good starting point however, but synaptic to me is better.

---

### Post by megatotz on 2008-12-17
thanks a lot! i used the first suggested way by HotShotDJ- worked fine. 
i'm happy now.:p

---

### Post by HotShotDJ on 2008-12-17
> **SunnyRabbiera said:**
> Personally I would not bother reinstalling add/remove as I personally find synaptic a better application and I also find it very easy to use.I, personally, agree with you.  However, the OP didn't ask for an opinion of the application, only how to get it back. :)

---

### Post by SunnyRabbiera on 2008-12-17
> **megatotz said:**
> thanks a lot! i used the first suggested way by HotShotDJ- worked fine. 
i'm happy now.:p

Still in the near future I would ween myself from add/remove.
About a month or so of experience for the average user.

> **HotShotDJ said:**
> I, personally, agree with you.  However, the OP didn't ask for an opinion of the application, only how to get it back. :)

I know, but I wanted to make the OP aware there is no danger in using synaptic and add/remove is sort of not needed if synaptic is working.
I understand add/remove is simple and straightforward but so is synaptic.
Just making sure he doesnt feel fearful about using synaptic thats all.

---

