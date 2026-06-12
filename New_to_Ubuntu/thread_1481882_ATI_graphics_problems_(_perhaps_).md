---
title: "ATI graphics problems ( perhaps )"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by stevoo on 2010-05-13
Hello, 

I am having some serious problems with my graphics i believe.

Attaching any logs is rather extremely hard ! 

I have a pc home that i used 8.04 Server edition.
i decided to upgrade to 10.04 a week ago.
Everything went fine, for over a week..

So i updated yesterday with some packages, and tried restarting as a new kernel was .22
I was doing this remotely away from my PC, and it never come up again.


So when i went home i was greeted with a small white shell window on the top right that takes 1/6th of the screen.
The rest of the screen in black and the cursor turns into an X there.

So everything i was doing it was done through a shell as of now.
So my VGA card is a ATI HD 3200, so naturally i though video cards problems.
I went and downloaded the official ATI catalyst drivers and installed them. I tried building a specific package with  --buildpkg Ubuntu/lucid but it was complaining to me something about fglrx not being istalled correctly.

I tried uninstalling fglrx and reinstalling it but it was not letting me as it was saying a link was not matching. 
I then remove the link that was complaining with dpkg-sylink --remove{or something like that }, that worked i uninstalled fglrx restarted and reinstalled fglrx.

So i said let me try just with fglrx if it is working, restart once more, the initial ubuntu login was using a more wide screen, so it was an improvement.

I then installed ATI official drivers, did a aticonfig --initial -f to set it up rebooted, the initial ubuntu logo was back to using almost half the screen. Bad sign 

I then typed in the small white screen 'exit' and it took me back to the login screen of having to select which user to login, the normal gui. 

Had only one user , so i logged in and created another user using addusser, exit again and logged in with that one.
Still the same. Wasnt expecting much from this anyway.

So back to my small white screen i tried aticcc.... something to display the ATI official settings for the drivers.

To my suprise, that was showing up in the middle of screen correctly. and i was able to change config stuff for my screen.

I was checking the /var/logs but i failed to see any errors in the Xorg.0.conf.


I am sort of puzzled currently, i runned out of ideas. Anyone has absolutely any idea in what to do ? i have been on this for over 3 hours and got nothing else than a small white box ! 



Sorry for the long, long explanation.
I will try to attach the logs tonight when i get home !

---

