---
title: "WIne... can't figure it out"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by GGGUUUYYY on 2009-01-13
I have wine installed but i can't figure how to configure it.

I've searched and come up with but i'm struggling with the code parts. 

any help will be appreciated!

Thanks

---

### Post by iaculallad on 2009-01-13
As always, [Wiki.Wiki.Wiki]("https://wiki.ubuntu.com/Wine").

---

### Post by logos34 on 2009-01-13
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by GGGUUUYYY on 2009-01-13
I've already read those help links, but sometimes you need to read them twice.

I just came to the conclusion that you can't run the application that are on my xp partition.. so i don't even no why i'm doing this.. lol

sorry about the thread..

---

### Post by dragonwolf on 2009-01-14
perhaps you could be a bit more specific as in what exactly you are wanting to run etc then maybe we could offer more support but as it it simply configuring wine in it's most basic form prior to any install of any windopws app is easy-

winecfg in terminal
set your audio driver, devices, etc then close it out( and all these are set not only to preference but what actually works on your pc)

---

### Post by dragonwolf on 2009-01-14
> **GGGUUUYYY said:**
> I've already read those help links, but sometimes you need to read them twice.

I just came to the conclusion that you can't run the application that are on my xp partition.. so i don't even no why i'm doing this.. lol

sorry about the thread..


This depends on the app and no they will nto run the apps installed on your Xp install it will require a fresh install of the app in the .wine folder however many apps will not run in wine and many will it's hit and miss one option to run more apps than wine itself is crossover by codeweavers

---

### Post by GGGUUUYYY on 2009-01-14
Ok i want to run full tilt poker. 

i downloaded wine.. but this is what i get when installing it?

going through add/remove programs

Edit.. how do i authenticate it?

---

### Post by donkyhotay on 2009-01-14
Have you edited your repositories at all? Wine is available directly from the default ubuntu repositories but you can also add the wine repositories for more up to date versions (this is what I do). The authentication error just means synaptic couldn't confirm the package. It's *probably* just fine but when in doubt don't install. Sometimes synaptic doesn't get all the information it needs when you hit 'reload' in synaptic and just hitting reload again will make it work when you try to download the package again.

---

### Post by GGGUUUYYY on 2009-01-14
Yes, i got the wine repositories right from the website.

I reloaded and got this error in synaptic package manager. so i assume i must of changed something.

---

### Post by The Cog on 2009-01-14
Here are the instructions from the wine site. 
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
The bit you need is the second section: **Trusting the WineHQ APT Repository**. I did this last week - it seemed to work fine. No warning messages when I try to install.

Actually, for months I just ignored the warnings and installed anyway because I couldn't be bothered to go back and install the authenticaton key.

---

### Post by GGGUUUYYY on 2009-01-14
> **The Cog said:**
> Here are the instructions from the wine site. 
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
The bit you need is the second section: **Trusting the WineHQ APT Repository**. I did this last week - it seemed to work fine. No warning messages when I try to install.

Actually, for months I just ignored the warnings and installed anyway because I couldn't be bothered to go back and install the authenticaton key.

How do i add that key.. i had that problem it says to download it, but i couldn't? 

do i copy the text and save it?

---

### Post by GGGUUUYYY on 2009-01-14
ttt

---

### Post by The Cog on 2009-01-15
Just right-click on the red link and choose **Save Link As...** which saves a .gpg file.

---

