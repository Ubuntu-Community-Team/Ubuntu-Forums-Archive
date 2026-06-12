---
title: "two things beans and compiz"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by TeamJ on 2009-07-12
these are both quickies so I have combined them

1. can anyone explain the beans system? what does the graphic, phrase and number of beans mean?

2. can anyone give me a step by step instruction on how to get compiz/compiz fusion/beryl/emerald on netbook remix. I maen for real beginners.
:confused:](*,):-k:???::oops::o:mad:

---

### Post by northern lights on 2009-07-12
> **TeamJ said:**
> 2. can anyone give me a step by step instruction on how to get compiz/compiz fusion/beryl/emerald on netbook remix. I maen for real beginners.
The *beryl* project is not being continued. It has been forked from *compiz* - the two are now re-merged as *compiz-fusion*. So that's what you want to install. Run```
sudo apt-get install compiz compizconfig-settings-manager
```


> **TeamJ said:**
> 1. can anyone explain the beans system? what does the graphic, phrase and number of beans mean?
Nothing.
Number of beans is post-count.
Recurring question - search the forums you'll find countless threads.

---

### Post by TeamJ on 2009-07-12
thanksare you sure this works in UNR?

---

### Post by northern lights on 2009-07-12
> **TeamJ said:**
> thanksare you sure this works in UNR?
Be advised that I do not own a netbook and do not use UNR at home - hence I cannot say that it will with absolute certainty.

That being said, it should though. And one thing's for sure - if it doesn't, it simply won't be installed. No harm for the system there, so you can savely run the above.

Further, UNR uses the same repositories as any other spin-off. So the package *compiz* has to be readily available. And if the* universe* repository is enabled (check under *System > Administration > Software Sources*), so will be *compizconfig-settings-manager*.



Another question is whether your graphics device and/or its driver support 3D acceleration - check using```
glxinfo | grep rendering

```

---

### Post by TeamJ on 2009-07-12
well check my signature. I think it supports everything, but very badly. what do you think? btw. that is why I use UNR

---

### Post by northern lights on 2009-07-12
Processing power and memory are way fine. No problems there. My guess, judging by the relative capacity of the rest of the system, is that you're graphics device will be fair enough as well. That however is the only questionable piece, if any, and is not part of your signature.

Really, your hardware is by far not too old to run any modern operating system. I don't see reasons for UNR at all.

Anyhow, you can either post the output of```
sudo lshw -C display
```to learn more on your graphics device or see whether```
glxinfo | grep rendering
```returns '*direct rendering: Yes*'

---

### Post by Michael.Godawski on 2009-07-12
Moved to ABT.

---

### Post by TeamJ on 2009-07-12
humph. so I am an absolute beginner, am I?

anyway I will do those commands soon. I chose UNR as I can have a nice intuitive menu, and also, trust me, it is the best thing for Intel integrated. is there any downside to it, either?

also as a mod, perhaps you can solve my beans question?

---

### Post by northern lights on 2009-07-12
> **TeamJ said:**
> I chose UNR as I can have a nice intuitive menu,
[...]
is there any downside to it, either?

UNR is an Ubuntu spin-off. It's not only not a different distribution, but also not considered an 'Edition' either, hence the term 'Remix'. Basically it's just a regular Ubuntu plus these packages: *go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet*

> **TeamJ said:**
> also, trust me, it [UNR] is the best thing for Intel integrated.How exactly did you reach this conclusion? Assuming by "intel integrated" your referring to and on-board graphics chip and your motherboard's chipset, there is absolutely no performance gap between any other Ubuntu edition and UNR beyond regular process consumption.

> **TeamJ said:**
> humph. so I am an absolute beginner, am I?
You asked the "beans question". Duh. Don't be pissed, man.

Googling '*beans site:ubuntuforums.org*' returns [Guide to Forum features ** INCLUDES: Thanking, beans, titles, searching, and more]("http://ubuntuforums.org/showthread.php?t=1006656") as the third link,

---

### Post by TeamJ on 2009-07-12
> **northern lights said:**
> How exactly did you reach this conclusion? Assuming by "intel integrated" your referring to and on-board graphics chip and your motherboard's chipset, there is absolutely no performance gap between any other Ubuntu edition and UNR beyond regular process consumption.

> **northern lights said:**
> Basically it's just a regular Ubuntu plus these packages: *go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet*

well integrated graphics means I have no GPU and little Graphics Memory. It uses the CPU and I only have about 256mb. I reached my conclusion by installing Vista, Ubuntu, Kubuntu and UNR. Ubuntu and Kubuntu were as slow as Vista, whereas UNR was quick to react. and no program to download and install can do that. I don't know this is related to Intel GMA but around the forums there is a pattern of people with it complaining, and apparently the driver is crap. Have you got first hand experience of both of them on a computer like mine?

> **northern lights said:**
> UNR is an Ubuntu spin-off. It's not only not a different distribution, but also not considered an 'Edition' either, hence the term 'Remix'. Basically it's just a regular Ubuntu plus these packages: *go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet*

well basically they removed some stuff to make it faster and smaller too, which is good. and seeing as they realised most netbooks have Intel GMA they worked around that

---

### Post by TeamJ on 2009-07-12
But can anyone list any downsides to using UNR?

---

