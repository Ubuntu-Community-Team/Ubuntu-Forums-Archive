---
title: "can't install live cd!"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by DElliottJr on 2009-03-09
i have been at this for two whole days now! i still can't even install these disks! and i've tried 3 different distros! and nothin! i was able to install intrepid but it will not go into desktop or gnome, i was told to reinstall and i can't even get that far!! i'm doin my research and hittin walls here!! there is,in all 3 distros(intrepid,hardy, and mint) an error screen right after the upsplash is done loading but it goes so fast i can not read or pause it. is it possible to hold this error screen? there is more than i could list here alone and i am already takin to long to get this out!! thank you

---

### Post by Crafty Kisses on 2009-03-09
Have you tried the [Alternate CD]("https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD")? Try the alternate CD and see if that works. I'd also like to know the specs of your machine. Have you checked the md5sums on the CD's you burned?

---

### Post by DElliottJr on 2009-03-09
dell inspiron 1100, celeron 2.30 ghz, 1150mb ram, with 20gb imternal hd, and 320gb external by western digital(this is where intrepid is installed by itself)yes i have checked all md5 checksums. this is drivin me nuts! also once i get past the upsplashes the screen is either black or just matrix.i think it may have to do this. and hopefully this alone ;)thanx

---

### Post by Crafty Kisses on 2009-03-09
I'd suggest you try the alternate CD, and if that fails try checking your RAM.

---

### Post by davidryder on 2009-03-09
Are you completely unable to boot into the live cd?

When the menu screen initially comes up you can edit the boot command and specify the nosplash option then you can see the errors.

---

### Post by DElliottJr on 2009-03-09
alright, this will be disk number 8! going throught these like water! and check RAM? i just upgraded from 256mb to 1.2gb i've run everest on it and bios agent to upgrade that too(from dell.com) and the ram is recognized across the board.. these error sreens that go by after upsplash don't have any useful info? going for the alternate! and again i appreciate it!

---

### Post by DElliottJr on 2009-03-09
davidryder Re: can't install live cd!

--------------------------------------------------------------------------------
Are you completely unable to boot into the live cd?

When the menu screen initially comes up you can edit the boot command and specify the nosplash option then you can see the errors.  ........
        yea i can boot from the cd and that about all.i get the menu that give the option to run or install or check for disk errors etc... how do i edit the boot command from here? i would love find out how! so i could actually reference some of these errors! if i could search this stuff out i wouldn't have to bug ya so much ;)

---

### Post by davidryder on 2009-03-09
When the main menu comes up when you first turn your PC on you will select the language (assumingly) then you can press F6 to edit the boot command. 

[img]http://img4.imageshack.us/img4/8162/ssmar0820092319.png[/img]

Remove the quiet from the end of the command and replace splash with nosplash. You will now see all the init process :)

---

### Post by DElliottJr on 2009-03-09
excellent thanx!:D

---

### Post by DElliottJr on 2009-03-09
well.. i didn't see any errors read out and all the checks at the end and the screen goes black before thay could finish. i used ctrl+alt+bkspce to return and they all finished ok and now im at the brown background with no install windows(i am on two computers)well i guess the alternate cd is the route to take now?

---

### Post by davidryder on 2009-03-09
If you are using 8.04 it might not hurt to try 8.10, or vice versa. That or the Live CD... it sounds like a hardware/driver problem and sometimes a different version can help. The alternative CD is just as a viable route IMO.

---

### Post by DElliottJr on 2009-03-09
yea i'm willing to try it all! not gonna give up so easy! i'm running xp  now. i've tried 8.04, 8.10,and even linux mint6... this is definitly something to do with my old laptop!!  hopefully i can figure it out and get around it

---

### Post by diwas on 2009-03-09
Do you mean that it loads and the screen goes blank after the "boot loading"?
If yes, try removing compiz-core by booting through the recovery mode.

---

### Post by Crafty Kisses on 2009-03-09
Yes try the alternate CD now.

---

### Post by SyberKowboy on 2009-03-10
I've been having a simialr issue with the 8.10 distro. I get to the first menu screen and select a language but then no matter how I congifure the boot options or which menu item I select it just hangs. It seems like a hardware issue but I can't find anything wrong with my hardware and 6.06 Dapper (old disrto lying around) has no problem loading into a live CD. Neither does Knoppix for that matter. I've burnt the disk twice and had the same results. I'm going to try 8.04 and see if that fixes it.

---

### Post by davidryder on 2009-03-11
I'm just making an assumption here but this may be a sign that you have unfortunately incompatible hardware, or some combination of hardware that is incompatible. I'm sure you will be able to get it to work with enough tweaking, but if it were me I would probably try a different distribution all together. 

*hides in corner* :)

---

