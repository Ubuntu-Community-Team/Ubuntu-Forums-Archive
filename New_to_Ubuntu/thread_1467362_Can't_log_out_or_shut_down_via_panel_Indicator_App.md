---
title: "Can't log out or shut down via panel Indicator Applet"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by ricardisimo on 2010-04-30
Just that. I click on "Log Out..." and get the little confirmation dialogue that says: "Are you sure you want to close all programs and log out of the computer?" I confirm, and then wait, and nothing happens. Same with "Restart..." and also "Shut Down..."

Any ideas?

---

### Post by Sealbhach on 2010-04-30
Does it work OK if you shut down from the System menu?

.

---

### Post by ricardisimo on 2010-04-30
How does one shut down from the System menu?

---

### Post by Sealbhach on 2010-04-30
> **ricardisimo said:**
> How does one shut down from the System menu?

You just click on the System menu in the top panel, and select Shut Down.

.

---

### Post by ricardisimo on 2010-05-01
There's no "Shut Down" option in the System menu. I think that you are referring to the Indicator Applet, normally on the top panel and to the right. If so, that is precisely what is not working.

I just noticed a similar thread to mine... let's see if someone else is having the same troubles.

---

### Post by ricardisimo on 2010-05-02
This is now happening on both computers: home and work. One was an upgrade, and the other was a fresh install.

[sigh]

---

### Post by AnAnSwe on 2010-05-03
Same here. Have a Compaq nc6000 laptop with a fresh installation of ubuntu 10.04. When I choose shut down from the top panel and to the right all it does is logging out. Can't shut down in any other way than press and hold down power button :(

I have also tried "gconf-editor" and "/apps/gnome-power-manager/actions/buttons" and set "power button" to "shut down" without any luck.

But today the touch pad works so thats one down one to go.. :D

---

### Post by spiky001 on 2010-05-03
You can shutdown with terminal
```
sudo halt
```

I have seen alot of reports on this my doneit the 1st time!!
I had to do sudo update-grub for another reason but all worked after that maybe coincidence!!!!!!

---

### Post by ricardisimo on 2010-05-03
sudo update-grub sounds like something one should not be doing without cause. Does it even apply in my case?

---

