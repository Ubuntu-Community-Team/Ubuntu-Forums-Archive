---
title: "package for selecting desktop environment"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Binny88 on 2009-02-05
I i have heard that there is a package in synaptic which will enable users to select there desktop environment at login,

Does anyone know of any such package or anything like that

I use gutsy gibbon:)

---

### Post by snowpine on 2009-02-05
You don't need any extra packages.

From the login screen (assuming you are using gdm, which is standard in ubuntu), just click Session then choose which desktop environment you want to use.

Or is your question "how do I install the ___ desktop environment?"

---

### Post by Binny88 on 2009-02-05
> **snowpine said:**
> You don't need any extra packages.

From the login screen (assuming you are using gdm, which is standard in ubuntu), just click Session then choose which desktop environment you want to use.

Or is your question "how do I install the ___ desktop environment?"

Okay thanks for the advice can we install two desktop environments at the same time(not running them at the same time). If so could u please tell me how?

Thanks in advance.

---

### Post by snowpine on 2009-02-05
It depends on which desktop environment. :)

Let's take Xfce as an example. You could do this:

```
sudo apt-get install xfce4
```

That will give you a very basic Xfce desktop. Or, if you want everything pre-configured like in Xubuntu:

```
sudo apt-get install xubuntu-desktop
```

Either way, you need to log out, then click Sessions, and choose Xfce. Or, you can choose Gnome to get back to Ubuntu (assuming Ubuntu was your starting point).

---

### Post by RedMartin on 2009-02-05
> **snowpine said:**
> It depends on which desktop environment. :)

Let's take Xfce as an example. You could do this:

```
sudo apt-get install xfce4
```

That will give you a very basic Xfce desktop. Or, if you want everything pre-configured like in Xubuntu:

```
sudo apt-get install xubuntu-desktop
```

Either way, you need to log out, then click Sessions, and choose Xfce. Or, you can choose Gnome to get back to Ubuntu (assuming Ubuntu was your starting point).

Does that apply to KDE 4.2? I'd like to install that but without all the K applications. Possible?

---

### Post by snowpine on 2009-02-05
> **RedMartin said:**
> Does that apply to KDE 4.2? I'd like to install that but without all the K applications. Possible?

I don't think KDE4.2 will ever be available in the Gutsy repositories, sorry.

(edit) But you could install KDE 3 with:

```
sudo apt-get install kde-core
```

ps packages.ubuntu.com is a great way to see what's in which release!

---

### Post by Binny88 on 2009-02-05
Does anyone know where to get good looking gnome themes. unfortunately i cannot try kde since i have a very slow 56kbps internet connection.

Again thanks in advance.

---

### Post by snowpine on 2009-02-05
A good place to start is [www.gnome-look.org](www.gnome-look.org)

---

### Post by RedMartin on 2009-02-05
> **snowpine said:**
> I don't think KDE4.2 will ever be available in the Gutsy repositories, sorry.

(edit) But you could install KDE 3 with:

```
sudo apt-get install kde-core
```

ps packages.ubuntu.com is a great way to see what's in which release!

Oops! I missed the bit about Gutsy. I'm on Intrepid. Would it still be kde-core and would I be missing anything from the KDE experience by not installing kubuntu-desktop?

---

### Post by snowpine on 2009-02-05
> **RedMartin said:**
> Oops! I missed the bit about Gutsy. I'm on Intrepid. Would it still be kde-core and would I be missing anything from the KDE experience by not installing kubuntu-desktop?

I am not a KDE user so the best I can do is give you these links:

[http://packages.ubuntu.com/intrepid/kde-core](http://packages.ubuntu.com/intrepid/kde-core)
[http://packages.ubuntu.com/intrepid/kubuntu-desktop](http://packages.ubuntu.com/intrepid/kubuntu-desktop)

This will show you the exact difference between kde-core and kubuntu-desktop. Generally speaking, if it has a "-desktop" at the end, it includes lots of applications, artwork, etc.

---

### Post by anjilslaire on 2009-02-05
regardless of which version you have, gutsy/hardy/intrepid, its:

```

sudo apt-get install kubuntu-desktop

```

Then read 
[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

---

