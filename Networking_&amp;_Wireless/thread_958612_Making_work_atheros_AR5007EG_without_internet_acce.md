---
title: "Making work atheros AR5007EG without internet access"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by LuisAugusto on 2008-10-25
Kubuntu Intrepid Ibex beta is pretty much getting me tired, it isn't because it didn't configure my wirless card, or because my wired network is blacklisted, nope, the reason, is that I can't understand why in the world it doesn't come with build-essentials out of the box **(!)**

Why is that? This is my case scenario:

- I don't have wired internet access.
- My atheros card is not working
- The solution is quite simple actually, I just need to use madwifi.
- The stupid, I can't install madwifi, because I don't have build-essentials.
- I tried to directly download them from ubuntu package search, prepared for a dependency hell experience.
- The problem: gcc-4.3-base could kill my system, yet, it's asked as a dependency, I guess this is because I'm trying to install an updated build-essential.

Could you help me XD? I'm out of ideas.

I just saw that Ubuntu Intrepid Ibex RC was released, that probably explained my depedency hell, but who knows? I'm going to try with the RC, any help is still appreciate.

---

### Post by wykedengel on 2008-10-28
I find myself under the same situation. I my atheros wireless isn't set up and I don't have access to wired Internet. Anyone with ideas of how to get wireless working without net access?

---

### Post by LuisAugusto on 2008-10-28
I already did, I just download build-essential from my windows installation, then try to install it from the command line, it will tell you what dependencies are missing, you can download them from the Ubuntu repositories search, then install them (repeat process to know what dependencies are missing for your just downloaded dependencies, yes, it sucks), and install madwifi like always :)

---

### Post by malleus74 on 2008-10-28
I installed the wifi exactly the same way... this took quite a while to figure out through the forums, then I had to download the dependencies... I'm just glad I dual-booted or I'd have been in a real mess. 

A list of needed dependencies that aren't installed in the live cd would be a great bit of info! Anyone have it? Does anyone know what you need to do differently in Intrepid?

---

### Post by LuisAugusto on 2008-10-28
> **malleus74 said:**
> I installed the wifi exactly the same way... this took quite a while to figure out through the forums, then I had to download the dependencies... I'm just glad I dual-booted or I'd have been in a real mess. 

A list of needed dependencies that aren't installed in the live cd would be a great bit of info! Anyone have it? Does anyone know what you need to do differently in Intrepid?

I have a folder with all the debs, if you want to, I can make a tar.gz, and then I could send it to you :)

However, Ubuntu should come with build-essentials, I mean, puppy linux comes with it!

---

### Post by malleus74 on 2008-10-29
I appreciate the thought, but if you could just list the debs in a post you'd make my day! 

That way, anyone else that has this problem, too, can know what to pick up, without having to try and install, fail for dependencies, repeat... :)

---

### Post by LuisAugusto on 2008-10-29
Ok, good idea:

[LIST]
[*]build-essential
[*]dpkg-dev
[*]g++
[*]g++-4.3
[*]libstdc++6-4.3-dev
[/LIST]

---

### Post by malleus74 on 2008-10-29
I think my problem was that I downloaded the dependencies you listed, and **their **dependencies weren't installed, either! :) Did you have a similar experience?

---

### Post by LuisAugusto on 2008-10-29
> **malleus74 said:**
> I think my problem was that I downloaded the dependencies you listed, and **their **dependencies weren't installed, either! :) Did you have a similar experience?

Yep, but I'm a little afraid of giving you the rest of them XD, since they killed once of my ubuntu installation, so proceed with care, I would recommend you to wait until tomorrow, after the final version is released, otherwise, you may have depedencie problems:

[LIST]
[*]patch_2.5.9-5
[*]syslinux_3.63+dfsg-2ubuntu3
[*]mtools_3.9.11-1_i386
[*]gcc-4.3-base_4.3.2-1ubuntu11
[/LIST]

---

### Post by malleus74 on 2008-10-29
I think, Luis, we can get this all lined out so a new person with a little bit of technical skill, can download the dependencies from another computer, and then install them at one time offline to Ubuntu, reboot, and be online.

You just took care of 80% of it right here. :)

---

