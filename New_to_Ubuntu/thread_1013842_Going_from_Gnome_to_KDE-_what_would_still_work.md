---
title: "Going from Gnome to KDE- what would still work?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-12-17
I'm new to linux (about 3 weeks), and I use gnome ubuntu 8.04- I'm thinking of wiping it all out, starting over with Kubuntu for the KDE environment that will supposedly let me organize by track number in the file viewer, which gnome for some reason doesn't support. A big part of my computer usage is music, so that really ticks me off.

I just started to grasp linux, but now I'm left wondering, what still works in Kubuntu? Can I get compiz-fuzion to work on it too? What about Open Office? Emerald? Is it any different at all? If so, what can KDE do that Gnome can't? visa versa?

Forgive me if this is a stupid question, but I can't help but ask, as it's like looking at two different types of apples again for me, like XP and linux all over again before I switched.

---

### Post by Michael.Godawski on 2008-12-17
For a brief overview have a look here:

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

All applications should run on both systems. Sometimes there are special kde applications, but you can run every gnome based software on kde too.

---

### Post by handydan918 on 2008-12-17
KDE is just a desktop environment. Open Office will be the same. In fact, you don't really need to wipe Gnome to install KDE. You can just add it via synaptic or apt-get.

[See this article.]("http://www.psychocats.net/ubuntu/kde")

BTW, if you haven't tried amarok for music playback and management, give it a shot. It makes keeping track of your music easy.

---

### Post by BastardNamban on 2008-12-17
Michael, that was really helpful!

It seems KDE is much more serious looking with all the menu options.
Gnome works fine for me, but I wonder what display options differ between nautilus and Konquerer for file viewing.

I like that I can try both on one setup! I will try that when I get a chance.

---

### Post by philinux on 2008-12-17
> **BastardNamban said:**
> Michael, that was really helpful!

It seems KDE is much more serious looking with all the menu options.
Gnome works fine for me, but I wonder what display options differ between nautilus and Konquerer for file viewing.

I like that I can try both on one setup! I will try that when I get a chance.

As per the previous thread. You can just install konqueror on its own, instead of full kde, if you wish. It will install some extras files it needs.

---

### Post by BastardNamban on 2008-12-17
Konquerer or Dolphin? Here you say Konqueror, there you mention Dolphin. Which is what?

---

### Post by Therion on 2008-12-17
> Dolphin is not intended to be a competitor to Konqueror: Konqueror acts as universal viewer being able to show HTML pages, text documents, directories and a lot more, whereas Dolphin focuses on being only a file manager. This approach allows to optimize the user interface for the task of file management.

[http://dolphin.kde.org/](http://dolphin.kde.org/)

[http://www.konqueror.org/](http://www.konqueror.org/)

---

### Post by BastardNamban on 2008-12-17
Ahh, I see. Thank you Therion. I guess I should indeed try Dolphin.

---

### Post by mrbiggbrain on 2008-12-17
Konquerer is a webbrowser/file viewer/file manager it has many tasks similar to how a web browser would handle files, but can acess your computers files directly.

doplphin is the half replacement to Konquerer, it replaces the filemanager options but leaves konqerer to hanle the web browser functions.

in theroty eaither would work, i douno how many more dependencys dolphin has, but i think it might be more threaded into KDE4/KDE4.[1/2]

again im only somewhat exspierience with Konquerer and even less with dolphin, so i dont know it all

---

### Post by SuperSonic4 on 2008-12-17
I know dolphin has a terminal embedded into it so it would have to install konsole as a dependency

---

### Post by waspbr on 2008-12-17
why would you need to remove gnome? just go to synaptic and add this line to your sources (synaptic>settings tab>sources>thirdparty app tab)

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```

reload (refresh) and search for 

```
kde-kubuntu-desktop
```

check the box and press apply, synaptic should provide all the necessary dependencies, (if it ask you to chose between desktop managers, choose gdm)

then log out (I would actually restart), you will see that in the sessions menu of your login screen (gdm [you could choose kdm but I would chose gdm I like it better]) KDE4 is listed. select it and loging as usual. 

welcome to kde4 (though I prefer gnome)

to get back to gnome  just select "gnome" in the sessions menu. 

you can do the same thing with XFCE by installing the package xubuntu-desktop in synaptic, it´s already in the repos so there's no need to add sources.

REF: [http://http://www.my-guides.net/en/content/view/120/26/]("http://http://www.my-guides.net/en/content/view/120/26/")

enjoy

---

### Post by BastardNamban on 2008-12-17
I was advised against adding any intrepid debs to my source list due to stability issues that could arise in my ubuntu (I use Hardy) when I tried to install Open Office 3.0 earlier. I'm not sure that's a good idea. Shouldn't Dolphin be in the hardy repos already?

---

### Post by SuperSonic4 on 2008-12-17
Not necessarily - there was a fork between d3lphin and dolphin between KDE3.5 and KDE4 both of which where in hardy. The former might be there still and konqueror should be.

The cleanest way would be to put your music on it's own partition and dual boot ubuntu and kubuntu so there are no overlaps, I found having both was too cluttered but it is up to you

---

### Post by BastardNamban on 2008-12-17
I was just about to ask- brought up Synaptic, and in my hardy repo 2 versions of Dolphin show up- dolphin (0.9.0.2ubuntu6.1) and dolphin-kde4 (4:4.0.3.0ubuntu2). The former has a little ubuntu logo next to it, leaving me to believe it's more stable?

Which should I put in? And putting music on a separate partition??? Why would things suddenly become more cluttered if I used Dolphin instead of Nautilus- it's just a different way to view the files & folders, it shouldn't duplicate them or anything?

I have to get to bed, it's 1 am in Japan and I start work tomorrow.

---

### Post by SuperSonic4 on 2008-12-17
ah you only wanted dolphin? Please disregard my last post, I thought you wanted kubuntu desktop.

The former is more stable and I prefer it to dolphin for KDE4 although I'm not entirely sure if the former is maintained. I'd go for the former anyway, I prefer it because of the sidebar and having more plugins/right click options.

If you do get dolphin you might be interested in the pacpl audio converter:  [http://pacpl.sourceforge.net/](http://pacpl.sourceforge.net/) for right click transcoding, it has a dolphin, amarok and konqueror plugin although you can exclude during ./configure
```
./configure --without-amarok --without-konq
```

---

### Post by waspbr on 2008-12-18
sorry didn't realize you were on hardy, that is no problem at all, the same repo is available for hardy, just substitute the word intrepid by the word hardy:

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

---

