---
title: "Terminal/Root Terminal and Text Editing in it"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Happyisgood on 2009-03-16
I came to Ubuntu from Debian and one thing that I've noticed is missing in Ubuntu is a root terminal (I am aware that I can act as a root user by using the "sudo" command.)  But I was wondering if there was a terminal mode where I do not need to use the "sudo" every line.

I also noticed that the command 'su' requests a password, however it rejects my password that I have set and I know I didn't set a specific root password upon setup.  Also trying to access a root account in console mode (ctr. alt. f1) gives me a password failure.

Is there a root terminal, and do I even HAVE a root account?

Also, an in terminal text editor with some decent structure.  Lacking a root account, while configuring my trackpad I used the command 'sudo pico Trackpad.fdi' and it opened it up with pico.

I found pico nicer than the first program I was suggested to use (can't even remember what it was called) but I was looking for a program which is easy for me to use and navigate with, seeing as for me to finish my MacBook config I have to mess with a ton more system files, and I want something easy to use so I don't make a mistake and delete any drivers that might be important.

So to simplify...

a) Is there a root account on Ubuntu?
b) If so what is the password?
c) If so is there a root terminal?
d) What is the easiest text editor to use in a terminal?

Thanks again in advance for your help!
Happyisgood

---

### Post by blueridgedog on 2009-03-16
Open a terminal. then

```
sudo su
```

---

### Post by m_duck on 2009-03-16
a) There is but by default it is disabled. See [here]("https://help.ubuntu.com/community/RootSudo") for the hows, whys and workarounds.

b) No password by default until it is enabled. Well, I think it's disabled by an "impossible password" - it's probably mentioned in the aforementioned link.

c) Root terminal either as blueridgedog said, and I think there are another couple of methods mentioned in the link. Also, if you're using GNOME, you should be able to right click your menu, then "Edit menus" and somewhere you should be able to tick a box to allow the "Root terminal" to be shown - I may be wrong here but I think there is an option. If it is the case, it will probably be the equivalent of running "gksu gnome-terminal".

d) I like to use nano which is an "improved pico editor".

---

### Post by Happyisgood on 2009-03-16
So to use nano the command would be (using my above example)

sudo nano trackpad.fdi

or would it be something like

sudo pico-nano trackpad.fdi

also thanks for that help with root, I tend to avoid root if at all possible.

Yeah, I use Gnome, I find that it is easier to navigate and I'm not a master of Linux yet (obviously) I use terminal as much as possible, but console mode only when I need to!

---

### Post by m_duck on 2009-03-17
It would be the former```
sudo nano trackpad.fdi
```While being an "improvement" on pico (I've never actually used pico) it is a separate program. Above code opens trackpad.fdi in nano as a superuser.

I am also far from being masterful - I just like nano!

---

### Post by Bölvaður on 2009-03-17
> **Happyisgood said:**
> b) If so what is the password?
d) What is the easiest text editor to use in a terminal?


b) same as your user account
d) if you used vim in debian like many others... that might be the thing for you to continue to use... so really.. what ever you used in debian you can just download it if it isnt here already.

---

### Post by PriceChild on 2009-03-17
I *think* it is recommended to use ```
sudo -i
``` rather than ```
sudo su -
``` and variants.

---

### Post by m_duck on 2009-03-17
> **PriceChild said:**
> I *think* it is recommended to use ```
sudo -i
``` rather than ```
sudo su -
``` and variants.
Yeah, looking at the link I posted earlier, that is the case - "If you really need a persistent root login, use sudo -i[FONT=Arial]"[/FONT]

---

### Post by issih on 2009-03-17
Not that there is anything wrong with a terminal based text editor, but as you stated you want something easier (and as you state you are using gnome), do bear in mind that you can use the gui text editor by simply doing:

```
gedit filename
```

where filename unsurprisingly is the file you want to edit. That will launch a gui text editor on the file in question.

If you need root to access that file you need to use gksudo rather than just sudo as it is a graphical app.

so its:

```
 gksudo gedit filename
```
Hope that helps

---

### Post by oldos2er on 2009-03-17
In Gnome, I have a menu entry Applications, System Tools, Root Terminal. If you don't have this, you should be able to enable with alacarte.

 If you use Nautilus, install the package nautilus-gksu. This will give you the ability to open a file as administrator in Nautilus' GUI environment, without running Nautilus itself as root.

---

### Post by namegame on 2009-03-17
> **Happyisgood said:**
> 
d) What is the easiest text editor to use in a terminal?


Since your other questions seem to have been answered. I'm obligated to mention Vi(m)/Emacs. They take quite a bit of time to learn, but once you have devoted the time to learn them, they are quite fast/efficient.

---

### Post by blueridgedog on 2009-03-17
> **namegame said:**
> Since your other questions seem to have been answered. I'm obligated to mention Vi(m)/Emacs. They take quite a bit of time to learn, but once you have devoted the time to learn them, they are quite fast/efficient.


Ah...now we get to it!!  Vim for me.  

One of my first post install task for years now has been mv /usr/bin/vi /usr/bin/vi.install and ln -s /usr/bin/vim /usr/bin/vi

However, that said, it really comes down to "what you are used to".

---

