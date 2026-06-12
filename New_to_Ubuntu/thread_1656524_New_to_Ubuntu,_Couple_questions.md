---
title: "New to Ubuntu, Couple questions"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by steakbbq on 2010-12-31
First I want to say how much I am enjoying linux/ubuntu. The people that made this did a really excellent job. IMO there is still a long ways to go as far as improvements are concerned.


[LIST=1]
[*]in linux/ubuntu it seems like installing stuff doesnt work like in windows. unless you get it from the software center. there have been several things i have downloaded that i just run.. was confusing at first, probably took me close to 2 hours to run my first program not from the software center haha. could anyone clarify this a bit?
[*]im running an acer 3620 and ubuntu seems a bit slower then windows xp on my system, is there maybe something i should do to speed up the os? i turned the effects for compiz down to the lowest but it seems like ubuntu hangs a lot and i get grey windows a little to frequently.
[*]i wasnt able to get flash to work for firefox.
[*]i wasnt able to get java to work.
[*]i play guitar so i wanted to check out the gtkguituner so i downloaded it from the software center. installed fine but when i go to run it nothing pops up, the program doesnt even show up in the system monitor.
[*]i also downloaded tuxguitar but when i try to play a song in it no sounds come out, im assuming that im missing the midi sounds lib or something.
[*]couldnt get utorrent to work so i got ktorrent. transmission was not connecting to  seeders, and there were plenty of seeders.
[*]managed to get the minimize close maximize from the wrong side to the right :P
[*]managed to bind xkill and system monitor.
[/LIST]
any help would be grealy appreciated.

i have really enjoyed learning this new os and i think its a keeper. i completely uninstalled windows and im hoping to just use vm player because i have magic jack and i need it ><

thanks a lot for this awesome os and nice to meet yall:guitar:

---

### Post by Locke_99GS on 2010-12-31
> **steakbbq said:**
> First I want to say how much I am enjoying linux/ubuntu. The people that made this did a really excellent job. IMO there is still a long ways to go as far as improvements are concerned.


[LIST=1]
[*]in linux/ubuntu it seems like installing stuff doesnt work like in windows. unless you get it from the software center. there have been several things i have downloaded that i just run.. was confusing at first, probably took me close to 2 hours to run my first program not from the software center haha. could anyone clarify this a bit?
[*]im running an acer 3620 and ubuntu seems a bit slower then windows xp on my system, is there maybe something i should do to speed up the os? i turned the effects for compiz down to the lowest but it seems like ubuntu hangs a lot and i get grey windows a little to frequently.
[*]i wasnt able to get flash to work for firefox.
[*]i wasnt able to get java to work.
[*]i play guitar so i wanted to check out the gtkguituner so i downloaded it from the software center. installed fine but when i go to run it nothing pops up, the program doesnt even show up in the system monitor.
[*]i also downloaded tuxguitar but when i try to play a song in it no sounds come out, im assuming that im missing the midi sounds lib or something.
[*]couldnt get utorrent to work so i got ktorrent. transmission was not connecting to  seeders, and there were plenty of seeders.
[*]managed to get the minimize close maximize from the wrong side to the right :P
[*]managed to bind xkill and system monitor.
[/LIST]
any help would be grealy appreciated.

i have really enjoyed learning this new os and i think its a keeper. i completely uninstalled windows and im hoping to just use vm player because i have magic jack and i need it ><

thanks a lot for this awesome os and nice to meet yall:guitar:


Linux is not Windows. Thats right, I said it. Just because it doesn't behave like Windows doesn't mean it's incomplete. It is not a Windows clone, neither is it intended to be. Along those lines, I would invite you to make these improvements and submit them to your favourite distro or (preferably) upstream. The people that created and continue to improve and polish Linux and it's DE's and distro's are you and me.

1. Tens of thousands of applications are available in the repo's. (enable all of them in software-sources) Running a binary on Linux will function exactly as on Windows, except individual binaries in Linux don't usually care about installing themselves. That is up to the user to manually place, make links, and add to menu, or for the packagers.

2. Linux performance "issues" is generally disk IO related. Look up performance tweaks for the filesystem you chose, or change your filesystem to one that better matches your needs/expectations.

3. Install the flashplugin-installer package.

