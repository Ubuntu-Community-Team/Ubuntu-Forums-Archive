---
title: "anything = to Visual Basic"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Zundap on 2010-01-09
Just a question here, does ubuntu have a program that is the same as, Visual Basic for Windows, thanks for any replies.

---

### Post by aaronp on 2010-01-09
Nothing as intuitive but you can try wxGlade. [http://wxglade.sourceforge.net/](http://wxglade.sourceforge.net/)

There are a couple of programs (BoaConsructor and PythonCard) that will allow you to create GUIs using a 'visual' approach but in my opinion the learning curve is quite steep.
On the plus side, once you conquer them you actually feel like you can read all the code they produce and I found I ended up writing my GUIs in a text editor instead.

---

### Post by Ubu2010 on 2010-01-09
Sorry, I don't want to seem like I am hijacking the thread, I just figured I would ask that since BC was mentioned. Regarding BoaConstructor, how necessary is it to download and install the wxPython extensions to use it ? I haven't quite figured out how to add those extensions. 

Anyway, back on topic, I have to say that since I have a background in Visual Basic using Studio Express, that BoaConstructor seems to look like something I am going to like, once I learn how to use it. It seems to be user-friendly, so I am hoping that it is.

---

### Post by kostkon on 2010-01-09
Then, you need to check [*Gambas*]("http://gambas.sourceforge.net/").
> Gambas is a free development environment based on a Basic interpreter with object extensions, a bit like Visual Basic™ (but it is NOT a clone !). Read the introduction for more information.

---

### Post by k64 on 2010-01-09
You can try the open source edition of Qt; it might come in handy.

To install it:

```
sudo apt-get install qt4-designer
```

---

### Post by Ubu2010 on 2010-01-09
Interesting, I will check out those links, thanks !

---

### Post by nexes128 on 2010-01-09
You should look at monodevelop its come along way and if you know .Net your already good to go(although mono doesn't support the entire .Net framework its pretty dam close)

---

### Post by HermanAB on 2010-01-09
My favourite RAD is Glade-2 and Perl.

---

### Post by AlanPo on 2010-01-10
> **kostkon said:**
> Then, you need to check [*Gambas*]("http://gambas.sourceforge.net/").

But one thing is - for hardy and interepid on AMD64 bit version you are not able to install Gambas. Forget it unless you are an expert in compiling from source.
Repositories do not provide working version. googling also didnt provide me with info how to deal with compile problems, so do not waste time if you are not an "expert" :)

---

### Post by aaronp on 2010-01-10
> **kostkon said:**
> Then, you need to check [*Gambas*]("http://gambas.sourceforge.net/").

Thanks! I've just installed gambas and it looks great - should allow me to spend less time on GUI and more time on the 'under the hood' parts of my apps.

Note to anyone, in Karmic I was simply able to install using: 
```
sudo apt-get install gambas2
```

I didn't have to go through the install from source or even downloading the elusive deb files referred to on the gambas site.

---

### Post by Zundap on 2010-09-13
Sorry to be so late in replying, i have been unable to get back to my computer for health reasons, but thanks to everyone for all your replies.

---

### Post by directhex on 2010-09-15
The mono-vbnc package contains the "vbnc" compiler, which can compile VB.NET code. the monodevelop package contains the MonoDevelop IDE, which can make editing VB-based projects easier (but has no GUI designer for VB.NET)

---

