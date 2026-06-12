---
title: "How to get the bottom taskbar in Unity to switch between applications?"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by Hotshot5000 on 2011-05-06
I upgraded to 11.04 and the default desktop is Unity. I started like two apps and apart from the stupid idea of moving the menu to the upper taskbar I realized that I cannot switch between applications since there is no bottom taskbar. So how do I get that taskbar in Unity? I want to be able to switch between applications just like in classic gnome in one click, fast and easy.

---

### Post by r-senior on 2011-05-06
You can. Click on the icon in the launcher. If the launcher isn't visible, move your mouse extreme left and it will pop out from the edge of the screen. The running applications have a white arrow on the left side, the focused application has a white arrow on the right side.

You may also want to use Compiz Config Settings Manager to adjust settings on the Unity Plugin. For example, you can change the icon size, set the launcher to be visible all the time rather than autohide, and you can also have running applications backlit (highlighted) in the launcher.

EDIT: At your leisure, you may want to look at some of the HOWTOs and videos.

[http://ubuntuforums.org/showthread.php?t=1742326](http://ubuntuforums.org/showthread.php?t=1742326)

---

### Post by Hotshot5000 on 2011-05-06
I find the autohide feature of the left panel annoying. I mean I have to wait for it to appear and then scroll down to the app and click it. Waaaay more complicated than the simple all opened applications on the taskbar click on which you want to bring in front. Is this supposed to be an improvement over the previous gnome 2.3 or just some experiment by some crazy programmers?

I switched back to gnome classic. If they are putting manpower into this new interface then this whole distribution is headed down the drain. There are many bugs to be fixed in the 2.3 gnome. They haven't finished those and they are already moving on? Does nobody see that it's more complicated now to do what was easy in previous version? And why is that panel in the left? What if I want to move it to the bottom? Is this even possible?

---

### Post by r-senior on 2011-05-06
> **Hotshot5000 said:**
> I find the autohide feature of the left panel annoying.
You can turn the autohide off, as explained above.

> Is this supposed to be an improvement over the previous gnome 2.3 or just some experiment by some crazy programmers?
In short, Gnome 2.x is not being developed (unless someone takes it on). The Gnome project has gone for Gnome Shell as its interface but Canonical didn't like the lack of customisation options for Ubuntu branding. Unity is a response to Gnome abandoning the old panel interface that the world has become accustomed to since 1995. It is a work in progress, a first cut.

> There are many bugs to be fixed in the 2.3 gnome. They haven't finished those
"They" are not one entity or corporation. Canonical have developed Unity. Gnome maintained Gnome 2.3 but are now focusing on Gnome Shell. It's not a simple matter of "them" and "us".

> And why is that panel in the left? What if I want to move it to the bottom? Is this even possible?
It is not currently possible. The reasoning behind being at the side is that monitors are wider than they used to be.

Mark Shuttleworth discussed the lack of configuration this week and it suggests that more configuration is probable in the future.

> “Why did you decide to make [Unity] less customisable”

In Unity, we have a very tight set of options. Part of that is because it’s a 1.0, and we wanted to focus on the things people will most enjoy and most need; part of that is because we know every option has a high cost, and not every option is equally used.

---

### Post by ajgreeny on 2011-05-06
> **Hotshot5000 said:**
> I find the autohide feature of the left panel annoying. I mean I have to wait for it to appear and then scroll down to the app and click it. Waaaay more complicated than the simple all opened applications on the taskbar click on which you want to bring in front. Is this supposed to be an improvement over the previous gnome 2.3 or just some experiment by some crazy programmers?

I switched back to gnome classic. If they are putting manpower into this new interface then this whole distribution is headed down the drain. There are many bugs to be fixed in the 2.3 gnome. They haven't finished those and they are already moving on? Does nobody see that it's more complicated now to do what was easy in previous version? And why is that panel in the left? What if I want to move it to the bottom? Is this even possible?
+1
I think, however, we are beginning to be part of a minority, and from what I have seen on this forum, a lot of users seem to like the unity desktop, or in other cases the gnome-shell of gnome 3.   I can only get either of those to work on my netbook, not my desktop nor laptop, so I have no idea what will happen when the classic desktop of gnome 2 goes totally from the gnome stable;  what then will those two machines default to?

If the classic desktop does disappear completely, as is being suggested for 11.10 or 12.04, I shall look elsewhere, though I hope still to stay with the ubuntu family, as I now know and understand the setup of the systems and how everything works.  Either Xubuntu or Lubuntu are top of my options at the moment.

---

### Post by Hotshot5000 on 2011-05-06
I agree it's just that I feel that if you cannot make application switching instant then something is just very wrong about the interface. It seems to me that this is just change for the sake of change. It just does not improve anything and makes things worse. Plus you need to learn to do what you knew to do well for 10 years now. If they made it default it means that they recommend it, which is just unbelievably wrong in the current state. This interface could and does scare newcomers.

I also heard that the classic gnome will no longer be an option in the next Ubuntu version so these guys are shoving down our throats a stupid interface that is worse than what we have (had). I wonder what are they trying to accomplish or if it's just a joke.

Also is there any petition to sign so the guys working on this at least know the opinion of the users?

---

### Post by Carborundum on 2011-05-06
> **Hotshot5000 said:**
> I find the autohide feature of the left panel annoying. I mean I have to wait for it to appear and then scroll down to the app and click it. Waaaay more complicated than the simple all opened applications on the taskbar click on which you want to bring in front. Is this supposed to be an improvement over the previous gnome 2.3 or just some experiment by some crazy programmers?

I switched back to gnome classic. If they are putting manpower into this new interface then this whole distribution is headed down the drain. There are many bugs to be fixed in the 2.3 gnome. They haven't finished those and they are already moving on? Does nobody see that it's more complicated now to do what was easy in previous version? And why is that panel in the left? What if I want to move it to the bottom? Is this even possible?
You can create a normal gnome panel and customize it however you want, even if you use Unity. Just enter the command "gnome-panel" in the terminal. If you want it to launch at startup, put the command in Startup Applications.

---

### Post by r-senior on 2011-05-06
> **Hotshot5000 said:**
> I agree it's just that I feel that if you cannot make application switching instant then something is just very wrong about the interface.
It is instant. Just click on the icon. You can have the launcher always visible or autohide, just as with the panel. 

The area where some people find it deficient is with multiple instances of an application or the fact that the launcher is common to all workspaces but switching between different applications is one click - exactly the same as with the panel.

---

### Post by mtangoo on 2011-05-06
Super Key [Windows key]+W and you have open and active (unminimized) app in screen. Just click the one you wan or just use <---- and ----> keys and return key

Stefano

---

### Post by ajgreeny on 2011-05-06
> **mtangoo said:**
> Super Key [Windows key]+W and you have open and active (unminimized) app in screen. Just click the one you wan or just use <---- and ----> keys and return key

Stefano
But that is still more long-winded than a single click in the panel, isn't it?

I prefer to use the mouse to move from app to app, rather than two keyboard keys and then the mouse.

---

### Post by mtangoo on 2011-05-06
Then use alt+tab key
That is what I can think of as "replacement" for the panel thing.
Else, set classic version as default until they add that option to Unity

---

### Post by Hotshot5000 on 2011-05-06
It's really interesting how smart people can come to such stupid design decisions... Scientists should probably study these kind of things. Who knows what we may discover. Alt-tab?? Is that the best they could come up with? We already had alt-tab since windows 95. And Win 95 also had a taskbar.. Why are these guys so against a taskbar? It's simple efficient and gets the job done without me having to use the keyboard. Don't change for the sake of change. There is absolutely nothing wrong with the taskbar. Every windows user is familiar with it. You expect people to switch from windows to something that is completely unfamiliar to them and embrace it? There are many things to be improved in linux. But then again people don't want to hunt bugs in rotten assembly code. They want to design new l33t interfaces that need manuals in order to be able to switch between apps....

---

### Post by scott-ian on 2011-05-06
See this: [http://gregcor.com/2011/04/12/get-a-taskbar-in-gnome-3gnome-shell/](http://gregcor.com/2011/04/12/get-a-taskbar-in-gnome-3gnome-shell/)
It is for Gnome 3, but it should work in unity.
Edit: The bar its self is for something else.  Works  great and is very customisable.

---

### Post by Carborundum on 2011-05-06
> **scott-ian said:**
> See this: [http://gregcor.com/2011/04/12/get-a-taskbar-in-gnome-3gnome-shell/](http://gregcor.com/2011/04/12/get-a-taskbar-in-gnome-3gnome-shell/)
It is for Gnome 3, but it should work in unity.
Edit: The bar its self is for something else.  Works  great and is very customisable.
Am I invisible? It is _dead simple_ to create a taskbar in Unity:
```
gnome-panel
```That's it. Customize away.

---

### Post by r-senior on 2011-05-06
Apart from multiple instances and the issue of not segregating apps between workspaces, I really don't get how people are finding it difficult to switch between applications using the launcher. I can think of more substantial issues to complain about with Unity. I don't see how application switching is that much different from the panel?

---

### Post by lotharmat on 2011-05-06
I use 2 computers at work

Windows 7 with dial monitors (1 and 2) and  Ubuntu on a docked laptop with an external monitor (3) I use synergyc to share the windows mouse and keyboard.

The desk setup is like this:

1 ---- 2 ---- 3

I'd love to be able to get the Unity bar on the right hand side of the monitor so the autohide works properly.

I do hope they sort this - Windows 7 is currently more configurable.

What is the world coming to? 

There is a war and the Germans want no part of. The French started the air assault in Libya, the best golfer in the world is black and the best rapper is white. Windows is more configurable than Ubuntu. It's all backwards I tell you. ;)

* Disclaimer: None of the bottom of this post is intended to cause offence - If any is caused; I apologise.

---

### Post by rockneverdies on 2011-07-24
Unity is really beautiful. Except its switching ability between multiple applications.

It looks like designers of it really never thought about the users that are working with at least 5-7 different application windows running at the same time and need to switch between those applications quickly and efficiently.  

I think it should be the first thing the designers need to rethink about.

---

### Post by lwalper on 2011-07-25
> **r-senior said:**
> At your leisure, you may want to look at some of the HOWTOs and videos.
Howtos and videos? I just want something that works out-of-the-box. So far, for me at least, Ubuntu has not been able to provide that experience. I've been playing with this for several years and still have found only a very few apps that actually work as advertised. It seems there's always a "go to the terminal ..." enter some esoteric strings of gobblydygook, scratch your head and wonder why that didn't work - then go back to Windoze to accomplish some simple task.

Though I appreciate the concept of "open source," there's nothing like the free market to bring products to fruition. If it doesn't work, nobody will buy it. If it's free, everyone wants it, but it's often served half baked and unpalatable.

---

### Post by malspa on 2011-07-25
> **Carborundum said:**
> Am I invisible? It is _dead simple_ to create a taskbar in Unity:
```
gnome-panel
```That's it. Customize away.

I guess you ARE invisible. Folks, if you want "a bottom taskbar in Unity to switch between applications," why not simply do as Carborundum suggests?

---

### Post by walt.smith1960 on 2011-07-25
> **malspa said:**
> I guess you ARE invisible. Folks, if you want "a bottom taskbar in Unity to switch between applications," why not simply do as Carborundum suggests?

Throw me on the "dense" pile.  Gnome-panel answers one of my big wishes for Unity.  I wonder if this will be available in 11.10 and subsequent?

---

### Post by malspa on 2011-07-25
> **walt.smith1960 said:**
> Gnome-panel answers one of my big wishes for Unity.  I wonder if this will be available in 11.10 and subsequent?

Good question. I'm thinking that it won't be there by default but maybe it could be installed from the repos.

Another option might be xfce4-panel, which would bring in a lot less stuff than if you tried to add gnome-panel. I don't see why it wouldn't work, but I haven't tried it in Unity yet. However, I use xfce4-panel in Openbox in Lucid.

---

### Post by Gone fishing on 2011-07-25
I like Unity, however I can see that switching between open applications is not a strong feature of this user interface. I wonder if something like the BeOS tracker wouldn't fit nicely on the top bar and make switching between and controlling open applications easier.

---

### Post by wildmanne39 on 2011-07-25
Hi, I installed awn launcher and put it at the bottom of the screen with an applet on it that has the old gnome2 menu of apps in it.

I have the launcher set to hide it only comes out if I hit the super key. Here is a screenshot.

---

### Post by beew on 2011-07-25
> **wildmanne39 said:**
> Hi, I installed awn launcher and put it at the bottom of the screen with an applet on it that has the old gnome2 menu of apps in it.

I have the launcher set to hide it only comes out if I hit the super key. Here is a screenshot.

It is a band aid but doesn't really address the design issue,--I know it was not your purpose to talk about design issue, I just want to bring it up. :)  Why would you need two docks with have basically the same functions only that awn does it better and have more options?

If the Unity bar is well designed you shouldn't need AWN. If not you should be able to get rid of the Unity bar instead of just hiding it. It is just not elegant to have two apps with similar functions even when one is hidden.

Another weird "feature" (it is by design) of Unity is that you can't minimize and open application by clicking the icon on the Unity bar.

Mind you I am saying this not as a Unity hater, I actually find it quite usable after some of the worse bugs have been cleared up and some customizations (like restoring the tray icons and getting rid of the global menu) I have no issue switching to the new UI (though I can see it would be a difficult sell to people steep in Windows habits, the very people that Ubuntu wants to attract)

P.S. I don't think it is possible to put a second dock in gnome-shell so in that sense Unity is more customizable. :)

---

### Post by malspa on 2011-07-25
> **wildmanne39 said:**
> I have the launcher set to hide it only comes out if I hit the super key.

How do you do that?

---

### Post by Anuovis on 2011-07-25
I just added the bottom panel and removed it again happily after minutes. Just clusters up the vertical space and displays something I really don't need to look at all the time.

I agree this could be handled somewhat more efficiently but alt-tab or the menu on the left might not be as bad as they seem. Unity is still a fresh product and some features are lacking, I suspect. You can't build it in one day and this release is not a long-term support version, therefore it will be somewhat experimental and maybe not polished in parts.

If you can't be productive with Unity, there is still Gnome, Gnome Classic, Xcfe, KDE. All have such panels by default at the moment. 

You could also use different workspaces instead of shuffling all windows on just one. Hit Super+S and you will get an overview. Hit Super+W and you will get an overview of all windows in the current one.

I personally love Unity and wouldn't trade it for anything else, it has been the smoothest Ubuntu ride so far. But it took some time to get used to.

---

