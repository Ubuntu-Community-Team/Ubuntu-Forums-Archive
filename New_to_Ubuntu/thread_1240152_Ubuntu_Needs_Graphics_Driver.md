---
title: "Ubuntu Needs Graphics Driver?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Chester Merve on 2009-08-14
I have a HP Compaq 6730s laptop. I'm already using Vista Home Basic but I'm sick of this system and want to use Linux now. I'm a little bit used to Linux because I used Knoppix and OpenSuSE before. But they didn't work for me. A friend of me told that I should've used Ubuntu, so I installed it on a virtual machine and ready to host it on my host machine, too. Now I have a few questions. First of all, will Ubuntu need any drivers? I'm asking that because that friend of me said that it wouldn't. I know that most of drivers support Linux but some of them are hard to find, even for Windows. Like my Ati Mobility Radeon HD 3430. There's no driver for Linux even which written as a open source driver. I wonder if I can handle this or not. I need your help. Thanks for now.

---

### Post by philinux on 2009-08-14
Burn the live cd and try it out. The default vesa driver is maybe all you need.

And no you dont need drivers.

---

### Post by Sidewinder1 on 2009-08-14
First, **Welcome** to Ubuntu Forums!!
The best way to test your system with Ubuntu is to run it from a live CD. There are many tutorials and "how-to"s around, If you then run into any driver issues (I don't think that you will) the folks here ( all volunteers) will be more than willing to try to assist.
HTH,
Side

---

### Post by Chester Merve on 2009-08-14
I was wondering that because I'm using the latest version of Ubuntu and I thought that maybe Ubuntu wasn't completely ready for all of drivers. OK, I know that's stupid. :)

@Sidewinder1, thanks a lot. I'll give it a try.

---

### Post by halitech on 2009-08-14
9.04 doesn't work with "older" cards but if you need more then the vesa drivers, the ATI catalyst drivers (9.7) should work with your version of Ubuntu under the Ati Radeon HD3xxx series. Best thing to check would be to check under System - Admin - Hardware drivers to see if anything is there before going to the ATI drivers.

---

### Post by Chester Merve on 2009-08-14
If I need to install a driver and there's no solution for this, can I use Wine or Cadega?

P.S.: I'm not good at Wine. Today I wanted to run Windows Live Messenger with Wine but it didn't work.

---

### Post by halitech on 2009-08-14
> **Chester Merve said:**
> If I need to install a driver and there's no solution for this, can I use Wine or Cadega?

P.S.: I'm not good at Wine. Today I wanted to run Windows Live Messenger with Wine but it didn't work.

no, wine and Cedega only allow you to run programs, it does not "talk" to the hardware so installing drivers using either will not work.

as far as WINE and msn, instead of using MS MSN, use Pidgin (installed under Applications - Network)

---

### Post by Chester Merve on 2009-08-14
> **halitech said:**
> no, wine and Cedega only allow you to run programs, it does not "talk" to the hardware so installing drivers using either will not work.

as far as WINE and msn, instead of using MS MSN, use Pidgin (installed under Applications - Network)

I gave it a try but habits won't fade away that easily :) till I'll get used to Linux by my whole world after using Windows for 10 years.

I have a new question, too. Will Wine run Windows Live Messenger's patch software, too?

---

### Post by halitech on 2009-08-14
if you want something that looks alot more like MS msn, look at aMSN or Emesene which are alot like MS msn.

Possible but the newest versions only run on XP so chances are that they won't run.

---

### Post by Sidewinder1 on 2009-08-14
I know where you're commin' from; I started with Winbloze NT, 3.5 and threw in the towel with XP Pro, which I liked but wanted no parts of Vista. That's when I moved to Ubuntu. There is a learning curve and Ubuntu does take a little getting used to.
First I would suggest, at least initially, staying away from wine (Sidewinder ducks as Wine aficionados throw rotten tomatoes at him) :-)  as I have has little success with it, nothing wrong with it, it's probably just me. You'll find that most, if not all win. programs, have linux equivalents, usually several. Go to: System---->Administration---->Synaptic Package Manager. Here you'll find many, many, (about 24,000) software programs available for install. That's one of the main ways in Ubuntu.
You have embarked on an exploration which I think you'll find rewarding and fascination.

---

### Post by Chester Merve on 2009-08-14
> **Sidewinder1 said:**
> I know where you're commin' from; I started with Winbloze NT, 3.5 and threw in the towel with XP Pro, which I liked but wanted no parts of Vista. That's when I moved to Ubuntu. There is a learning curve and Ubuntu does take a little getting used to.
First I would suggest, at least initially, staying away from wine (Sidewinder ducks as Wine aficionados throw rotten tomatoes at him) :-)  as I have has little success with it, nothing wrong with it, it's probably just me. You'll find that most, if not all win. programs, have linux equivalents, usually several. Go to: System---->Administration---->Synaptic Package Manager. Here you'll find many, many, (about 24,000) software programs available for install. That's one of the main ways in Ubuntu.
You have embarked on an exploration which I think you'll find rewarding and fascination.

I guess you're right. :) Anyway, I'll figure it out and become a monster of Ubuntu! :P And it seems that I'll come here a lot along the way out. I really wanna get rid of this Vista, maybe Se7en would be nice but I really need to be some part of open source world. I'm wasting my time and myself using Winblowz.

---

