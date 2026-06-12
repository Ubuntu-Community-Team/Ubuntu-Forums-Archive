---
title: "Networking Shares / Connect to Server"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by AgentZ86 on 2007-10-26
Hi

I've used the Networking Connect to Server feature to create a shortcut on my desktop for my shared folders on the local server.

But some programs won't recognize that shortcut I can't browse to a file or see the shortcut on the desktop, with many programs. I can click the desktop shortcut and browse and use files but many programs won't do this.

Example I create a new Kompozer webpage and then want to save to or save as.
Well I can only save to local folder, then I have to use Nautaulist to copy and past into my shortcut to the server.

I have no other problems other then the programs no being able to see these shortcuts.

I tried to make link but that wo'nt work says some error message so I'm guessing that gnome does not have the ability to make link with server files.

Anyhow Please advise this is very annoying I can't seem to figure this out.

KDE always could make link on these server files etc.

And not every programs has this problem but many do. Gthumbs works seems to work fine and can see my shortcuts to the server.

:confused:

---

### Post by jfrorie on 2007-10-28
> **AgentZ86 said:**
> Hi

I've used the Networking Connect to Server feature to create a shortcut on my desktop for my shared folders on the local server.

But some programs won't recognize that shortcut I can't browse to a file or see the shortcut on the desktop, with many programs. I can click the desktop shortcut and browse and use files but many programs won't do this.

Example I create a new Kompozer webpage and then want to save to or save as.
Well I can only save to local folder, then I have to use Nautaulist to copy and past into my shortcut to the server.

I have no other problems other then the programs no being able to see these shortcuts.

I tried to make link but that wo'nt work says some error message so I'm guessing that gnome does not have the ability to make link with server files.

Anyhow Please advise this is very annoying I can't seem to figure this out.

KDE always could make link on these server files etc.

And not every programs has this problem but many do. Gthumbs works seems to work fine and can see my shortcuts to the server.

:confused:

I think you've created a network share under Nautilus.  IIRC, nautilus shares only appear under gnome compliant apps.  Under gnome, I don't think any KDE apps will see the share.  If you want them to, you will need to mount them under fstab at the O/S level, not desktop.

Jim

---

### Post by AgentZ86 on 2007-10-29
> **jfrorie said:**
> I think you've created a network share under Nautilus.  IIRC, nautilus shares only appear under gnome compliant apps.  Under gnome, I don't think any KDE apps will see the share.  If you want them to, you will need to mount them under fstab at the O/S level, not desktop.

Jim

Darn, thats really a pain, cause all my KDE apps use to simply copy and paste to desktop, and then a link would come up to either copy/link/move etc. 

I'm having fun with my ?Gnome desktop, but I'm not sure how to mount them under fstab.

But what about samba shares shouldn't they  be able to link either Gnome or KDE apps ??

Thats how I basically have the shares setup on an SME server but using the samba windows share feature on the SME linux server. ??

Anyhow thanks

---

### Post by jfrorie on 2007-10-29
> **AgentZ86 said:**
> Darn, thats really a pain, cause all my KDE apps use to simply copy and paste to desktop, and then a link would come up to either copy/link/move etc. 

I'm having fun with my ?Gnome desktop, but I'm not sure how to mount them under fstab.

But what about samba shares shouldn't they  be able to link either Gnome or KDE apps ??

Thats how I basically have the shares setup on an SME server but using the samba windows share feature on the SME linux server. ??

Anyhow thanks

Both gnome and KDE let you create samba share painless, but they only work work with their compliant apps.  Gnome Nautilus will let you mount samba share similar to the KDE way without going through fstab.  If you want to mount a persistent share that will see by both without setting them up under each window manager, you need to use fstab.

---

### Post by AgentZ86 on 2007-10-31
Thanks

---

### Post by AgentZ86 on 2007-11-06
> **jfrorie said:**
> Both gnome and KDE let you create samba share painless, but they only work work with their compliant apps.  Gnome Nautilus will let you mount samba share similar to the KDE way without going through fstab.  If you want to mount a persistent share that will see by both without setting them up under each window manager, you need to use fstab.

One more app I noticed a problem with among others--, Firefox ?
When in firefox lets say you want to save page using the firefox (save page as) feature.
Well you get your normal sort of Nautilus file browser screen where you see the locations in which to save your page etc. 
But I notice that my connect to server shortcut links from my desktop are not shown here. So I can't save pages to my server.basically only to the local folders. This is strange and should be typical to see your shortcuts on the desktop from within save as feature. Shouldn't it ?

Please advise ?

---

### Post by jfrorie on 2007-11-06
> **AgentZ86 said:**
> One more app I noticed a problem with among others--, Firefox ?
When in firefox lets say you want to save page using the firefox (save page as) feature.
Well you get your normal sort of Nautilus file browser screen where you see the locations in which to save your page etc. 
But I notice that my connect to server shortcut links from my desktop are not shown here. So I can't save pages to my server.basically only to the local folders. This is strange and should be typical to see your shortcuts on the desktop from within save as feature. Shouldn't it ?

Please advise ?

IIRC, Firefox uses neither the gnome or KDE toolkit, thus doesn't have access to eithers extentions.

Jim

---

### Post by AgentZ86 on 2007-11-07
> **jfrorie said:**
> Both gnome and KDE let you create samba share painless, but they only work work with their compliant apps.  Gnome Nautilus will let you mount samba share similar to the KDE way without going through fstab.  If you want to mount a persistent share that will see by both without setting them up under each window manager, you need to use fstab.

Hi

What about doing it the fstab method and if the server gets restarted or for some reason can't find shared files. ??

Will this cause major problems with starting ubuntu ? or no big deal ?

Also is there a clickety method to edit fstab to include my server shares ?

Thanks for the help:)

---

### Post by jfrorie on 2007-11-07
> **AgentZ86 said:**
> Hi

What about doing it the fstab method and if the server gets restarted or for some reason can't find shared files. ??

Will this cause major problems with starting ubuntu ? or no big deal ?

Also is there a clickety method to edit fstab to include my server shares ?

Thanks for the help:)

Unfortunately, my knowledge in this area is purely theoretical.  I really don't know the effect of mounting a samba share that times outs. :(

try linneighborhood. This thread has some more info on what you are doing I think:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

