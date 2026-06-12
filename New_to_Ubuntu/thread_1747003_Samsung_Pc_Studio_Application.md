---
title: "Samsung Pc Studio Application"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Solstice Bahai on 2011-05-02
Does anybody know about a linux version of Samsung's Pc Studio application for syncing mobile 'phones with netbooks/notebook pcs?:)

---

### Post by Steve H on 2011-05-02
I don't think there is a version of the Samsung PC Suite (Kies) software (and Kies doesn't play well with WINE). What type of "sync" are you wanting?

I have a Samsung Galaxy S, so I tend to mount the phone as a Mass Storage Device (either in Settings or when connected the phone asks). That way I get two short cuts, one to the internal memory and one to the SD Card. I then just drag and drop the files where I want them.

I've never found a reliable way to sync address books etc, but as all of my contacts are synced with Google there is no need for me.

One last option is to run Kies/PC Suite in a VMWare machine running Windows. That might get you the functionality you desire.

Hope that helps.

---

### Post by Solstice Bahai on 2011-05-02
Thanks,I recently downloaded winetricks but find all the options there a bit on the intimidating side, as I have never used any form of emulation or whatever. All I really wanted was to be able to sync address book, contacts, and any photo I happened to make,( not that I use the camera all that much ). Apart from that not much else, by the way, really, really loving Natty!!=D>

---

### Post by Steve H on 2011-05-02
WINE can be a bit intimidating at first, but don't worry it won't (or shouldn't) break your system. Also bear in mind that _W_ine _I_s _N_ot an _E_mulator. It is an abstraction layer (it basically links GNU/Linux files to application requests for Microsoft files).

If you need a "pretend Windows" system then Virtual Machines would be the better bet. I know from experience that once you get you VM set up it should do everything you need (and doesn't require a reboot).

Have you taken a look at the Evolution website ([here]("http://projects.gnome.org/evolution/")) as what you are really doing is syncing your contacts, calendar etc with Evolution.

---

### Post by Solstice Bahai on 2011-05-03
Thanks! will give that a look-up. Hope there tutorials for using wine/wine tricks ( in PDF perhaps? ) that I can study when off line, which is more often than not with Wireless Broadband on pay as you go:( I'm still considering dual booting on my Notebook, any advice?

---

### Post by Steve H on 2011-05-03
If you need some guidance about WINE, check [here]("http://www.winehq.org/"). You'll get all the info you'll need. As for a pdf, [here you go]("http://ftp.winehq.org/pub/wine/docs/en/wineusr-guide.pdf"). I'm not too sure about the age of the doc, so it may be worth checking the Wine HQ just in case.

As for dual booting, it's no problem so long as you've put the Win partition on the first part of the drive. Windows doesn't play well unless it's the first OS on the drive. It may worth asking that question on it's own.

---

