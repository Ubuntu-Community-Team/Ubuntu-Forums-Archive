---
title: "Where are my Nvidia drivers?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by The_Proffessor on 2009-05-23
Since the upgrade to 9.04 I've noticed that Nvidia video card drivers aren't listed on the hardware app. I had em installed before for playing the lovely lovely video games...which now don't work too well. So where'd my drivers go? Any code I could feed into the terminal to get em?

---

### Post by hansdown on 2009-05-24
Hi The_Proffessor.

Try this tutorial. Hopefuly it helps.

[http://www.detector-pro.com/2009/04/how-to-install-nvidia-linux-display.html](http://www.detector-pro.com/2009/04/how-to-install-nvidia-linux-display.html)

---

### Post by zubin71 on 2009-05-24
go to system > administration > hardware drivers.
you`ll see the drivers avaiable there.
you get the option to use the version 180 or the version 173 drivers; choose 180.

it`ll download the drivers by itself and install it!
happy gaming :-)

---

### Post by The_Proffessor on 2009-05-25
I did both these things and the Nvidia drivers still don't appear on my System > Administration > Hardware drivers thingy. I only have the madwifi driver available.

---

### Post by clhsharky on 2009-05-25
Go to Synapic and search nvidia, you will find several packages named "nivdia-*something*-modalises" install each one. It wont load any drivers yet, but will make them available to you with the recommended driver in the "hardware driver" GUI

---

### Post by The_Proffessor on 2009-05-25
still no good :( went to the synaptic package manager, and reinstalled all the nvidia modaliases and still no graphics driver on my hardware gui.

---

### Post by clhsharky on 2009-05-25
What card do you have .and did you add the legacy-modaliases?

---

### Post by The_Proffessor on 2009-05-25
I think my graphics card is an ATI Radeon series. Not sure why Nvidia drivers are what I'm after other than Ubuntu installed em before I upgraded to 9.0.4 and they worked just fine. I also can't locate any legacy-modaliases in the package manager (ran quicksearch).

---

### Post by clhsharky on 2009-05-25
OK the nvidia drivers wont do anything in that case, you can remove what I told you. do you think it might be a older ATI card. ATI doesn't support legacy cards any more. But The open source drivers that come with Jaunty do. BTW the open source stack are good even 3D.

---

### Post by The_Proffessor on 2009-05-25
It's probably an older ATI. It came with the laptop I bought about 3 years ago (Toshiba Satellite A130/135 series). But you're saying the stock drivers work? The games I played before are all manner of mucked up graphics wise right now.

---

### Post by clhsharky on 2009-05-25
They have some tweaky and such here

 [https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

I use them, but TBO Id go back to 8.10 with proprietary drivers to get best game play.

---

### Post by linux000019 on 2009-05-25
alot of these suggestions work; i used 2 or three myself; before finding that going to the nvidia website and downloading their package for my video driver, installing it using their install guide, and rebooting x server was the least confusing way to do it. im a newbie to linux, and even i could figure out how to do this using the terminal; so im sure you can too

---

### Post by clhsharky on 2009-05-25
It end up he has a ATI card so none of the Nvidia stuff matters, and yes CLI is the best way & not very hard. By the_Proffessor posts, it looked like he was use to a GUI so I went that way.

Sorry for any confusion

Sharky

---

### Post by The_Proffessor on 2009-05-25
I've been reading up a bit. Apparently the consensus is that ATI cards and 9.04 just don't mix. So I'm either going to just deal with it or roll back to 8.1. Thanks for the help anyway.

Here's a link detailing the problem 
[http://blogs.computerworld.com/the_ubuntu_and_ati_blues]("http://blogs.computerworld.com/the_ubuntu_and_ati_blues")

---

### Post by clhsharky on 2009-05-25
Your welcome

"Cyber Cynic" yes that is what is right under his name is not correct all the time, and he seam to leave thing out a lot. But Whatever!
Compiz does work, and I dont think ATI/AMD is going out of business, being second to Intel and Nvidia is nothing to be ashamed of. It sure keeps them on ether toes.

---

### Post by The_Proffessor on 2009-05-25
One last thing and then I'll stop buggin y'all with my nubery. I don't suppose there's a way through deep linux-fu to revert to 8.10 without loosing all my files?

---

