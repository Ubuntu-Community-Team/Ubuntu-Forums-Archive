---
title: "MSN download error"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by Jackson7 on 2010-09-15
Hi There, I just installed Ubuntu earlier today with no problems. And a few minutes ago I installed Wine. But when i tried to download MSN it stopped after a moment of trying to install and said "Couldn't install programs" and something about how it could be a deficiency in Wine. Any advice would be greatly appreciated :)

thanks,

Jackson7

---

### Post by JRBye on 2010-09-15
Are you trying to download MSN Messenger? If so I would bypass Wine entirely and use Pidgin Instant Messenger. It is an awesome program and it will connect to all of the popular chat networks.

Go to [http://www.pidgin.im/](http://www.pidgin.im/) or open a Terminal Applicatons->Accessories->Terminal and type in: 'sudo apt-get udpate' without the quotes. It will ask you for you password. Enter that and it will update all of your sources. Then type in: 'sudo apt-get install pidgin' and hit enter. It may or may not ask you for you password again. It may also ask you to confirm the installation. Answer 'Y' and it will install.

If it is not the Messenger what is the program that you are having an issue with?

---

### Post by kaldor on 2010-09-15
> **JRBye said:**
> Are you trying to download MSN Messenger? If so I would bypass Wine entirely and use Pidgin Instant Messenger. It is an awesome program and it will connect to all of the popular chat networks.

Go to [http://www.pidgin.im/](http://www.pidgin.im/) or open a Terminal Applicatons->Accessories->Terminal and type in: 'sudo apt-get udpate' without the quotes. It will ask you for you password. Enter that and it will update all of your sources. Then type in: 'sudo apt-get install pidgin' and hit enter. It may or may not ask you for you password again. It may also ask you to confirm the installation. Answer 'Y' and it will install.

If it is not the Messenger what is the program that you are having an issue with?

Or you could just go to Applications > Software Centre and search for Pidgin :)

---

### Post by JRBye on 2010-09-15
> **kaldor said:**
> Or you could just go to Applications > Software Centre and search for Pidgin :)
Yea I guess that would work too. :-) I have been so into the shell lately that I forget the GUI tools. The  Software Centre would be the easiest. If you want to learn the shell or terminal commands you can try it that way. It is kind of interesting.

---

### Post by t0p on 2010-09-15
I don't know about the "deficiency" being in Wine - I think it's more likely the MSN app that can't step up to the plate/crease/whatever national game you happen to play...

I remember spending a few hours trying to make Yahoo's instant messenging app to install; and I learned that actually Yahoo hadn't updated its Linux client in years, Yahoo couldn't care less if all us Linux users caught something nasty and died.  These big computer-related companies (Google excepted for some reason) *hate* Linux... WAKKA WAKKA TIN FOIL HAT ALERT - because Microsoft don't like Linux.  Microsoft do not want Linux to succeed on home computers.  So they do their best to block Linux's development wherever they can.

Unfortunately for Microsoft, there are plenty of Free/"open source" equivalents of most common Windows apps.  And if you really truly can't find a suitable alternative, projects like VirtualBox and Wine exist so you can use Windows apps *with* Linux.

Go check **System > Administration > Synaptic Package Manager** or maybe [b]Applications > Apps Store (I don't use a very new version so I don't know what today's menus look like) - you will find lots of Instant Messenging apps out there.  I've used Pidgen, and I think it's okay - but I'm not really an IM man and I haven't used any of the alternatives, so my opinion probably isn't worth the tuppence I value it at.

---

### Post by 3rdalbum on 2010-09-15
Ubuntu comes with an MSN client already - it is called Empathy.

Treat Wine as a last resort, it works with only about 20% of Windows programs.

---

### Post by jeight on 2010-09-15
The reason that Wine can't install MSN is because it is not yet compatible with .net of Microsoft. Unfortunately, I'm not sure that there will be a fix in the near future. The good thing is that Empathy and Pigin work wonders as a MSN client.

---

### Post by Mark Phelps on 2010-09-15
If you're going to mess around with Wine, you need to first go to the WineHQ site and look up the compatibility ratings for the apps you want to run.

The page below is for MSN messenger -- and the ratings speak for themselves:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=127]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=127")

---

### Post by Jackson7 on 2010-09-16
thank you all for the help, i really appreciate it :D I downloaded aMSN, but when i tried it i found it very...minimal i guess you could say with some features, so i'll try pidgin :)

---

### Post by GaryTheCat on 2010-09-17
emesene is also worth a look (especially if you only really use msn messenger in windows)

---

