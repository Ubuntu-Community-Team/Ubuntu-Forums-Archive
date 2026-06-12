---
title: "Windows Game on Cdrom"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by idproc on 2008-12-12
I'm new to ubuntu and I have some games on Cdrom that I would like to play how do I get these games to run. Thanks

---

### Post by -kg- on 2008-12-12
If they're Windows games, you will either need to learn one of the emulators, like WINE, or you'll have to run them under Windows.

I know the feeling.  I particularly like MS Flight Simulator X, and the best of us have tried to get it loaded in WINE unsuccessfully.  So I keep Windows around so I can use that (that and DeLorme mapping and GPS software).

Have you checked out some of the games that are available in the Repositories?  Check out games under Synaptics and see what you can find.  I found a couple of flight simulators written for Linux, though I haven't tried them out yet.

GL!

---

### Post by idproc on 2008-12-12
Thanks, Is it possible to only go with ubuntu and still live a normal computer life.

---

### Post by noway on 2008-12-12
Sure it's possible but it depends on what you think is "a normal computer life". Obviously Windows program won't work on Ubuntu (just like that) just as OS X programs won't work on Windows. 

But as -kg- wrote there is a solution. Wine lets you run Windows programs. You can search Wine AppDB to see if your games will work.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Good luck!

---

### Post by sneeks on 2008-12-13
depends on the games you want to run realy,age of empires and stuff run fine under wine but they are quite old realy,i dont know of any sport's games that run(please correct me if im wrong).
although world of warcraft and others of that ilk still do.
if the linux community could crack this one it would be a god send  !!!!

---

### Post by JKBurton on 2008-12-13
I never had any luck with wine until Ubuntu 8.10, and now it's worked on nearly everything I throw at it.

Install Wine.  Run Applications/Wine/Configure Wine and set the Windows version to "Windows 98". Yeah, I know, seems like it should be XP or Vista, but 98's the one that usually works best. (If your game won't install under Win98, give Win2000 a try. Worked for me with Morrowind)

Now, on the Graphics tab, enable "Emulate a virtual desktop", and give it a size that will make an appropriate window on your desktop. You can turn this off later for many games and they'll still work, but I always install and do my first test with it turned on.

Now open "Places/Removable Media", and whatever your game CD drive is. Double-click on SETUP.EXE, and best of luck!

The Wine AppDB, incidentally, looks way out-of-date to me. Most apps don't have an entry posted since Wine was still in beta testing, so aren't valid.

---

