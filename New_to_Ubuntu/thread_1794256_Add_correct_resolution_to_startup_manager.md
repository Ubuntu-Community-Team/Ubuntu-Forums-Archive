---
title: "Add correct resolution to startup manager"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-06-30
I have the startup manager installed to set the resolution for the splash screen but ive just bought a new monitor today and there is no option in startup manager that matches my monitor now, the resolution of the new one is 1092 x 1080, once loaded to the desktop the resolution is fine, i use the nvidia xserver settings manager and that detected the correct ratio no problem

Can anyone help me change this setting?

Thanks 
Mark

---

### Post by jtarin on 2011-06-30
Are you talking about the login screen background?

---

### Post by CaptainMark on 2011-07-01
no, as soon as xserver/gdm loads the resolution is okay, im talking about the bootsplash ubuntu logo, its all distorted and stretched wide

---

### Post by jtarin on 2011-07-01
What graphics card are you using? Have you done any tweaking to Grub or to Plymouth?

---

### Post by CaptainMark on 2011-07-01
its a nvidia geforce 9400gt, the only thing ive done like that on this system is installed startup manager a whiile back when 11.04 came out theres a known bug with many nvidia cards where you dont get splash top but text display on bootup (i think this bug relates to resolution and so is probably the same issue im having now), i installed startup manager to get rid of that but the resolution for my old monitor 1024x1080 was on the list so that was okay.

---

### Post by jtarin on 2011-07-01
I don't think startup manager initiates until after you login so that wouldn't really affect the Plymouth Splash screen. Does 11.04 still use the Plymouth Splash like 10.04,10.10?

---

### Post by jtarin on 2011-07-01
[Found ya a fix.]("http://ubuntu4beginners.blogspot.com/2011/05/simplest-method-to-fix-ugly-plymouth.html") 
Would have posted sooner but that site has some great tips on the Plymouth screen.....installed a beautiful one...Grub2 screen with correct resolution....changed the GDM theme all very easy.:p
I should thank you. I would've been looking for a long time for that place.:p

---

### Post by CaptainMark on 2011-07-01
well its completely got rid of the boot splash, which apparently means my display cant handle the resolution ive specified, i know it can because its full hd1080p, i will try the next resolution down but keep the same aspect, thats at least a start for now, i expect it wont be a problem once 11.10 comes out

edit: plus startup manager does affect bootsplash, its what its intended for, its the gui to alter grub setting, similar to something else i may try, plymouth-manager

---

### Post by jtarin on 2011-07-01
> **CaptainMark said:**
> 
edit: plus startup manager does affect bootsplash, its what its intended for, its the gui to alter grub setting, similar to something else i may try, plymouth-managerI had "Startup Applications" on the brain.

---

### Post by CaptainMark on 2011-07-01
nope that script completely blanks my splashscreen and nothing seems to bring it back, still better than it coming up all distorted and with boot text, itll do for now i guess

---

### Post by jtarin on 2011-07-01
> **CaptainMark said:**
> nope that script completely blanks my splashscreen and nothing seems to bring it back, still better than it coming up all distorted and with boot text, itll do for now i guessThe Plymouth Manager might give you some relief.

---

### Post by CaptainMark on 2011-07-01
yeah it works but adds looooooads of time to the boot up, got rid of it straight away

---

