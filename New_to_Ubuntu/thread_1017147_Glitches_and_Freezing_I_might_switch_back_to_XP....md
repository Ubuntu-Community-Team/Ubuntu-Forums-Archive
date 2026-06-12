---
title: "Glitches and Freezing: I might switch back to XP..."
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Dareth on 2008-12-20
I made the switch to Ubuntu a couple weeks ago and, at first, I liked it. The visual effects were astonishing and the idea of having a completely open source was invigorating. However, I've been experiencing some major problems. My laptop is a Dell Inspiron e1705 from 2006, has a solo core processor, 512MB of RAM, and a 70GB hard drive. I'm not working with the cutting edge of technology here, but when I had XP it could run multiple applications without slowing down or freezing. I can't run more than three programs at once without Ubuntu crashing. Another problem occurs at startup: the "NetworkManager Applet" asks to access my keyring an infinite number of times. I have to deny it at least three times before my network menu pops up. Then, I have to enter the password to my wireless network. Every. Single. Time. I. Log. In. When I connect to the network, it asks to access my keychain again. I've tried to change the settings so it will automatically find and connect to the network, to no avail. I have a Broadcom wireless card and I had to install the Broadcom B43xx driver after I got Ubuntu for my internet to work. Is this the cause of the issue? I'm also looking for a Linux-based replacement of VSThost. I would like to find a similar application to avoid downloading each instrument simulator separately.

---

### Post by SunnyRabbiera on 2008-12-20
Well it might be running effects and junk that could be clogging up your memory usage and causing slowdown.
It really depends on what you run and what you do.
I know firefox can be a hog for some people especially with flash running.
For your broadcom I am not surprised, broadcom sucks

---

### Post by mapes12 on 2008-12-20
> Another problem occurs at startup: the "NetworkManager Applet" asks to access my keyring an infinite number of times. I have to deny it at least three times before my network menu pops up. Then, I have to enter the password to my wireless network. Every. Single. Time. I. Log. In. When I connect to the network, it asks to access my keychain again. I've tried to change the settings so it will automatically find and connect to the network, to no avail. I have a Broadcom wireless card and I had to install the Broadcom B43xx driver after I got Ubuntu for my internet to work. Is this the cause of the issue?Looks like Network Manager is letting you down. Others have reported the same problem but many have had success with [WICD]("http://wicd.sourceforge.net/"). Personally, I have not had reason to use it but it may work for you. Hope you stay with us.

---

### Post by Dareth on 2008-12-20
I mostly encounter problems trying to run Banshee and Firefox simultaneously. I know Broadcom sucks, but I got this laptop for free. I'm not complaining. I'll try switching to the least amount of visual effects and see if it helps.

---

### Post by Dareth on 2008-12-20
> **mapes12 said:**
> Looks like Network Manager is letting you down. Others have reported the same problem but many have had success with [WICD]("http://wicd.sourceforge.net/"). Personally, I have not had reason to use it but it may work for you. Hope you stay with us.

Thanks, I'll try that.

I want to stay with Ubuntu, but I need my computer to do things I want.

---

### Post by TrakerJon on 2008-12-21
Why are you denying the keychain at startup? Once you enter it your wireless should connect just fine. You could make a passwordless keychain but it's not advised. It's a security feature, enough said. More memory is your slowless answer there Skippy, put 2Gb SDRAM in that thing...it's a core duo, why are you holding it back? XP was slow too I'm sure. I'm on a dinasaur C610 with Compiz and Conky running...no problem and cool runnings with 1Gb SDRAM and 1.2GHz.

