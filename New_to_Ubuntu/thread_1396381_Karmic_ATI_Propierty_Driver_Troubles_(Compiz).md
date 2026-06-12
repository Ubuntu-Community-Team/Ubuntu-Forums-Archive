---
title: "Karmic ATI Propierty Driver Troubles (Compiz)"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by den160593 on 2010-02-02
Hi,

I'm trying to set up [Docky]("https://launchpad.net/docky") on Karmic. To do so I'm (trying) to follow this guide: [http://tombuntu.com/index.php/2009/12/20/how-to-install-docky-in-ubuntu-9-10/](http://tombuntu.com/index.php/2009/12/20/how-to-install-docky-in-ubuntu-9-10/)

It says I need to have Compiz enabled. So to do so I need to install the ATI drivers. I tried doing so (through the automatically found drivers) and now I have this weird problem.

I have dual screen setup, and without the ATI driver it works perfect, I can use both screens. When I install the ATI driver however my right screen becomes my main screen and my left screen is shifted about 5 cm from the left corner (so black bar). To get to the left screen from the right screen i gotta move my mouse to the right and it appears on the left (with that bar still there where nothing happens).

Now i tried to switch this by dragging my right screen to the position of the left screen under the Display monitor. This however does nothing at all. Anybody happen to know how to fix this? Sorry about my crappy description :(

Thanks!

---

### Post by nishant.singh28 on 2010-02-02
I can't help you out much but one advice from my experience, stay off Docky. The current versions have a nasty habit of clogging up the startup on ATI machines. I had troubles on my notebook too. Try Cairo instead.

---

### Post by den160593 on 2010-02-02
Hi, thanks for the reply. I uninstalled Docky. Problem is still happening however. I can't enable effects, and if I try activate the driver it stuffs up :( Any reasons why this could be occuring

---

### Post by den160593 on 2010-02-03
Still stuffs up if I try to load teh ATI driver via System -> Administration -> Hardware Drivers. My graphics card is (in case this might be an issue with that): VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]

---

### Post by den160593 on 2010-02-05
Anybody able to help?

---

### Post by den160593 on 2010-02-06
I have tried to install the opensource drivers ([https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)) however, when I try to enable desktop effects my screen becomes blank and the only thing I can move is the mouse. Can anybody help me out?

Thanks

---

### Post by samantha_ on 2010-02-06
I had the same problem.

I simply ended up switching the stuff on the screen (ie. moving the panels from one screen to another).


However, I never got the shifted screen problem.
Are you using the catalyst control center majiggy?

---

### Post by den160593 on 2010-02-07
Hi thanks for reply :). When I downloaded the driver via System>Admin>Hardware Drivers I didn't have that option. I then installed a newer version from the ATI website ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)), that had the Catalyst Control Center. However that just flickered alot and wouldn't save when I tried to make it stop mirroring my screens.

I've heard that opensource drivers work better, and if so, I was wondering how I could set them up to work with Compiz with my Radeon HD 4870.

Thanks!

---

