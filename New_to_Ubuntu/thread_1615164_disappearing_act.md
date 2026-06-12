---
title: "disappearing act"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by moheganer2 on 2010-11-06
I am new to ubuntu having just installed meercat.I noticed within 2 days my applets for volume control and update manager have disappeared.also i installed vlc and it has also disappeared and i had to reinstall it.are these things normal in linuxland?

---

### Post by sikander3786 on 2010-11-06
> are these things normal in linuxland?

Not at all. :-) How can you assume that? You sure you didn't copy/paste any commands or didn't try something fancy you were not sure about?

How was Ubuntu installed? And where is it installed actually? I assume you are not running it from a thumb drive. Is it a complete install?

---

### Post by Hippytaff on 2010-11-06
The first day I used ubuntu I accidentley deleted the top panel :-)

try
```

dpkg --list | grep gnome-apletts

```

see if your applets are still installed

---

### Post by sikander3786 on 2010-11-06
> **Hippytaff said:**
> The first day I used ubuntu I accidentley deleted the top panel :-)

try
```

dpkg --list | grep gnome-apletts

```

see if your applets are still installed
Found a typo :-)

```
dpkg --list | grep gnome-**apletts**
```

Should be

```
dpkg --list | grep gnome-**applets**
```

---

### Post by Hippytaff on 2010-11-06
> **sikander3786 said:**
> Found a typo :-)

```
dpkg --list | grep gnome-**apletts**
```Should be

```
dpkg --list | grep gnome-**applets**
```

Nice one...thanks sikander :-D

---

### Post by moheganer2 on 2010-11-06
thanks for the replies.The terminal command came up saying various applets but did not list them individually.i installed a different applet for the update manager so i am only down 1-the volume control.i did a complete install of ubuntu with a dual boot with windows.i like ubuntu-windows does even stranger things.

---

### Post by Hippytaff on 2010-11-06
Have you tried right clicking on the panel and add to panel?
Choose "**Indicator Applet**" from the list and click on "**Add**". The volume control should come back.

---

### Post by coffeecat on 2010-11-06
What is the "different applet" for the Update Manager? I've not heard of such a thing.

Also - VLC is not usually in the habit of disappearing spontaneously. Are you sure you didn't just remove it from the menu by editing the menu?

---

### Post by Hippytaff on 2010-11-06
> 
Are you sure you didn't just remove it from the menu by editing the menu?

does it matter? :-)

---

### Post by coffeecat on 2010-11-06
> **Hippytaff said:**
> does it matter? :-)

It does to the OP. :p

---

### Post by moheganer2 on 2010-11-06
when i right click add to panel it did not list a volume control some other nice ones though.i am not smart enough to be editing any thing yet but i will be.thanks for your reply and help.the update applet is just what i added from the administration menu.the original one had a little check mark and was always there when i booted up.

---

### Post by Hippytaff on 2010-11-06
What bout 'indicator applet' ? was that there?

---

### Post by moheganer2 on 2010-11-06
Indicator applet is the correct answer-thank you so much!it also gave back mail indicator which i didnt notice was gone.perservance wins out again.

---

### Post by Hippytaff on 2010-11-06
Perseverance will succeed :-)

If your happy with the outcome mark the thread as solved in the forum tools at the top of the page :-)

---

