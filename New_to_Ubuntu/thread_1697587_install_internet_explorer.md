---
title: "install internet explorer"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by euriboyka on 2011-03-01
i want to install internet explorer inside wine but on running a few commands the winehq homepage comes up instead of installation window.
earlier i have installed notepad++ like this but now its all different happening.

---

### Post by waynefoutz on 2011-03-01
> **euriboyka said:**
> i want to install internet explorer inside wine but on running a few commands the winehq homepage comes up instead of installation window.
earlier i have installed notepad++ like this but now its all different happening.

try installing playonlinux through the repositories and install it that way. For some reason they changed the look of it,But it's IE under the hood.

---

### Post by euriboyka on 2011-03-01
"they changed the look of it.but it's still IE under the hood "
by above line  did you mean if i can still install IE through that  WINEHQ homepage window also even without  installing playon linux !!!

---

### Post by euriboyka on 2011-03-01
ok..i have installed playonlinux. 
so how should i proceed from here onwards !!

---

### Post by waynefoutz on 2011-03-01
> **euriboyka said:**
> ok..i have installed playonlinux. 
so how should i proceed from here onwards !!

It's in the menus in playonlinux. they have versions 6 and 7

---

### Post by Smart Viking on 2011-03-01
Maybe we should take a few staps back and look at the situation.

Why do you want to install IE?

---

### Post by waynefoutz on 2011-03-01
> **euriboyka said:**
> "they changed the look of it.but it's still IE under the hood "
by above line  did you mean if i can still install IE through that  WINEHQ homepage window also even without  installing playon linux !!!

I mean WINE slightly altered the UI, maybe for copyright reasons, I'm not sure. It just sort of happened one day.

---

### Post by waynefoutz on 2011-03-01
> **Smart Viking said:**
> Maybe we should take a few staps back and look at the situation.

Why do you want to install IE?

there'd be a lot of reasons, the best one I can think of is if you are a web developer and want to see how your site renders in IE. Also some sites only render properly with IE, although that situation is getting rare these days.

I hope the original poster isn't planning on using it as a permanent browser, it's painfully slow compared to a native browser.

---

### Post by grahammechanical on 2011-03-01
I only run one Windows program inside wine but I install it by typing in a terminal winefile.

This produces a Windows Explorer type window. If I have the CD in the drive at the time I do this I can browse to the CD drive, just like in Windows itself (also just like in Ubuntu) and find the start.exe or setup.exe or install.exe file and click in it. The install shield program launches and I am away.

Have you tried this?

Regards.

P.S. We are all assuming that you have a Microsoft Internet Explorer install CD. If you were thinking that you could download Internet Explorer from the Wine website, then you are mistaken. This program is copyright material and the Wine developers would be breaking the law if they did that. So, they don't.

---

### Post by mikechant on 2011-03-01
> P.S. We are all assuming that you have a Microsoft Internet Explorer install CD. If you were thinking that you could download Internet Explorer from the Wine website, then you are mistaken. This program is copyright material and the Wine developers would be breaking the law if they did that. So, they don't.

Actually MS itself provides direct download links for standalone IE installers (no IE CDs for a long time); general opinion is that it's legal to use IE under Wine as long as you have some sort of valid Windows license.

Thing is, what version of IE do you want to run?
IE6 runs pretty well with wine and I found it very easy to install using the 'ies4linux' package. Later versions are more problematic and complicated with different people reporting different levels of sucess/failure. You might want to look into 'winetricks' which sorts out much of the detail for you, I haven't tried it.
I see that the ies4linux site, which appeared to be dormant, now says they are working on IE9 support.

---

