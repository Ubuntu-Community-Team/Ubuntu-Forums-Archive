---
title: "Can someone please help me, Graphics Problem"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by verachion on 2010-02-04
First off I am a _complete_ beginner, I apologise   

I have just installed Ubuntu and have downloaded all updates, I have tried to enable visual effects but it says its not possible? which is a  bit strange because I am on a brand new laptop. If I go in to Hardware drivers there is nothing there. Please can you help me

---

### Post by s.fox on 2010-02-04
Hello and welcome to the forum :D

Can you please open up a terminal 

**Applications -> Accessories -> Terminal **

And then run the following command:

```
lspci | grep VGA
```

Please post the output back 

-Silver Fox

---

### Post by audiomick on 2010-02-04
Open a terminal
applications> accessories> terminal
and type
```
lspci
```
there and enter.
If you can't make out your video card in there, copy (select the text, shift+ctrl+c) and paste it here (use the # button at the top of the post window to put code tags around it)
so we can see what video card you are using.

---

### Post by inobe on 2010-02-04
hi open terminal and run a few commands that you can copy and paste on your next post.


```
glxinfo
```

```
lspci
```

---

### Post by ibuclaw on 2010-02-04
There is a nice script call "compiz-check", which tests whether or not your system is compiz-ready, and if not - should tell you why it isn't.

It may also prove useful if you run that also, and paste the output of it.

You can [get it at this blog]("http://forlong.blogage.de/entries/pages/Compiz-Check").

Regards
Iain

---

### Post by inobe on 2010-02-04
i'm wondering if it will be the chromium driver, if yes' than it's possible to have desktop affects !

i had this with an intel gpu, i just kept trying to enable the affects, after two tries it worked.

---

### Post by s.fox on 2010-02-04
Oh,  forgot to ask.

What make and model of laptop are you using ? :D

---

### Post by verachion on 2010-02-04
My goodness me, thankyou so much for your quick replies, 

I have downloaded loads of apps whilst I have been like child with a new toy, I have managed to get it working by using the terminal bar to find out what graphics I am using and then I downloaded the ATI 3d driver which seemed to do the trick. 

There are so many things I want to know, but I am going to take it one step at a time, and if possible try to find it out before asking here as I know you have many people asking you the same questions all the time, I am a techy BUT a complete ubuntu novice. 

I have one question 

[B]Can anyone point me in the right direction now I have got the visual effects working

Edit: sorry I do have another problem, I seem to have to prod my mouse pad quite hard in order to double click, I have tried changing the sensitivity on the standard mouse app but nothing seems to change, is there anyway around this?
[/B]

---

### Post by audiomick on 2010-02-04
> **verachion said:**
> 
 but I am going to take it one step at a time, and if possible try to find it out before asking here as I know you have many people asking you the same questions all the time.
Good on you. Good luck with it. 
> I have one question 

**Can anyone point me in the right direction now I have got the visual effects working**
can you be a bit more specific about what you want to achieve or find out?
> **Edit: sorry I do have another problem, I seem to have to prod my mouse pad quite hard in order to double click, I have tried changing the sensitivity on the standard mouse app but nothing seems to change, is there anyway around this?**
sorry, no idea...:(

---

### Post by inobe on 2010-02-04
many of us like single click, you can achieve this by opening your home directory "nautilus" and hitting edit> preferences> behavior..

i really don't know why your having that mouse issue.


here's the documentation site, choose your version of ubuntu and browse for what you need.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by verachion on 2010-02-04
> **inobe said:**
> many of us like single click, you can achieve this by opening your home directory "nautilus" and hitting edit> preferences> behavior..
[/]("https://help.ubuntu.com/")

Single click sounds great, one problem though, what is home directory? what is nautilus? 

I know I sound a complete noob however, I am learning,  [B]I have just set up compiz with the old 3d barrel effect , woohoo! 
[/B]

---

### Post by verachion on 2010-02-04
> **audiomick said:**
> Good on you. Good luck with it. 

can you be a bit more specific about what you want to achieve or find out?
sorry, no idea...:(

Sorry, I should have been more specific, I have just seen on youtube a screen with a gadget bar or something at the top of his screen like windows where you can snap on your shortcuts, also I have just seen a fantastic way of closing a screen it sort of explodes, I know they must be apps but where on earth do I find all these things, its a little overwhelming really, I have been using ubuntu for just over an hour and half.

---

### Post by inobe on 2010-02-04
for compiz affects search in synaptic **compizconfig-settings-manager**

once installed' it should be located in preferences.

nautilus is a file manager where pictures, documents and music can be browsed.

you can click places to open it.

---

### Post by audiomick on 2010-02-04
> **verachion said:**
> ... its a little overwhelming really, I have been using ubuntu for just over an hour and half.
Don't try and rush ahead too fast. At the moment, if you manage to do anything that disrupts your system, you will have no idea what you have done or how to put it back the way it was.

By all means go ahead and try things out, it is the only way to learn, but don't forget to stop and take a breath now and then.;)

---

### Post by verachion on 2010-02-04
> **inobe said:**
> for compiz affects search in synaptic **compizconfig-settings-manager**

once installed' it should be located in preferences.

nautilus is a file manager where pictures, documents and music can be browsed.

you can click places to open it.

OK so far I have installed medibuntu which gave me skpe and google earth and codecs 

I have checked with the synaptic package manager and it shows nautilus as installed, but I can;t find it anywhere? its not in places? perhaps I have done something wrong.

---

### Post by verachion on 2010-02-04
> **audiomick said:**
> Don't try and rush ahead too fast. At the moment, if you manage to do anything that disrupts your system, you will have no idea what you have done or how to put it back the way it was.

By all means go ahead and try things out, it is the only way to learn, but don't forget to stop and take a breath now and then.;)

I won't go rushing ahead, it took me a good few years to know windows inside and out and still I am learning new things. Anything I do I will google first of all. All these terminal strings bring me back to the olden dos days. 

Do you know how I can play avis on this O/S per chance?

Edit: All done, I installed VLC after watching a tutorial

---

### Post by inobe on 2010-02-04
> **verachion said:**
> OK so far I have installed medibuntu which gave me skpe and google earth and codecs 

I have checked with the synaptic package manager and it shows nautilus as installed, but I can;t find it anywhere? its not in places? perhaps I have done something wrong.

[http://www.youtube.com/watch?v=Mg1fwIaxDOA](http://www.youtube.com/watch?v=Mg1fwIaxDOA)

---

### Post by verachion on 2010-02-04
> **inobe said:**
> many of us like single click, you can achieve this by opening your home directory "nautilus" and hitting edit> preferences> behavior..

Hhahahahaha I have been trying to find nautilus and then I went to about on the home directory and found that to be nautilus. Well thanks for making me work for it ;) now if only I can find some decent codecs ;)

---

### Post by verachion on 2010-02-04
> **inobe said:**
> [http://www.youtube.com/watch?v=Mg1fwIaxDOA](http://www.youtube.com/watch?v=Mg1fwIaxDOA)

You have got to be joking, what is with you guys hahahahahaha thanks for that I should have watched that first. :D

---

