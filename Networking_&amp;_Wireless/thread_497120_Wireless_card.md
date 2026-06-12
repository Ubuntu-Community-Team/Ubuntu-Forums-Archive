---
title: "Wireless card"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by hdshngout on 2007-07-09
This is my third time trying ubuntu, the other few times, I tried to dual boot and it failed miserably.  Anyways, this time, I have decided to go cold turkey.  My main problem is I can not seem to get my wireless card working.  (At the moment I am on an Ethernet connection, and I'm not too keen in having a 200ft Ethernet cable running through the entire house.)

But back to the card.  A few months ago, I attempted to install dapper drake and the card worked fine, but upon installing 7.04, the card refuses to work.  I have installed ndiswrapper attempted to install the card, but upon entering ndiswrapper -l, I got

> "sis163u : invalid driver!"

I'm not thrilled about this and a member of the Ohio Ubuntu team attempted to help me, but sadly he was stumped as well.  He told me to post here and possibly someone could assist me.

My card info is (I'm not sure what is needed, so heres everything).

> Ovislink Air Live 802.11G Wireless USB
WL-5460USB
FCC ID : NHPWLG1600
S/N: 5460UE5091015
MAC: 004F63007D01

Thank you for your time in reading this :)

---

### Post by fredj on 2007-07-10
Where did you get your version of ndswrapper. Open a terminal and type ndiswrapper -v and
post the result here. The version of ndiswrapper in the feisty repository is flawed in some way 
it doesn't install some drivers properly. The only way round this is to download the latest source
code from the ndiswraper site, install the build-essentials package and compile ndiswrapper
yourself.

With regard to windows drivers you want to get the latest XP drivers for your card.

---

