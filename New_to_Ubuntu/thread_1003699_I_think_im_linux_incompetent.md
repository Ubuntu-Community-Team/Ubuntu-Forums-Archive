---
title: "I think im linux incompetent"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Chriscopenhaver on 2008-12-06
Hello all im new to the forums and have only had Ubuntu for around a day now. I have been messing around learning a few things and its pretty awesome. However I ran into my first road block. I am attempting to download frostwire 4.17.1 and i download it by selecting open with Gdebi package installer which it says is the default one. I do as i would normally do it asked me to install and i selected to install it does its things says its installed but however the file does not open and does not feel like to installed itself right. If you guys can offer any easier ways to do this or if its quite simple just let me know. Thanks

---

### Post by Patrick793 on 2008-12-06
Well, if it said it's installed try going to Applications > Internet and Frostwire should be there.

If it's not, open a terminal (Applications > Accessories > Terminal) and type frostwire. See if it starts then.

---

### Post by Duck2006 on 2008-12-06
Did you install Java first?
Did you install ubuntu-restricted-extras?

From the terminal sudo aptitude install ubuntu-restricted-extras

---

### Post by birddog165 on 2008-12-06
Oh boy you are in for a real treat. You can go
System > Administration > Synaptic Package Manager
and open the Package Manager. This is a very easy way to download almost whatever you want. Here is a link to their site if you have more questions: [Package Manager]("https://help.ubuntu.com/8.04/add-applications/C/index.html")

So anyways. Open package manager and then type frostwire in the search. You should find it.

---

### Post by Chriscopenhaver on 2008-12-06
Yes frostwire shows up in my applications panel. I click on the link nothing happens. As for a terminal i apologize for not knowing what im doing but im not sure i know what that is. As for installing java im having a hard time figuring out where to get the file i need. I look in the add/remove app panel and i download all of those other java apps. Im confused for the most part thanks for your help guys

---

### Post by Duck2006 on 2008-12-06
From the terminal

sudo aptitude install ubuntu-restricted-extras

It will install Java with some other packs.

---

### Post by s.fox on 2008-12-06
The terminal can be found at:

Applications menu -> Accessories -> Terminal.

---

### Post by Chriscopenhaver on 2008-12-06
Ok well i found the terminal and this is where it gets hard for me. I really do not know what to do next

---

### Post by Chriscopenhaver on 2008-12-06
Ok im dumb thanks for your help man i never thought to put it in there lol. Thanks again guys

---

### Post by s.fox on 2008-12-06
type this in

```
sudo aptitude install ubuntu-restricted-extras
```

EDIT:  don't forget to press enter :)

---

### Post by txwooley on 2008-12-06
With the terminal open, press F1.  This will bring up the terminal help.  It will help you understand it a lot better.

---

