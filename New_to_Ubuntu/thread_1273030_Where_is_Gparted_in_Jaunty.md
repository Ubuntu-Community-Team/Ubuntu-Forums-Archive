---
title: "Where is Gparted in Jaunty?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by donsy on 2009-09-22
In the Ubuntu Help Center (The ? on top panel) the section on disks and partitions says that the Gnome Partition Editor is in System > Administration > Gnome Partition Editor, but it doesn't appear on my System > Administration menu at all. Do I have to install it separately?

---

### Post by mah817 on 2009-09-22
Yes it is absent from the default install. It is included and can be run from the live CD or you can install from the Synaptic Package Manager.

---

### Post by lisati on 2009-09-22
You can also install it from the Add/Remove menu.

---

### Post by ~sHyLoCk~ on 2009-09-22
> **lisati said:**
> You can also install it from the Add/Remove menu.

or
```
sudo apt-get install gparted
```

You might need dosfstools and ntfsprogs as well.

---

### Post by lisati on 2009-09-22
> **~sHyLoCk~ said:**
> or
```
sudo apt-get install gparted
```

You might need dosfstools and ntfsprogs as well.

Well spotted.

As usual, there is often more than one way of answering a question.

---

### Post by zeroseven0183 on 2009-09-23
> **lisati said:**
> As usual, there is often more than one way of answering a question.

Here's another one:

```
sudo aptitude install gparted
```

[Psychocats: aptitude vs. apt-get]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by mcduck on 2009-09-23
> **zeroseven0183 said:**
> Here's another one:

```
sudo aptitude install gparted
```

[Psychocats: aptitude vs. apt-get]("http://www.psychocats.net/ubuntu/aptitude")

I hope you have noticed that the article you posted is very old, and even then also mentions that it's mostly irrelevant since Ubuntu 6.10..

> 
So the points outlined on this page about using aptitude over apt-get are largely irrelevant if you're using Edgy Eft (6.10), Feisty Fawn (7.04), or any future version of Ubuntu


These days aptitude has no benefits over apt-get any more. Actually in my opinion it's worse, since it sometimes tries to be "too smart" when sorting out dependencies, and ends installing or removing wrong stuff.

I wouldn't recommend aptitude over apt-get unless somebody really needs an ncurses interface (which is the only feature Aptitude has that apt-get doesn't have).

---

