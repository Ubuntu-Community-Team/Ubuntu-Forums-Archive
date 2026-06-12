---
title: "Kubuntu ubuntu"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by il pepe on 2009-08-14
I had the clever idea of installing kubuntu in my existing ubuntu jaunty. (via the terminal: install kubuntu)
Now of course lots of things have changed, which i actually don't like. 
Is there a way to repair my ubuntu? I mean to properly remove all kubuntu parts and fully working with ubuntu again?

---

### Post by hibliss on 2009-08-14
Not easily. You can just always go in to a Gnome session, but removing the kubuntu package does not remove all of the dependencies and programs that come with it.

What exactly do you not like?

---

### Post by Copernicus1234 on 2009-08-14
Yes I wouldnt do this without taking a backup. And I would run the live CD first just to make sure I really want KDE... 

I tried KDE 4.3 today from the CD and while it looks great, I still felt I wanted to get back to my clean, crisp, no-clutter gnome environment. So I did. KDE is not for me, but I bet it will be nice for a lot of people.

---

### Post by Cheesemill on 2009-08-14
Instructions can be found here:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by il pepe on 2009-08-14
Okay that worked great! thx a lot.
The only problem i now have is something very stupid: i seem to have lost my network connectivity icon in my panels and i don't know how to set it back :s

---

### Post by hibliss on 2009-08-14
sudo apt-get install nm-applet

---

### Post by il pepe on 2009-08-14
terminal: E:/ couldn't find packet nm-applet
or something like that (working in dutch)

---

### Post by hibliss on 2009-08-14
I guess you could install the entire gnome network manager package.

```
sudo apt get install network-manager-gnome
```

nm-applet is included in that.

---

### Post by il pepe on 2009-08-14
installed still no nothing.
Stupid icon, but usefull for a quick lookup....

---

