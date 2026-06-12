---
title: "splash screen problem"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by joshuapbell on 2010-01-22
when I boot instead of getting the black and white splash screen with the ubuntu logo, i get a gray box that says "input not supported" and then eventually it gets to the login screen, my theory is that the resolution is out of range for the splash screen, how would i go about fixing this??

anyone??

Thanks a billion times

---

### Post by JiuJitsu500 on 2010-01-22
Try [this]("http://www.dwasifar.com/?p=846") maybe?

This is for editing the gdm (gnome display manager) which is in charge of boot splash and the, as he describes comically, the "white-on-poo" logo screen :)

Hope this helps, if not try googling change boot splash or something, maybe it just didn't install that part right, happens sometimes...

---

### Post by 416inversed on 2010-01-22
Start-up Manager, under System, Administration, has Splash resolution options.

---

### Post by JiuJitsu500 on 2010-01-22
You have to install Start-up-manager though :)

And it's pretty sweet, when I installed Xfce and KDE things got screwy and had all three things going at once (Xfce Usplash, gnome other parts, KDE sounds)... but on the Usplash part, even in Karmic, you can change it to Ubuntu Usplash... or if you prefer and have KDE's or Xfce's, Kubuntu or Xubuntu :)

---

### Post by 416inversed on 2010-01-22
> **JiuJitsu500 said:**
> Try [this]("http://www.dwasifar.com/?p=846") maybe.

I actually just tried that, as it only commented out the old Splash making it easily reversible, and wow, that is a much sharper boot & shut down experience.

Thanks.

> **JiuJitsu500 said:**
> You have to install Start-up-manager though :) 

Oh yeah... oops. I'm still exceedingly new to Linux and forgot that I had installed Start-up Manager separately in my excitement that I thought I knew an answer.:)

---

### Post by JiuJitsu500 on 2010-01-22
Oh.... but I must also add that when you do edit the xsplash if you choose to do so, the background image will change to the "poo" screen, and the splash screens will be whatever you set them as....

but to change the background image of the login screen you have to essentially "hack" as some call it the gdm (since it's open source i just say "change"... not hack lol)

---

### Post by joshuapbell on 2010-01-22
> **JiuJitsu500 said:**
> Try [this]("http://www.dwasifar.com/?p=846") maybe?

This is for editing the gdm (gnome display manager) which is in charge of boot splash and the, as he describes comically, the "white-on-poo" logo screen :)

Hope this helps, if not try googling change boot splash or something, maybe it just didn't install that part right, happens sometimes...

This worked after i figured out that you had to install the start up manager, thanks everyone for the help and suggestions

---

