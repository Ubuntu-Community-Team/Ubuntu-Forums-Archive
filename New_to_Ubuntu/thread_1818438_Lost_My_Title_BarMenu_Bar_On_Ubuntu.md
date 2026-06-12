---
title: "Lost My Title Bar/Menu Bar On Ubuntu"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by Ashley04 on 2011-08-04
[B][SIZE=2]Hello All,

I have lost my Title/Menu Bar on any window i open.
I have looked it up on here & have seen many fixes, I did fix it  with clicking on metacity instead of compiz in the compiz fusion  icon..but my problem after that is it my effects stop working when  ticking the metacity...how can i keep my menu  bar & still have my  compiz effects working? :confused:[/SIZE][/B]

---

### Post by relay_man on 2011-08-06
Hi Ashley

I'm not 100% sure I understand your problem but if you are talking about the "panel" that is present at the top a bottom of the desktop with a default install, then here is some good info about how to add/remove/restore or change the properties of the panels.


[http://www.techotopia.com/index.php/Configuring_the_Ubuntu_Desktop_Panels](http://www.techotopia.com/index.php/Configuring_the_Ubuntu_Desktop_Panels)

Let me know if this  helps.

---

### Post by laithbsoul on 2011-08-06
I've found that this is a problem with intel graphics and compiz you can bring them up each time it happens by installing the compiz fusion icon and selecting reload windows manager from the right click drop down menu on the icon

---

### Post by Ashley04 on 2011-08-10
> **relay_man said:**
> Hi Ashley

I'm not 100% sure I understand your problem but if you are talking about  the "panel" that is present at the top a bottom of the desktop with a  default install, then here is some good info about how to  add/remove/restore or change the properties of the panels.


[http://www.techotopia.com/index.php/Configuring_the_Ubuntu_Desktop_Panels](http://www.techotopia.com/index.php/Configuring_the_Ubuntu_Desktop_Panels)

Let me know if this  helps.

> **laithbsoul said:**
> I've found that this is a problem with intel graphics and compiz you can bring them up each time it happens by installing the compiz fusion icon and selecting reload windows manager from the right click drop down menu on the icon

I tried both these...& its still doing the same thing...i do not have my title bar.
& its not the title bar at the top of the main screen that im talking about,
The bar i mean is the one on the top of windows that says..File,Edit,View,History,Bookmarks,Tools,Help
that bar whatever it is called?

---

### Post by CatKiller on 2011-08-10
> **Ashley04 said:**
> The bar i mean is the one on the top of windows that says..File,Edit,View,History,Bookmarks,Tools,Help

Right-click on panel -> Add to Panel... -> Indicator Applet Appmenu.

---

### Post by Ashley04 on 2011-08-10
> **CatKiller said:**
> Right-click on panel -> Add to Panel... -> Indicator Applet Appmenu.

Thank you. But i said the wrong panel/bar..lol sorry.
The bar that is missing is the one that goes about that that has..
X to close, minamize, & the other option, that is the bar i would somehow like to get back & still be able to have my compiz settings working for the effects.

---

### Post by CatKiller on 2011-08-10
Alt-F2.

compiz-decorator --replace

---

### Post by Ashley04 on 2011-08-10
> **CatKiller said:**
> Alt-F2.

compiz-decorator --replace


Alt-F2....it didnt do anything?

& where do i find this?....compiz-decorator --replace

---

### Post by CatKiller on 2011-08-10
Alt-F2 is supposed to bring up the Run dialogue. As an alternative, for testing, you can run that command in a Terminal.

---

### Post by Ashley04 on 2011-08-10
> **CatKiller said:**
> Alt-F2 is supposed to bring up the Run dialogue. As an alternative, for testing, you can run that command in a Terminal.


Thanks.
I got into the terminal & put all that in together & it doesnt do anything it just sits there saying...starting unity..something

---

### Post by telescopic on 2011-08-15
I don't know if this help.
try type in terminal: xfce4-panel

---

### Post by Ashley04 on 2011-09-11
> **telescopic said:**
> I don't know if this help.
try type in terminal: xfce4-panel

I tried this, & it said it wasnt installed in my computer...so i installed it through the terminal & restarted my netbook..
& what do i do now? i still do not have that top bar i need.

---

