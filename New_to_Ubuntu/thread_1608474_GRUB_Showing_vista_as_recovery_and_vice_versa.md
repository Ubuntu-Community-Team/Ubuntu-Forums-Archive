---
title: "GRUB Showing vista as recovery and vice versa"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Omnomnom on 2010-10-29
I'm new to Ubuntu, just installed it, I went into the Windows Vista entry to see if it's ok, and it was the recovery program. I then went into the Windows Vista Recovery entry, and it was Vista. Is there any way I can edit them so it shows the right one or am I stuck on having to click Windows Vista Recovery to boot into Vista? And yes, I know, Vista sucks, but it came preloaded on my laptop and I'm saving up for COD Black ops so I can't get windows 7 or XP.

Anyway, ontopic, how can I fix this? It's just a minor inconvenience but I'd prefer it how I want it.

---

### Post by Hippytaff on 2010-10-29
you can edit the grub menu, see -  /etc/default/grub file [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)
after you do this type
```

update-grub

```

---

### Post by Omnomnom on 2010-10-29
Thanks, :)
But I didn't quite understand it, could you tell me where the Grub config file is? It says there are about 5 of them... Hahaha.. Yeah um is it just boot/grub and that or is it in etc/ or what?

EDIT

Never mind found it but I don't see anything about windows vista recovery there.

---

### Post by coffeecat on 2010-10-29
A lot of people are getting this oddity, myself included on a Vista laptop. I don't believe that you can deal with this with /etc/default/grub, but I'm happy to be corrected. What you can do is to create custom entries in /etc/grub.d/40_custom and make 40_custom executable. Then you'd have to make /etc/grub.d/30_os-prober non-executable otherwise you'd get double menu entries. The details should be in the link Hippytaff posted. After which you run 'sudo update-grub'

Out of interest, what machine is it? There was a suggestion that this was affecting Sony Vaios - which my laptop is - but I think the issue is more widespread. On my Acer laptop with Windows 7, but with a separate small Windows boot partition, it doesn't invert the entries but calls the recovery partition a Vista one. Just to keep me on my toes. :|

---

### Post by Omnomnom on 2010-10-29
Meh... I don't really like the looks of that, I might try it one day but... I don't wanna screw up my MBR or anything like that... Sorry to be a bother, but I got another question, it's about ubuntu booting, ever since I got my ATI drivers working on it, the booting ubuntu logo, the all pixelly one, has been bigger than it used to, it's not that annoying but it just startled me at first, what could be the cause? And also, Acer Aspire 5536G is my model. Thanks for the help anyways guys.

---

### Post by Hippytaff on 2010-10-29
> 
 I don't believe that you can deal with this with /etc/default/grub, but I'm happy to be corrected

Your right, wasn't thinking straight, but the details of how to amend the correct file are in the link :-)
should pay more attention :-s :-)

---

### Post by coffeecat on 2010-10-29
> **Omnomnom said:**
> Meh... I don't really like the looks of that, I might try it one day but... I don't wanna screw up my MBR or anything like that... Sorry to be a bother, but I got another question, it's about ubuntu booting, ever since I got my ATI drivers working on it, the booting ubuntu logo, the all pixelly one, has been bigger than it used to, it's not that annoying but it just startled me at first, what could be the cause? And also, Acer Aspire 5536G is my model. Thanks for the help anyways guys.

That's a known issue with the proprietary ATI and nvidia drivers. They don't play nicely with the Plymouth boot splash and, being closed source, there's nothing the devs can do with the drivers.

Out of interest, what graphics card do you have, and do you game? The reason I ask is that I have ATI cards in my Acer laptop and in the desktop I'm posting from. I use the default open-source ATI driver in both and I get 3d acceleration adequate for compiz and a nice Plymouth screen as a bomus.

---

### Post by Hippytaff on 2010-10-29
You can always revert back :-)

to edit 40_custom
```

sudo gedit /etc/grub.d/40_custom

```add the entries (see the link)
then
```

sudo chmod +x /etc/grub.d/40_custom

```to make it executable...
I would wait to see if this works before making 30_os-prober non-executable.

and you might want to read up on changing permissions (chmod) [http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

If your happy with it as it is though leave it, but its an opportunity to learn (and it's a bit fun..isn't it?)

Coffeecat- please jump in if you spot a blazing balls up in my suggestion :-)

---

### Post by alphacrucis2 on 2010-10-29
> **coffeecat said:**
> A lot of people are getting this oddity, myself included on a Vista laptop. I don't believe that you can deal with this with /etc/default/grub, but I'm happy to be corrected. What you can do is to create custom entries in /etc/grub.d/40_custom and make 40_custom executable. Then you'd have to make /etc/grub.d/30_os-prober non-executable otherwise you'd get double menu entries. The details should be in the link Hippytaff posted. After which you run 'sudo update-grub'

Out of interest, what machine is it? There was a suggestion that this was affecting Sony Vaios - which my laptop is - but I think the issue is more widespread. On my Acer laptop with Windows 7, but with a separate small Windows boot partition, it doesn't invert the entries but calls the recovery partition a Vista one. Just to keep me on my toes. :|

I also get this on a Lenovo T400 dual booting with Windows Vista. It seems that the Grub2 OS prober is confused. More of a cosmetic issue but I was a bit puzzled when I first saw it.

---

### Post by Omnomnom on 2010-10-29
> **coffeecat said:**
> That's a known issue with the proprietary ATI and nvidia drivers. They don't play nicely with the Plymouth boot splash and, being closed source, there's nothing the devs can do with the drivers.

Out of interest, what graphics card do you have, and do you game? The reason I ask is that I have ATI cards in my Acer laptop and in the desktop I'm posting from. I use the default open-source ATI driver in both and I get 3d acceleration adequate for compiz and a nice Plymouth screen as a bomus.
Yes, I play Sauerbraten and some other games, it's an ATI Radeon HD 4570 with 512 MB memory.

---

### Post by coffeecat on 2010-10-29
You should get acceleration with the open source driver and the 4000 series but possibly not enough for gaming.

There are some alleged workarounds and fixes for the ugly Plymouth splash posted around the place, but I don't know how good they are now. I was fairly unimpressed with one 'fix' I found that I tried with a nvidia card.

---

### Post by Omnomnom on 2010-10-29
Ah well. I'll just keep it at that really giant loader, least it's prettier than window's loading bar, well in my eyes anyway.

---

