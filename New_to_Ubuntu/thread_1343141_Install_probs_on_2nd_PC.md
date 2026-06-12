---
title: "Install probs on 2nd PC"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by THXTom on 2009-12-01
[FONT=Verdana]Hi all,[/FONT]
[FONT=Verdana]Got ubuntu installed on 1st old P4 1.3 system now moving on to 2nd PC.[/FONT]
[FONT=Verdana]It's a Pentium D, 2.8, w/scuzzy Seagate 78gig.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]I originally installed Debian on it- and it worked fine. Went to install Debian on 1st PC had probs. So my buddy suggested ubuntu and it worked well on 1st PC.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]So today unbuntu on 2nd PC.[/FONT]
[FONT=Verdana]Used unetbootin to load 8.04 on USB drive. booted from USB, system worked fine live. [/FONT]
[FONT=Verdana]Selected install from desktop and went through all steps.[/FONT]
[FONT=Verdana]Used "guided" to partition, when all was done doing partition, it left debian on about 3.3gigs, space for 8.04 & swap.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]OK, fine. booted from HD and first got grub error 22, fixed this with:[/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black]sudo grub[/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black][FONT=Verdana]This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black]find /boot/grub/stage1[/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black][FONT=Verdana]This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black]root (hd?,?)[/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black][FONT=Verdana]Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black]setup (hd0)[/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black][FONT=Verdana]Finally exit the grub shell[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[CENTER][CENTER][COLOR=black][FONT=Verdana][/FONT][/COLOR][/CENTER][/CENTER]
[COLOR=black]quit[/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Re booted and am now getting grub error 15.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I think this disk is hosed (with debian stuff and who knows what :)) now so I try using gparted to fix. Deleted all parts., made unallocated, formatted to ext3, resized drive to max and booted into live, install to HD from live......[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Still getting grub 15 error.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I was going to try this I found:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
***[COLOR=black][FONT=Verdana][SIZE=3]Grub Error 15 File Not Found[/SIZE][/FONT][/COLOR]***[I][COLOR=black][FONT=Verdana]
 [/FONT][/COLOR][/I]
***[COLOR=black][FONT=Verdana]I have found an easier way to do this.[/FONT][/COLOR]***
***[COLOR=black][FONT=Verdana]Quote:[/FONT][/COLOR]***
[CENTER][CENTER]***[FONT=Verdana][/FONT]***[/CENTER][/CENTER]
[B][I][FONT=Verdana]When it sends you back to the list of choices, hit "c"
That will bring you to a Grub prompt.
grub>
If you installed a /boot partition, do[/FONT][/I][/B]
***[FONT=Verdana]Code:[/FONT]***
[CENTER][CENTER]***[FONT=Verdana][/FONT]***[/CENTER][/CENTER]
***find /grub/stage1******[FONT=Verdana] [/FONT]***
[CENTER][CENTER]***[FONT=Verdana][/FONT]***[/CENTER][/CENTER]
***[FONT=Verdana]If you did not do a /boot partition [most likely choice] do[/FONT]***
***[FONT=Verdana]Code:[/FONT]***
[CENTER][CENTER]***[FONT=Verdana][/FONT]***[/CENTER][/CENTER]
***find /boot/grub/stage1******[FONT=Verdana] [/FONT]***
[CENTER][CENTER]***[FONT=Verdana][/FONT]***[/CENTER]
[CENTER]***[FONT=Verdana][/FONT]***[/CENTER][/CENTER]
***[FONT=Verdana][/FONT]***

***[COLOR=black][FONT=Verdana](from[[COLOR=#0000ff] budman[/COLOR]]("http://www.linuxforums.org/forum/gentoo-linux-help/31581-error-15-file-not-found-startup.html"))[/FONT][/COLOR]***[B][I][COLOR=black][FONT=Verdana]

One of these commands will give you an answer like[/FONT][/COLOR][/I][/B]
***[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]***
[CENTER][CENTER]***[COLOR=black][FONT=Verdana][/FONT][/COLOR]***[/CENTER][/CENTER]
***[COLOR=black]root (hd0.0)[/COLOR]******[COLOR=black][FONT=Verdana] [/FONT][/COLOR]***
[CENTER][CENTER]***[COLOR=black][FONT=Verdana][/FONT][/COLOR]***[/CENTER][/CENTER]
[B][I][COLOR=black][FONT=Verdana]Now press Esc.
Select the first boot option and press "e"

Press "e" again on the root option
Change the hd(X,X) to whatever you got above. for me it was hd (0,0).
Press Enter.
Now press "b"

Ubuntu should load up.

Now that you are in, you need to change this for good.
Open a terminal and enter[/FONT][/COLOR][/I][/B]
***[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]***
[CENTER][CENTER]***[COLOR=black][FONT=Verdana][/FONT][/COLOR]***[/CENTER][/CENTER]
***[COLOR=black]sudo gedit /boot/grub/menu.lst[/COLOR]******[COLOR=black][FONT=Verdana] [/FONT][/COLOR]***
*[COLOR=black][FONT=Verdana] [/FONT][/COLOR]*
*[COLOR=black][FONT=Verdana]or, depending on your setup[/FONT][/COLOR]*
*[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]*
[CENTER][CENTER]*[COLOR=black][FONT=Verdana][/FONT][/COLOR]*[/CENTER][/CENTER]
*[COLOR=black]sudo gedit /grub/menu.lst[/COLOR]**[COLOR=black][FONT=Verdana] [/FONT][/COLOR]*
[CENTER][CENTER]*[COLOR=black][FONT=Verdana][/FONT][/COLOR]*[/CENTER][/CENTER]
[I][COLOR=black][FONT=Verdana]Scroll down towards the bottom of the file, and you will find the same "root (hdX,X)" change it appropriately, and you can save!

Also while editing, you can go ahead and change all of the root options for the different ubuntu modes, because they are all most likely wrong.[/FONT][/COLOR][/I]
*[COLOR=black][FONT=Verdana] [/FONT][/COLOR]*
[COLOR=black][FONT=Verdana]But I'm just not that proficient enough w/Linux yet.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Would knoppix or Super Rescue CD allow me to wipe the drive totally clean and just start fresh, or another wipe & zero fill app.? My boot options include a floppy drive, USB, CD.....[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Tried booting from an Arconis rescue CD, wont load.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Still searching forum for ideas....[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks, T[/FONT][/COLOR]
*[COLOR=black][FONT=Verdana] [/FONT][/COLOR]*
*[COLOR=black][FONT=Verdana] [/FONT][/COLOR]*
*[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]*
*[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]*
*[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]*
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by cariboo on 2009-12-03
Why not just use you live CD to wipe the drive? Once at the desktop open a terminal and type:

```
sudo dd if=/dev/zero of=/dev/sdX
```

Where /dev/SdX=the drive to be wiped. Go away for a couple of hours, as it may take some time.

---

