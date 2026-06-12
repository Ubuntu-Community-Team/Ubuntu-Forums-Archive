---
title: "new gnu/linux user, hello"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by paks.dreamer on 2009-07-08
**what I would have posted yesterday if I wasn't busy playing with my new toy**: Hey, I'm a new user in the gnu/linux community. Just wanted to say not only did Ubuntu prove to be a wonderful and relatively simple experience for me as a beginner, installing & learning on my own, it also saved my spare old "jarred" hard drive that had crashed in the windows kernel or some such -- now I have two working drives. Awesome.

**& today**: Still loving this thing.  I've had to switch to my "other" drive for a while to copy files, patch a game, and some other windows-related business, and I can't wait to switch back.  I'm going to look into running WINE (or a good alternative) so that I'm not physically switching drives just to game and run Rhino (3D CAD required for my course), though at the moment I need more cables if I want to use both drives.  I'm also looking into setting up my drives in a RAID 1 (or a better alternative? -- discuss); assuming that would be a good idea, since I seem to have a spare.  Both are 320G seagate if that makes a diff.

Nice to meet part of the community here. I hope I've posted this in the right forum -- couldn't seem to find a suitable place for an intro.  I'll try to check in from time to time.


[SIZE=1]~Paks.[/SIZE]

---

### Post by Tibuda on 2009-07-08
Welcome!

The last VirtualBox version (3.0) has better support for graphic cards, so you should try it.

---

### Post by ivanvajar on 2009-07-08
Welcome! First thing to be done is setting up your boot loader so you can boot into both systems without any drive switching.

---

### Post by Paddy Landau on 2009-07-08
> **paks.dreamer said:**
> I'm going to look into running WINE (or a good alternative)
If you want to use Wine, I strongly recommend that you take a look at [PlayOnLinux]("http://www.playonlinux.com/"). It's a manager for Wine, making it really easy to install and uninstall Windows programs.

---

### Post by paks.dreamer on 2009-07-08
Thanks for the replies and tips, I'll look into those things you suggested.  And yes, a boot loader sounds like a good idea for once I get those extra cables, but then I'll try to ditch windows when I can, so I may not use it much.  At current I can only plug in one HDD at a time.

---

### Post by niteshifter on 2009-07-08
> **danielrmt said:**
> Welcome!

The last VirtualBox version (3.0) has better support for graphic cards, so you should try it.

I'd wait a bit on that, there's a permissions bug with shared folders on a Windows Guest:
[See here ]("http://ubuntuforums.org/showthread.php?t=1202319")(ubuntuforums.org).
[And here ]("http://www.virtualbox.org/ticket/4381") (virtualbox.org).

Yeah, it's fixed in the current SVN - but let's not make the new user's life more difficult. ;) 

Vbox 2.2.4 is worth a try, however. Or wait for the next 3.0 maintenance release.

---

### Post by paks.dreamer on 2009-07-10
Noted. ;x

---

### Post by psycosteve on 2009-09-28
As we speak I am starting my first linux system. I am piecing together a Dell Optiplex gx260 (small form factor )P4 2.8gb with 512 mb of ram,and a 20gb HD a throwaway from a law firm . I had win 2000 on it for a while so I know that the core does in fact work . I am building the box to get experience and figure why not .  I already use firefox open office and opera to an extent but I wonder about bit torrent clients and gaming as that is what I mainly use my windows box for .

---

### Post by jmszr on 2009-09-28
psycosteve,

Ubuntu comes with Transmission as the default bittorrent client, some  people prefer Deluge or Vuze - anyway, here's a list of bittorrent clients available: [http://www.ubuntugeek.com/list-of-bittorrent-clients-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-bittorrent-clients-available-in-ubuntu.html) . Here is the Ubuntu Forums gaming section: [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93) .

Edit: this may be of interest to you also (games):[http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/) and: [https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games) and: [http://www.brighthub.com/computing/linux/articles/30780.aspx](http://www.brighthub.com/computing/linux/articles/30780.aspx)

---

### Post by humphreybc on 2009-09-29
> 
"...prove to be a wonderful and relatively simple experience for me as a beginner, installing & learning on my own."


Holy Crap, we don't hear that around here much!!!

---

### Post by paks.dreamer on 2009-09-29
**humphreybc**: :]

**psycosteve**: I found my gaming a bit stunted, but nothing serious, as I can run most of my games and favourite MMOs in WINE without a hitch, including valve games through steam, and I play guild wars regularly.

Virtualbox or something would be even better than WINE as it can run a native windows copy, but I don't have a copy of windows yet.  I haven't used windows at home since I switched.

Problems I have with my gaming in linux so far is getting xfire to pick up on certain games (though I haven't put much time in to figure it out), and won't run any game which uses nprotect gameguard, as it uses .DLL processes and runs at kernel (probably not an issue with virtualbox), and an inconsequential glitch at rare times where I "lose" my mouse cursor in GW and have to reboot the client if I want it back.  Gameguard is horrible and does not run well (if at all) for all windows users anyway.  It's a bit of a loss as I was keen on playing trickster sometimes, but I have my other games. *shrugs*

---

