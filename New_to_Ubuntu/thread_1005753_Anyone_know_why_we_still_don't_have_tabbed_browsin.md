---
title: "Anyone know why we still don't have tabbed browsing in 8.04???"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-12-08
I was just wondering why we don't have tabbed browsing in 8.04 for Nautilus.

I haven't heard anything about this anywhere else.

Intrepid 8.10 had it even before it was even released.

Surely Hardy users should get it in the repos soon?

Is there a stability problem with it or something?

---

### Post by Locke_99GS on 2008-12-08
In Nautilus or Firefox?

---

### Post by pluckypigeon on 2008-12-08
> **Locke_99GS said:**
> In Nautilus or Firefox?

Nautilus. Sorry, I should have mentioned that!

They have it in Intrepid.

---

### Post by edd07 on 2008-12-08
> **pluckypigeon said:**
> I was just wondering why we don't have tabbed browsing in 8.04.

I haven't heard anything about this anywhere else.

Intrepid 8.10 had it even before it was even released.

Surely Hardy users should get it in the repos soon?

Is there a stability problem with it or something?
I'm guessing you're talking about Nautilus (since tabbed browsing has been in Firefox since 1.0)

I don't think Hardy users will get it in the standard repos, because Ubuntu only provides security upgrades, not new versions of software.

Maybe in the backports repo? Or if you really need it, you can always compile from source.

BTW, I have Intrepid, and it's not as useful as I thought it would be. Especially because it doesn't have the Ctrl-Click shortcut I use all the time in Firefox to open a new tab

Hope this helps

---

### Post by mk1w86 on 2008-12-08
I think it is because you only get the newer nautilus with tabs in Gnome 2.24 (In Intrepid) whereas Hardy only has Gnome 2.22 and it might break stability if Gnome was updated in Hardy especially considering its an LTS release.

---

### Post by pluckypigeon on 2008-12-08
> **edd07 said:**
> 
Maybe in the backports repo? Or if you really need it, you can always compile from source.

BTW, I have Intrepid, and it's not as useful as I thought it would be.



I have the backports enabled but it's not there as of yet.

I did have Intrepid and did find the tabs quite useful. I don't like having too many programs in the window list.

Unfortunately, I had to reinstall Hardy because compiz blacklisted my card and pulseaudio used to cut out.

---

### Post by pluckypigeon on 2008-12-08
> **mk1w86 said:**
> I think it is because you only get the newer nautilus with tabs in Gnome 2.24 (In Intrepid) whereas Hardy only has Gnome 2.22 and it might break stability if Gnome was updated in Hardy especially considering its an LTS release.

It is a shame that Intrepid is supposed to be stable but at the same time it's not really.

---

### Post by edd07 on 2008-12-08
> **mk1w86 said:**
> I think it is because you only get the newer nautilus with tabs in Gnome 2.24 (In Intrepid) whereas Hardy only has Gnome 2.22 and it might break stability if Gnome was updated in Hardy especially considering its an LTS release.
He's right. Sorry, but I guess it won't be in Hardy, even in the backports.

If you don't want to go through the trouble of updating GNOME, you could try out other file managers. I've only used Thunar apart from Nautilus, but I don't know if it's got tabbed browsing. The KDE file managers (Dolphin and Konqueror) do, if you don't mind running a Qt app within GNOME.

---

### Post by pluckypigeon on 2008-12-08
> **edd07 said:**
> If you don't want to go through the trouble of updating GNOME, you could try out other file managers. I've only used Thunar apart from Nautilus, but I don't know if it's got tabbed browsing. The KDE file managers (Dolphin and Konqueror) do, if you don't mind running a Qt app within GNOME.

I don't really think that is the answer. 

I dislike thunar and dolphin/konqueror and anything kde is just to garish.

I'm going to use opensuse11 for now.. or until I can afford to get new hardware that is compatible to new ubuntu at least!

---

### Post by Sukarn on 2008-12-08
Short answer : no, nautilus or any other part of GNOME will not be updated in Ubuntu 8.04 from 2.22 to 2.24

Explaination : This is to prevent any unstable behaviour in the OS. Once released, Ubuntu offers only security updates and bug-fix updates to the OS.
If you want, you can build the packages yourself (as recommended earlier in the thread) or you could try looking for a ppa or some other repository that hosts updated GNOME packages for Ubuntu 8.04

---

### Post by nhasian on 2008-12-08
what do you mean?  If i Ctrl-Click on a link it opens in a new tab.  You can also just use the middle mouse button to open the link in a new tab.

> **edd07 said:**
> I have Intrepid, and it's not as useful as I thought it would be. Especially because it doesn't have the Ctrl-Click shortcut I use all the time in Firefox to open a new tab

---

### Post by Sukarn on 2008-12-08
> **nhasian said:**
> what do you mean?  If i Ctrl-Click on a link it opens in a new tab.  You can also just use the middle mouse button to open the link in a new tab.

He meant that Nautilus does not have that shortcut, and thus he does not find tabbed-Nautilus to be so useful.

---

