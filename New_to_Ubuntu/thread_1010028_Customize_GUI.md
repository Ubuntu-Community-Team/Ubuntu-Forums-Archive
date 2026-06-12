---
title: "Customize GUI"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Shippou on 2008-12-13
Hello guys...

D you know of any customization tool available in GNOME? What I mean is something like which is found in KDE which is used to make new themes.

---

### Post by sirjoebob on 2008-12-13
I don't know about creating new themes, but you can easily add created ones or modify installed themes by going to system>preferences>appearance.

You can use the customize button to change more detail. If this doesn't answer your question, try to provide more detail as to what you are looking for.

---

### Post by Shippou on 2008-12-13
> **sirjoebob said:**
> I don't know about creating new themes, but you can easily add created ones or modify installed themes by going to system>preferences>appearance.

You can use the customize button to change more detail. If this doesn't answer your question, try to provide more detail as to what you are looking for.

Sorry for the sparse details.

I was looking for a tool that will allow me to tweak preset themes more deeply or make an entirely new one. I am somewhat irritated by the Customize button for its very limited options.

What I want is a customization tool for Ubuntu (if there is one) that lets me edit the color of the taskbar, change icon backgrounds... something like that that will let me edit up to the tiniest detail.

Sorry, I'm a black fanatic, so I am somewhat in need of the app to tailor my needs.

My current theme is attached below. It's based from the Moomex theme. What I want for now is make the toolbar black and the background of the window black. (It is not possible using the Customize button).

---

### Post by oldos2er on 2008-12-13
You can change color or images on the panels by right-clicking on an empty spot, choosing Properties, Background.

---

### Post by mister_pink on 2008-12-13
It is possible to customise all of it, but how easy it is is another matter. A lot of the options are rather scattered I think. I have gnome colo(u)r chooser installed and that allows a lot of things to be changed.

```

sudo apt-get install gnome-color-chooser
```

---

### Post by billgoldberg on 2008-12-13
Just install the gtk theme 'wii-black" from gnome look, they don't come much darker than that.

---

### Post by blackened on 2008-12-13
> **Shippou said:**
> ...What I want is a customization tool for Ubuntu (if there is one) that lets me edit the color of the taskbar, change icon backgrounds... something like that that will let me edit up to the tiniest detail...

```
gedit /path/to/theme/gtkrc
```

---

### Post by sirjoebob on 2008-12-13
> **mister_pink said:**
> It is possible to customise all of it, but how easy it is is another matter. A lot of the options are rather scattered I think. I have gnome colo(u)r chooser installed and that allows a lot of things to be changed.

```

sudo apt-get install gnome-color-chooser
```

I never knew about color chooser until your post. Thanks BTW. I love the extra level of customization i get with it.

---

