---
title: "Graphics issue (Possibly driver issue)"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by MrSnuggles on 2010-02-28
K, so over the past month I've been running Ubuntu 9.10, and videos have all been running weird, I didn't think too much of it, I assumed it was just the internet (As running like a DVD will run perfectly, but going on youtube or something like it will cause a horribly slowed picture with the sound on time) but now that I'm trying to run a few games (iRO on Wine, and some of the games in Ubuntu Software Center) and they all run with a horrible delay. I'm assuming it has something to do with my ATI card (Radeon x1300 Pro) so I tried installing ATI's Linux driver, as I don't think I actually have any drivers installed at the moment. I downloaded the package, ran it in terminal and got "Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-19-generic; make sure that the version is being
correctly set by --iscurrentdistro
"

How would I go about fixing this?

---

### Post by MrSnuggles on 2010-02-28
... What?

---

### Post by Paddy Landau on 2010-02-28
> **Laurar468 said:**
> Thank you so much for the post. It's really informative!
I trust that you accidentally responded to the wrong post?

---

### Post by MrSnuggles on 2010-02-28
> **Paddy Landau said:**
> I trust that you accidentally responded to the wrong post?

I'm fairly sure it's a bot/spammer, considering it's the first post made by her/him, and the signature is basically "Hey, watch movies that aren't out yet" kinda website.

---

### Post by Mark Phelps on 2010-02-28
> **MrSnuggles said:**
> I'm assuming it has something to do with my ATI card (Radeon x1300 Pro)
If you're getting a graphical desktop at present -- there is nothing to "fix".  There are no ATI drivers that will work with your card and Ubuntu 9.x.

If you force the installation of these drivers, you will corrupt your display and only have to then remove them.

The open source drivers are installed by default and that's all that is available.

---

### Post by MrSnuggles on 2010-02-28
Is there better Linux support for a Radeon 9700? I have an old card in my other computer.

---

### Post by Talon2 on 2010-02-28
> **MrSnuggles said:**
> Is there better Linux support for a Radeon 9700? I have an old card in my other computer.

I have one system with an ATI Radeon 9600 in my home office that works great with the included open source drivers (9.10).

My system at work has a ATI Radeon x1400.  It works well with the included open source drivers (9.04).

I'd say give the 9700 a try.  I'm not familiar with the specifics of the x1300.

---

### Post by MrSnuggles on 2010-02-28
I tried in the 9700 but still getting the same thing, I'm considering getting a Nvidia card, want somewhat of a low end one, one that could at least run, say, Ragnarok Online considering I love that game, semi-decently. Any ides of which I should get?

---

### Post by Mark Phelps on 2010-03-01
> **MrSnuggles said:**
> Is there better Linux support for a Radeon 9700? I have an old card in my other computer.

Basically -- no.

ATI dropped Linux support for all but the newer HD 3x/4x/5x cards last May,  Anything else (except for some recent Mobility Radeons) are now relegated to using the open source drivers -- which, BTW, tend to work fairly well for everything except hardware accelerated 3D gaming.

---

