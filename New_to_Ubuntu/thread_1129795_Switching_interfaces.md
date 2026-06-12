---
title: "Switching interfaces"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by chris.willis on 2009-04-19
Hi there, I've looked around the forums but still not sure about this--I really like Ubuntu but my family prefer the KDE interface. I am aware that the Ubuntu distro can be used with the KDE look with 'kde-desktop'. I'm a bit confused. ie, after installing ubuntu, how can I make it look like KDE, but without installing KDE applications? Does this make sense :/  hope so.

---

### Post by sim-value on 2009-04-19
You cant

Either you install KDE and the Core applications it depends on (Konqueror ...) or you dont

Though you avoid some dependecies  when using kde-core

/me

---

### Post by chris.willis on 2009-04-19
Sorry for the question - thought it was possible. So many people are dead against Linux. My wife doesn't like the look of Ubuntu and I may be able to convince people with KDE interface - can you skin gnome to KDE, or am I way off track with this? (Sorry, being new myself, I'm not completely aware of Ubuntu limitations, and although not a Windows fan, at least one can skin it - what is the Gnome equivalent?)

---

### Post by JoshuaRL on 2009-04-19
You can, to a small extent.  There's an Oxyglass theme on gnome-look.  But for the full KDE experience, which it seems like your family wants, you're not really going to get it.

Is there any reason why you can't have a few more applications installed?

---

### Post by chris.willis on 2009-04-19
There's no reason at all my friend - what do you have in mind?

---

### Post by lisati on 2009-04-19
I take it that installing the kubuntu-desktop would be a problem?

---

### Post by JoshuaRL on 2009-04-19
> **chris.willis said:**
> There's no reason at all my friend - what do you have in mind?

:)

Well, if you install the kubuntu-desktop metapackage, it will give them what they want.  And I've seen that exact thing make a big difference to someone regarding their opinion of Linux.  They got aggrivated by Gnome for some reason, and when I installed and showed them how to run KDE, they felt much more comfortable.  That said, you'll just have to make sure you have enough drive space.  But if that isn't an issue, whatever makes the horse drink right?

To do this, it's best to use aptitude:
```
sudo aptitude install kubuntu-desktop
```
The reason is that aptitude handles metapackages a little better than apt-get.  Metapackages are actually empty, and point to a number of other packages needed to make the whole thing work right, and in this case give you the full "Kubuntu" experience.  Aptitude is able to work backwards with them to remove everything if you ever want to delete all of that.  Apt-get will just delete the empty metapackage.

To delete:
```
sudo aptitude remove kubuntu-desktop
```

You can also try XFCE the same way:
```
sudo aptitude install xubuntu-desktop
```

Hope that helps.

---

### Post by chris.willis on 2009-04-19
Have 1TB of drive space. Shouldn't be a problem. So the above commands are what you reckon I need: to make Gnome with all its wonderful apps to look a little more eye-candyish for Windows users?

---

### Post by muted1987 on 2009-04-19
after you have used sudo aptitude install kubuntu-desktop you will need to press ctrl+alt+baskspace which will take you to the login screen and you will hav to change the session there to kde and you can als set it to default aswell.

Just a heads up in case you didnt know

---

### Post by JoshuaRL on 2009-04-19
> **muted1987 said:**
> after you have used sudo aptitude install kubuntu-desktop you will need to press ctrl+alt+baskspace which will take you to the login screen and you will hav to change the session there to kde and you can als set it to default aswell.

Just a heads up in case you didnt know

Yep, muted got it right.  That's how you change the Desktop Environment.   As the base OS is the same, X will boot up the DE of your choice that way.  If it's a different user, it keeps default logins so you'll only have to change that once for them.

---

### Post by chris.willis on 2009-04-20
Thanks very much for the replies: sounds great. I'll wait a couple of days for Jaunty and do it then.

Thanks again,
Chris

---