**[http://www.oempcworld.com/](http://www.oempcworld.com/)** should have the memory for your computer. They'll even buy your old card(s) for half the retail price making the deal better than you can find elsewhere.

---

### Post by Dareth on 2008-12-21
> **TrakerJon said:**
> Why are you denying the keychain at startup? Once you enter it your wireless should connect just fine. You could make a passwordless keychain but it's not advised. It's a security feature, enough said. More memory is your slowless answer there Skippy, put 2Gb SDRAM in that thing...it's a core duo, why are you holding it back? XP was slow too I'm sure. I'm on a dinasaur C610 with Compiz and Conky running...no problem and cool runnings with 1Gb SDRAM and 1.2GHz.

**[http://www.oempcworld.com/](http://www.oempcworld.com/)** should have the memory for your computer. They'll even buy your old card(s) for half the retail price making the deal better than you can find elsewhere.

I don't think you understand. I have a SOLO core. I would be typing for all eternity if I kept entering the password in my keyring. A new menu pops up every time I press enter or click accept. Thanks for the site, but I think I'll wait get a new computer in a couple of years.

---

### Post by Miljet on 2008-12-21
If you will type in your login password one time, It should then associate it with your keyring and automatically start your wireless network when you log in. That is, if you shut your computer down between uses. If you use hibernate, it will ask for the password on each restart.

---

### Post by IamReck on 2008-12-21
You can get a good amount of RAM for a very cheap amount right now, try New Egg, or go to the Dell Website and they will have something for your.  It would greatly improve both Ubuntu and XP and it is highly recommended as the prices are dropping since the whole DDR3 thing is starting up, (the next generation of RAM).

Could you explain exactly step by step what happens with Network Manager?  Are you trying to connect to a Secured Wireless network?

Also, turn any visual effects you have on completely off if they are slowing your computer down, just right click on your desktop, select "Change Desktop Background," go to the "Visual Effects" tabs, and select "None."

I assume you are running 8.10 Ubuntu Intrepid Ibex?

---

### Post by Dareth on 2008-12-22
> **IamReck said:**
> You can get a good amount of RAM for a very cheap amount right now, try New Egg, or go to the Dell Website and they will have something for your.  It would greatly improve both Ubuntu and XP and it is highly recommended as the prices are dropping since the whole DDR3 thing is starting up, (the next generation of RAM).

Could you explain exactly step by step what happens with Network Manager?  Are you trying to connect to a Secured Wireless network?

Also, turn any visual effects you have on completely off if they are slowing your computer down, just right click on your desktop, select "Change Desktop Background," go to the "Visual Effects" tabs, and select "None."

I assume you are running 8.10 Ubuntu Intrepid Ibex?


Yes, I am running Ibex.

1. I turn my computer on from shutdown, Ubuntu starts up, and my desktop loads.
2. The "Network Manager applet" asks for the password to my keyring.
3. If I type in my password and hit enter, a new menu pops up. If I type in my password and click the accept button, a new menu pops up. This happens every time I type in my password.
4. I deny the NetworkManager applet four times, then the menu that connects me to the wireless pops up. I have to enter the code, then hit enter or click connect.
5. Another infinite "NetworkManager Applet" menu appears. If I deny it once, the wireless card connects to the network and I can finally use my computer.

---

### Post by fistfullofroses on 2008-12-22
First, I would try Xubuntu if Ubuntu is running sluggishly. Which is to say "apt-get install xubuntu-desktop" and you ought to be fine, just make sure that you select XFCE at your login screen. With wireless, use WICD. Broadcom sucks major. If you have a few bucks, go on Ebay and try to find a cheap atheros chipset pcmcia card. It would help alot with wireless issues. If you absolutely insist on sticking by Ubuntu proper and no derivatives, try disabling all graphic effects... could save you a lot of headache.

---

### Post by Dareth on 2008-12-22
Weighing the options, I think I'll get some more memory. It will solve a lot of problems.

Anyone have a alternative to VSThost? What about Guitar Pro?

---

### Post by IamReck on 2008-12-22
When you enter the code for the wireless network is there an option to click "Remember Passcode"?

Could you take a screenshot?  I can't seem to get my desktop to do the same thing.

Also, what version of Network Manager are you running?

Right click, click About to find out.

---

### Post by MarblePanther on 2008-12-22
I'm using the same broadcom driver in my laptop and had the same problem.  Just use wicd instead as someone else already suggested and add "wicd-client" to your autostart list in kde4 or i believe the sessions list in gnome (i haven't used gnome in a while, someone confirm). It remembers your password.

As for slowness...turn off compiz--will surprise you how much resources that frees up.

...And yes, get at least a gb of ram (less than 20$ off of amazon or crucial)

You should then be running smoothly

512mb is the minimum (ie slow) for "modern" os's (xp,vista,eye-candy desktops in *nix)

---

### Post by wolfen69 on 2008-12-22
in 9 days, ubuntu 8.04.2 comes out with all updates rolled up and support for newer hardware. why not wait and give that a try? it is a long term support release.

---

### Post by newbee70 on 2008-12-22
> **Dareth said:**
> I made the switch to Ubuntu a couple weeks ago and, at first, I liked it. The visual effects were astonishing and the idea of having a completely open source was invigorating. However, I've been experiencing some major problems. My laptop is a Dell Inspiron e1705 from 2006, has a solo core processor, 512MB of RAM, and a 70GB hard drive. I'm not working with the cutting edge of technology here, but when I had XP it could run multiple applications without slowing down or freezing. I can't run more than three programs at once without Ubuntu crashing. Another problem occurs at startup: the "NetworkManager Applet" asks to access my keyring an infinite number of times. I have to deny it at least three times before my network menu pops up. Then, I have to enter the password to my wireless network. Every. Single. Time. I. Log. In. When I connect to the network, it asks to access my keychain again. I've tried to change the settings so it will automatically find and connect to the network, to no avail. I have a Broadcom wireless card and I had to install the Broadcom B43xx driver after I got Ubuntu for my internet to work. Is this the cause of the issue? I'm also looking for a Linux-based replacement of VSThost. I would like to find a similar application to avoid downloading each instrument simulator separately.

**Strange: **I run an e1705 and had nothing but exceptional performance from it. 8.04.1 installed and setup without a hitch the only exception was having to turn on the wireless card.

performance wise I ran vista on the 1705 before switching, and I see about a 2 fold increase in performance.

mayhaps your not really ready to learn a new operating system? remember how long it took you to get used to being hand held and led: it won't happen in Ubuntu, you are the Software engineer so hit the books and learn what you need to do to fix it.

---

### Post by IamReck on 2008-12-22
> **MarblePanther said:**
> I'm using the same broadcom driver in my laptop and had the same problem.  Just use wicd instead as someone else already suggested and add "wicd-client" to your autostart list in kde4 or i believe the sessions list in gnome (i haven't used gnome in a while, someone confirm). It remembers your password.

If you are going to use WICD, just make sure you uninstall Network Manager, you can not have both installed at the same time.

---

### Post by MarblePanther on 2008-12-22
Installing wicd from the added repo in synaptic automatically removes NetworkManager.

---

### Post by Dareth on 2008-12-23
I try to install wicd, but it refuses to give it up. It won't let me uninstall the Network Manager. How exactly should I go about this so as not to ruin my pc in the process?

Disabling the effects has helped immensely, but I'm still going to purchase new memory.

I was never led by the hand in XP; I made it my bitch. Granted, Ubuntu is a drastic change, but I'm ready to get into the OS. Learning to code or understand most linux-based processes would help, but I have trouble teaching myself things without at least a little guidance.

I'll try to get a screenshot.

---

