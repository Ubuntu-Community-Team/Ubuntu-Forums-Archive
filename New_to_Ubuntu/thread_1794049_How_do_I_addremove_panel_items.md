---
title: "How do I add/remove panel items?"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Linksku on 2011-06-30
I have Ubuntu 11.04 with Gnome.

---

### Post by haqking on 2011-06-30
> **Linksku said:**
> I have Ubuntu 11.04 with Gnome.


right click on the item to remove, right click on panel and choose add

---

### Post by Linksku on 2011-06-30
The right click menu is the same as the left click. For example, when I right click the mail icon, the only option is "Set up mail..."

---

### Post by Elfy on 2011-06-30
You need to be a bit more specific about what you're trying to do - if you are using the new unity panel it is a whole lot different than it used to be.

There's a bunch of stuff here [http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

Wish I could help more but I'm not using it.

---

### Post by haqking on 2011-06-30
> **Linksku said:**
> The right click menu is the same as the left click. For example, when I right click the mail icon, the only option is "Set up mail..."


Your original post said you were using 11.04 with Gnome ?

or are you using unity which is a shell on Gnome ?

if you are using what you said which is Gnome (which i am assuming as classic) then right clicking the panel should give you options such as adding to it ?

can you show us a screen dump of what you mean ?

---

### Post by mcduck on 2011-06-30
If you are using classic Gnome, and not Unity, then the right-clicking on the panel should work. If it doesn't, then press Alt-F2, run "gconf-editor", browse to *apps/panel/global* and make sure the *locked_down* -key is disabled.

If you are using Unity, then the top panel doesn't support panel applets. Look for Indicator applets to add new features to the top panel instead. What comes to the Launcher in Unity, just start the apps you want and you can right-click their icon & select "Keep in Launcher".

---

### Post by Linksku on 2011-06-30
Sorry, I am using Unity. I thought I was using Gnome (new to Ubuntu). I will do some Googling on Unity panels. Thanks!

---

### Post by Elfy on 2011-06-30
You are using gnome. 

People get confused - unity is running in gnome. If you login with the classic desktop then it works like the old gnome2 panels.

It's just a bit easier at the moment to say unity ;)

---

### Post by haqking on 2011-06-30
> **forestpiskie said:**
> You are using gnome. 

People get confused - unity is running in gnome. If you login with the classic desktop then it works like the old gnome2 panels.

It's just a bit easier at the moment to say unity ;)

yeah sorry about that, i meant it in classic.  I understand Unity is a shell on Gnome, my bad ;-)

---

### Post by Elfy on 2011-06-30
:lol: Didn't actually mean you.

If the OP ventures into the cafe looking for unity ...

---