### Post by spiky001 on 2010-05-03
[http://ubuntuforums.org/showthread.php?t=1469595](http://ubuntuforums.org/showthread.php?t=1469595)

have a look here

---

### Post by Lachinchon on 2010-05-03
I'll add my voice to the chorus. Shutdown (or restart, too) brought up the user selection screen. Only hard reset got me out. Shutting down using the terminal does not seem like a very user-friendly option.

---

### Post by alexanda on 2010-05-03
> **ricardisimo said:**
> There's no "Shut Down" option in the System menu. I think that you are referring to the Indicator Applet, normally on the top panel and to the right. If so, that is precisely what is not working.


On my install, shutdown only appeared on the system menu after I Right-Clicked on the shutdown Indicator Applet and removed it from the Panel.

---

### Post by ricardisimo on 2010-05-03
> **alexanda said:**
> On my install, shutdown only appeared on the system menu after I Right-Clicked on the shutdown Indicator Applet and removed it from the Panel.

But did it make any difference? Does it work in any location?

---

### Post by AnAnSwe on 2010-05-04
> **spiky001 said:**
> [http://ubuntuforums.org/showthread.php?t=1469595](http://ubuntuforums.org/showthread.php?t=1469595)

have a look here

Thanks!
I'll try this when I get home from work.
I'll get back with information if this works or not.

---

### Post by ricardisimo on 2010-05-05
Mine is fixed. I still had grub - and not grub2 - installed on my system. I followed the instructions in the [grub2 wiki]("https://wiki.ubuntu.com/Grub2") and now all is joy. Thanks for the help.

---

### Post by ricardisimo on 2010-05-11
I take it all back, and I apologize for not posting earlier. Nothing is fixed. It worked once after installing grub2, then I didn't use this computer again for about a week.

Any other ideas? I can switch users, and I think that includes starting a "guest" session. Otherwise the panel applet does nothing. Well, not nothing... as I stated earlier, it gives me a little pop-up asking for confirmation of whatever I want to do, but that's it. I still have to shut off at the power button or command line, neither of which is very appetizing.

Any help would be greatly appreciated.

---

### Post by ricardisimo on 2010-05-16
It's definitely affecting both of my computers, but differently. I cannot always switch users on one of them, which is all that I can do on the other.

On the work computer (which is the one where I can only switch users) I've noticed that it sometimes behaves for the "base" user account, the one I installed with. Even though the others are also administrators, they don't seem to ever be able to log out or shut down or restart via the panel.

Anyone else having these issues or know of the appropriate Launchpad bug?

---

### Post by ashwinhgtx on 2010-05-16
I have the same problem. I'm using this```
sudo shutdown -h now
```

Is this a bug in Lucid?

---

### Post by ricardisimo on 2010-05-17
And I've been using "sudo reboot" or "sudo shutdown -h now" as well. I have to assume this is a bug.

---

### Post by laidback on 2010-05-17
I have the same problem. But on my system I use "Switch User" then choose from the icon (applet) at the bottom right of the new window which has "Shut Down" as an option.

Modifying /etc/default/grub didn't help me unfortunately.

Log Out and Restart don't work either.

---

### Post by ricardisimo on 2010-05-18
Hmmm... I'm wondering if [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562027") is the issue. Do any of you have the OOo 3.2 Quickstarter up on your panel? Try exiting Quickstarter, then see if the panel shutdown/restart works.

I'm not at the right computer until tomorrow, so I can't check.

---

### Post by laidback on 2010-05-18
ricardisimo,

I had the Quickstarter applet as I have done on all my Ubuntu installations, up to now it's been really good. 

After I deleted it in 10.04....

I've done 2 shut downs and 1 restart and they've worked each time...fantastic,

---

### Post by ricardisimo on 2010-05-18
> **laidback said:**
> ricardisimo,

I had the Quickstarter applet as I have done on all my Ubuntu installations, up to now it's been really good. 

After I deleted it in 10.04....

I've done 2 shut downs and 1 restart and they've worked each time...fantastic,

So it worked? Fantastic... I'm off to work to try it now. The shame of it is that I do like the Quickstarter. Have you tried putting it back after the fact? Maybe something just needed to reset.   :-k    Dunno.

I'll be right back.

---

### Post by laidback on 2010-05-19
For now nothing new tried. I'm wondering whether adjustments to the memory settings in OOo would have any effect.

I have created applets/icons for OOo Word and Spreadsheet that reside on the task bar, they work just fine but are not quite as quick as Quickstarter.

---

### Post by ricardisimo on 2010-05-19
For me it seems to have worked. I right-clicked on the OOo quickstarter and selected "disable systray quickstarter" or whatever the option said, and so far all is joy. We'll see if it comes back.

---

### Post by laidback on 2010-05-19
Pleased to hear it, at least we appear to know the cause now.

---

### Post by pizza-is-good on 2010-05-19
> **ricardisimo said:**
> For me it seems to have worked. I right-clicked on the OOo quickstarter and selected "disable systray quickstarter" or whatever the option said, and so far all is joy. We'll see if it comes back.

That is what it is. I had the same issue a few days after 10.04 came out. Took me a while to figure it out.
Glad you got it working. Although I came too late, just to confirm that it does work.

Happy ubunting.

~pizza

---

### Post by ricardisimo on 2010-05-20
> **pizza-is-good said:**
> That is what it is. I had the same issue a few days after 10.04 came out. Took me a while to figure it out.
Glad you got it working. Although I came too late, just to confirm that it does work.

Happy ubunting.

~pizza

Likewise. May I ask if "pizza-is-great" was taken? Because, you know, pizza ***is*** great.

---

