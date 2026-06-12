---
title: "window color automatically changed"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by kickwin on 2009-08-12
I do know what happened but when I started my computer today, I was surprised to find that the window top bar (which has close, minimize etc.) changed colour. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124632&stc=1&d=1250110202[/IMG]

I do not know how I can change it back to the original default colour (brown). I changed the theme but it did nothing to change this. I am totally surprised and I would appreciate any help.

---

### Post by TheNosh on 2009-08-12
in the top menu: system--> preferences--> appearance

then you can select one of the default theme options, or to simply change the colours you can click the "customize" button and then go to the "colors" tab

---

### Post by kickwin on 2009-08-12
I tried that but there is no option to change the color of the active window title bar. I could change the color of other things such as window area, text box etc.

---

### Post by theozzlives on 2009-08-12
> **kickwin said:**
> I tried that but there is no option to change the color of the active window title bar. I could change the color of other things such as window area, text box etc.

I believe it's called hilighted item or object or something to that effect.

---

### Post by TheNosh on 2009-08-12
it's "selected items". i just checked.

---

### Post by kickwin on 2009-08-12
It still doesn't change it.

---

### Post by TheNosh on 2009-08-12
> **kickwin said:**
> It still doesn't change it.

i can't really tell by the picture you gave, but are you using emerald theme manager?

---

### Post by CatKiller on 2009-08-12
That looks like the default Emerald theme to me.

---

### Post by kickwin on 2009-08-12
Oh..yes...I have emerald installed. I thought it was needed for having Compiz work properly. Is this correct? 

Emerald has been on my system for a while but this change of color happened only today. 

So I reckon I have to change this option within emerald.

---

### Post by TheNosh on 2009-08-12
you actually don't need emerald for compiz to function properly, many of us just prefer it. i'm not sure how to make it not run with compiz though if you'd like that i'm sure someone here can help you. if you would just like to change the colour of your emeral theme you can do so by going to 

system --> prefferences --> emerald theme manager

and then just click edit themes to be given options for colors and such

---

### Post by CatKiller on 2009-08-13
> **kickwin said:**
> So I reckon I have to change this option within emerald.

You don't have to, although you can. There are some themes that are just like the default Metacity theme, but with Emerald flourishes. As well as some other nice ones, too, of course.

You could configure Compiz to use Metacity to decorate the windows with Metacity rather than Emerald instead, although I can't remember exactly how at the moment. I know you can do it through CompizConfig Settings Manager, but there may well be a more general way.

---

### Post by wizard10000 on 2009-08-13
> **kickwin said:**
> I do know what happened but when I started my computer today, I was surprised to find that the window top bar (which has close, minimize etc.) changed colour. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124632&stc=1&d=1250110202[/IMG]

I do not know how I can change it back to the original default colour (brown). I changed the theme but it did nothing to change this. I am totally surprised and I would appreciate any help.

Your screenshot is of the default emerald theme.  If you want metacity back all you have to do is either uninstall emerald or open a terminal window and type 

```
metacity --replace &
```

Hope this helps -

---

### Post by TheNosh on 2009-08-13
> **wizard10000 said:**
> Your screenshot is of the default emerald theme.  If you want metacity back all you have to do is either uninstall emerald or open a terminal window and type 

```
metacity --replace &
```

Hope this helps -

that stops compiz though

---

### Post by wizard10000 on 2009-08-13
> **TheNosh said:**
> that stops compiz though

It does?  Sorry, I'm at work on a Windows machine  :)

---

### Post by TheNosh on 2009-08-13
> **wizard10000 said:**
> It does?  Sorry, I'm at work on a Windows machine  :)

no need for appologies, i had to test it myself before i realized that. (which is sad on my part because it's the command i always use to stop compiz before playing games.)

---

### Post by TheNosh on 2009-08-14
AH! found it! (the name of the default window decorator) it's gtk-window-decorator (duh!)

the command you need is ```
gtk-window-decorator --replace
``` and then all should go back to normal

metacity --replace wouldn't work because metacity is a window **manager** which is what compiz is as well so they conflict. however gtk-window-decorator (which metacity uses) can be used with other window managers with no conflict as it is a window **decorator**.

---

### Post by kickwin on 2009-08-14
I uninstalled emerald and it appears to have solved the problem. Compiz works fine as well. Is there something wrong with what I did?

---

### Post by kickwin on 2009-08-14
> **kickwin said:**
> I uninstalled emerald and it appears to have solved the problem. Compiz works fine as well. Is there something wrong with what I did?

I realized the use of Emerald which is to change themes.

---

### Post by TheNosh on 2009-08-16
> **kickwin said:**
> I uninstalled emerald and it appears to have solved the problem. Compiz works fine as well. Is there something wrong with what I did?

nope, theres nothing wrong with what you did. getting rid of emerald made it default back to gtk-window-decorator.

---