4. Install the sun-java6-jre and sun-java6-plugin packages. 

5. Evoke it from a terminal and let us know the output.

6. If it uses PulseAudio, make sure your sound is unmuted and volume is proper. If it still doesn't work, from a terminal run *alsamixer* and make sure the proper outputs are unmuted.

7. uTorrent is a Windows application. If you really, really need it, it must be installed via WINE. I don't think very many people have any issues with Transmission. A decent uTorrent alternative is called Deluge. It's probably in the repo's, but I'm not going to search for you. Sorry.

8. Good.

9. Good.

---

### Post by ikt on 2010-12-31
Welcome :)

Just to let you know there is a learning curve going from windows to ubuntu, but once you get the hang of things ubuntu is definitely easier to run and use than windows ever was.

> **steakbbq said:**
> [*]in linux/ubuntu it seems like installing stuff doesnt work like in windows. unless you get it from the software center. there have been several things i have downloaded that i just run.. was confusing at first, probably took me close to 2 hours to run my first program not from the software center haha. could anyone clarify this a bit?

You should be aiming to get 99.9% of all your software from the software centre, the other .1% should have .deb package files available for easy installation, there is also the ability to add software to the software centre via ppas, here's a guide for that:

[http://linuxers.org/howto/how-install-any-software-ubuntu-ppa](http://linuxers.org/howto/how-install-any-software-ubuntu-ppa)

But as mentioned 99% of all software is usually in the repos/software centre.


> **steakbbq said:**
> 
[*]im running an acer 3620 and ubuntu seems a bit slower then windows xp on my system, is there maybe something i should do to speed up the os? i turned the effects for compiz down to the lowest but it seems like ubuntu hangs a lot and i get grey windows a little to frequently.

Unfortunately the system specs on that laptop are pretty terrible, I actually have an Asus EEPC with similar specs beside me and yeah, I agree it is a bit laggy.

There is another option of installing a varient of ubuntu on it called lubuntu, you can download it here:

[http://lubuntu.net/](http://lubuntu.net/)

> **steakbbq said:**
> 
[*]i wasnt able to get flash to work for firefox.

Ubuntu software centre > Search for: adobe flash, if the adobe flash plugin is installed then we can look at other things :)

> **steakbbq said:**
> 
[*]i wasnt able to get java to work.

Ubuntu software centre > Search for: java, same as above, this might help:

[http://www.clickonf5.org/linux/how-install-sun-java-ubuntu-1004-lts/7777](http://www.clickonf5.org/linux/how-install-sun-java-ubuntu-1004-lts/7777)

> **steakbbq said:**
> 
[*]i play guitar so i wanted to check out the gtkguituner so i downloaded it from the software center. installed fine but when i go to run it nothing pops up, the program doesnt even show up in the system monitor.

You can usually find out if a program is having problems by going:

Applications > Accessories > Terminal and typing the program name, in the case of gtkguitune it doesn't work for me either, and we're not the only ones:

[http://ubuntuforums.org/showthread.php?t=1640427&highlight=gtkguitune](http://ubuntuforums.org/showthread.php?t=1640427&highlight=gtkguitune)

So I'll take a look into it and see if it's fixable.

> **steakbbq said:**
> 
[*]i also downloaded tuxguitar but when i try to play a song in it no sounds come out, im assuming that im missing the midi sounds lib or something.


> **steakbbq said:**
> 
[*]couldnt get utorrent to work so i got ktorrent. transmission was not connecting to  seeders, and there were plenty of seeders.

You might not find this helpful but I believe deluge torrent is the best torrent client on ubuntu, which you can get the ppa for here:

[http://deluge-torrent.org/](http://deluge-torrent.org/)

just to be certain, have you forwarded the appropriate ports on your router?

> **steakbbq said:**
> 
[*]managed to get the minimize close maximize from the wrong side to the right :P

You get used to it =)

> **steakbbq said:**
> im hoping to just use vm player because i have magic jack and i need it ><

Have a look at virtualbox, it's the easiest vm software I have ever used, you can literally setup a vm in under 2 minutes.

> **steakbbq said:**
> 
thanks a lot for this awesome os and nice to meet yall:guitar:

If you feel like helping out the best thing to do is familiarise yourself with launchpad and report any and all bugs you run across :)

---

