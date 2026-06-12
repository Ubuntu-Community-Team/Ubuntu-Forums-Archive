---
title: "Browse C:\ in Wine?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Gael33 on 2009-02-21
I recently upgraded from Ubuntu 8.04 to 8.10 (64) and after a few little glitches almost everything is as it should be, except for one thing. Wine is working but it is very slow and the Browse C:\ drive is not working at all. Could someone help me correct this because I use the programs in Wine almost every day.
Thanks in advance,
gael.

---

### Post by Kellemora on 2009-02-21
Hi Gael

I'm on a 64 bit machine and use Wine every day too!

How are you accessing drive_c?

The few times I've needed to work in it, I just go to filesystem, /home/user show hidden files, drop down to .wine and go in that way.

Or in Gnome, you can go to Applications/wine/browse c:\drive and it pops right up.  A zillion times faster than on the 32 bit machines too!

A possibility is wine did not install right.  Save what ever data you put in your C drive on Z temporarily.  Reinstall Wine and move your data back to C again.  See if that helps.

I have a few programs for the Doze that although they shouldn't require this, due to the oversights of Doze, they MUST be run in Administrative mode.  I've never found a way to do this in Wine yet.  Even the latest release of a certain program I found the same problem and sent it back to the publisher for my money back and told him why too!  I won't run a machine in Administrative mode to use simple user programs.

TTUL
Gary

---

### Post by Gael33 on 2009-02-22
> **kellemora said:**
> hi gael

i'm on a 64 bit machine and use wine every day too!

How are you accessing drive_c?

The few times i've needed to work in it, i just go to filesystem, /home/user show hidden files, drop down to .wine and go in that way.

[color="deepskyblue"]that's the way i've had to use drive c:\ on wine.[/color]

or in gnome, you can go to applications/wine/browse c:\drive and it pops right up.  A zillion times faster than on the 32 bit machines too!

[color="deepskyblue"]gary, that's the way i would like to use wine but the link is dead. Could you write out the link in the wee box that works for you and i will insert it into mine and hopefully it will work. If not i will have to uninstall wine and start again :([/color]

a possibility is wine did not install right.  Save what ever data you put in your c drive on z temporarily.  Reinstall wine and move your data back to c again.  See if that helps.

[color="deepskyblue"]i'm not sure how to transfer the data over to the z drive (i'm a newbie) it might be quicker for me to reinstall the whole thing including prgrams.[/color]

i have a few programs for the doze that although they shouldn't require this, due to the oversights of doze, they must be run in administrative mode.  I've never found a way to do this in wine yet.  Even the latest release of a certain program i found the same problem and sent it back to the publisher for my money back and told him why too!  I won't run a machine in administrative mode to use simple user programs.

[color="deepskyblue"]nothings perfect with software etc. We're still a long way from 'star trek' but we're getting there :) [/color]

[color="deepskyblue"]thanks for your advice, gael.[/color]

ttul
gary

22/02.2009

---

### Post by Kellemora on 2009-02-22
Hi Gael

The link (command line) that Browse C_Drive uses on my computer is

```
xdg-open ~/.wine/drive_c
```

You get to this by RIGHT clicking on Applications then selecting Edit Menus, then going down to wines Browse C_Drive link and selecting PROPERTIES to edit the link.

Your's should automatically READ exactly the same as mine though I would imagine.  
There is a BROWSE button you could use also to change the command line to see if that helps.  By finding the C drive and just clicking on it, that will rebuild the command again.

Good Luck

TTUL
Gary

---

### Post by Gael33 on 2009-02-25
> **Kellemora said:**
> Hi Gael

The link (command line) that Browse C_Drive uses on my computer is

```
xdg-open ~/.wine/drive_c
```

You get to this by RIGHT clicking on Applications then selecting Edit Menus, then going down to wines Browse C_Drive link and selecting PROPERTIES to edit the link.

Your's should automatically READ exactly the same as mine though I would imagine.  
There is a BROWSE button you could use also to change the command line to see if that helps.  By finding the C drive and just clicking on it, that will rebuild the command again.

Good Luck

TTUL

Gary

Hi Gary, Thanks for getting back to me. The code in my link is exactly the same as yours. I tried following the browse, found the drive_c ... clicked on it and it opened to show the contents of the drive which meant it wasn't going to work as we thought it would. Having tried every which way, I have come to the conclusion that the problem lies in the upgrade from Ubuntu 8.04 to 8.10, it must be one of those quirky things. Oddly, when I type in terminal (Nautilus) "nautilus ~/.wine/drive_c" it opens no problem ... very strange!
Thanks for trying to help.
gael.
Gael.

---

