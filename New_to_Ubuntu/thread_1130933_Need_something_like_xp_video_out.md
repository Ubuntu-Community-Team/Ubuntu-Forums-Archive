---
title: "Need something like xp video out?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by kermorvan on 2009-04-20
I have just bought a lcd tv and want to connect it to my portable which has VGA and audio out, the TV has VGA and audio in. The handbook recommends using the external screen option of XP. 

I use Ubuntu 8.10 and would like to know if there is something I'm missing here already or is there a package I can download?

Regards
Steve


Samsung R40, 2GB Memory, 160 Gb HD, T5500 Dual core

---

### Post by DGortze380 on 2009-04-20
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by halitech on 2009-04-20
do you have the correct drivers installed for your video card?

---

### Post by kermorvan on 2009-04-20
Well, I'm a novice where Ubuntu is concerned, but I ha nvidea card and driver and it worked fine with xp before my trying Ubuntu.

Thanks for the replies so far, I'll try to work out the command line thing (VERY long time no see :-) I understood DOS as a young lad......

Steve

---

### Post by Hospadar on 2009-04-20
If you have an nvidia card, tv-out, external monitors, etc, is really easy

Just use nvidia-settings

Alt-F2, type in nvida-settings, go here (see attachment) do detect displays, set everything up, and if you want to make you settings permanent, start nvidia settings with "sudo nvidia-settings" and do "Save to X configuration file" when you've got everything the way you want.

---

### Post by kermorvan on 2009-04-20
Just for a second or two that looked really hopeful, but my nvidia x-settings doesn't look like yours - I wish it did. It just says nvidia configuration settings, and then show tooltips etc, no choice about anything really. I also get a popup stating that I don't seem to be usuing X-settings and to use the command line with x-config. Done that, no joy :(

Why do I  get all thiese niggling, stupid, petty little problems with Ubuntu? First my text cursor moves all by itself so I get text in the middle of test - not my typing, I didn'thave the problem with XP. Now this, it's almost as if you have to be some type of uber geek just to use the system for something this basic - why? Do things keep falling between the cracks or is it a Microsoft response by writing yet more bad code and passing it off as Linux Development??

Thanks anyway people

Steve - Very fed up!!

---

