---
title: "trying out ubuntu"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by zxy on 2009-03-01
ok so ive downloaded and have ubuntu as my other os

but when i start it up, it looks like msdos, i was wondering if anyone could help me with the gui.


i found this site called gnome.org but im not really sure what it does or how to load it up onto ubuntu

---

### Post by taurus on 2009-03-01
1.  What is the spec of your machine, especially RAM?

2.  Did you remember to do the checksum of the ISO image after you've downloaded it?

3.  Did you burn it at a slow speed like 4x?

4.  Did you run check cd for defects at the initial screen (booting from the CD)?

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso](https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso))

---

### Post by zxy on 2009-03-01
> **taurus said:**
> 1.  What is the spec of your machine, especially RAM?

2.  Did you remember to do the checksum of the ISO image after you've downloaded it?

3.  Did you burn it at a slow speed like 4x?

4.  Did you run check cd for defects at the initial screen (booting from the CD)?

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso](https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso))

1. [specs here]("http://www.radioshack.com/product/index.jsp?productId=3204548&CAWELAID=211617859")

2. nope :\

3. nope :\

4. nope :\

soz for late  repost but im exercising also right now

---

### Post by pspsampsp on 2009-03-01
im guessing theres something like this Ubuntu 8.10 "intrepid ibex" Ubuntu tty1

Ubuntu Login:

type your username press enter then type your password and press enter and the type startx or start-x if that doesnt work put in your ubuntu cd and type   "sudo apt-get install ubuntu-desktop" without quotes and turn your computer off then back on and it should work.

---

### Post by thtrgremlin on 2009-03-01
when you startup from the CD, there is an option to "check CD for defects". that should cover the above issues. If it reports defects, then you want to check the iso to see if it downloaded correctly. If you can provide a likn to the CD you downloaded, I can show you how to check it.

Further, when the computer starts up and before it leaves you at the "command line", are there any error messages? Is it prompting you to "login:"? Did the screen flicker for maybe a second or two before it went to that "command line"?

In my experience, and please correct me if you have seen different taurus, bad CDs or corrupted ISOs fail to install, not install buggy.

Sorry to overload you with information, but I am sure this can be resolved without too much trouble. Just need a bit more information about what you are seeing at startup.

---

### Post by thtrgremlin on 2009-03-01
> **pspsampsp said:**
> im guessing theres something like this Ubuntu 8.10 "intrepid ibex" Ubuntu tty1

Ubuntu Login:

type your username press enter then type your password and press enter and the type startx or start-x if that doesnt work put in your ubuntu cd and [COLOR="Red"]type   "sudo apt-get install ubuntu-desktop" without quotes and turn your computer off then back on[/COLOR] and it should work.

Just to note, don't restart the computer until after it finishes :) In case it needed to be said  :)

---

### Post by taurus on 2009-03-01
> **thtrgremlin said:**
> when you startup from the CD, there is an option to "check CD for defects". that should cover the above issues. If it reports defects, then you want to check the iso to see if it downloaded correctly. If you can provide a likn to the CD you downloaded, I can show you how to check it.

Further, when the computer starts up and before it leaves you at the "command line", are there any error messages? Is it prompting you to "login:"? Did the screen flicker for maybe a second or two before it went to that "command line"?

**In my experience, and please correct me if you have seen different taurus, bad CDs or corrupted ISOs fail to install, not install buggy.**

Sorry to overload you with information, but I am sure this can be resolved without too much trouble. Just need a bit more information about what you are seeing at startup.

I've never claimed it's installed buggy.  If you have a bad download (checksum doesn't match) or a bad burn (burn too fast, default speed), it will not install, period.  That's why I've asked him/her to go through all those steps first before he/she can install Ubuntu on that new Toshiba laptop.

---

### Post by mkvnmtr on 2009-03-01
Did you by chance use the server install disk? On that one all you get is a log in you don't get a gui.

---

### Post by pspsampsp on 2009-03-01
i think he or she might have accidently done a server install or for some reason the installer just didnt install gnome like what happened to me when i first tried ubuntu however the commands i said to run should fix the problem as they did for me

---

### Post by zxy on 2009-03-01
i dont see any errors come up and yeah i think i downloaded the server pack >.>

---

### Post by thtrgremlin on 2009-03-01
No need to download the other CD. As mentioned above, you can just install the desktop from that command line after you type in your username and password:
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

That should have you all set!

Enjoy!

---

### Post by zxy on 2009-03-01
honestly i dont even know my username or pass

---

### Post by thtrgremlin on 2009-03-01
didn't you pick one when you installed?

It will be an important thing to remember. If you don't remember, may just be easier to download the right version (Desktop) and go from there.

---

### Post by zxy on 2009-03-01
i dont even remember it aasking me....

how can i uninstall the server os?

when i start up my laptop it comes up vista or ubuntu, how can i get it back to just vista automatically starting again, im gonna try re downloading the right thing this time

---

### Post by pspsampsp on 2009-03-01
i think you can just download the ubuntu desktop cd and just overwrite the server ubuntu install instead of removing ubuntu

---

### Post by zxy on 2009-03-01
i rather have it gone completely and just start over

any help please?

---

### Post by stalkier on 2009-03-01
> **zxy said:**
> i rather have it gone completely and just start over

any help please?

Before you do anything. Download the Super Grub Disk from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) This will be a great tool in case something goes wrong with you linux GRUB loader. If the loader is messed up you will not be able to get into Windows either. Well I am sure there are ways but it is best if you download and burn this tool.

---

### Post by pspsampsp on 2009-03-01
you will need to delete the linucx partions and have them as unallocated space and as i am pressed for time i cant help you there but i can give you a link for extending your windows partion: [http://support.microsoft.com/kb/325590](http://support.microsoft.com/kb/325590)

---

### Post by thtrgremlin on 2009-03-01
When in the installer, you can use the 'partitioner', part of the setup, to delete everything. There are ways of completely erasing the disk, but they are not only unnecessary, but they take a very long time.

When you start the installer from the CD, select the first option that says "use entire disk" which it will warm will destroy all data on the disk. Doing it this way, you will never see any sign of your old install.

Still happy to help with any other questions. Also, if you just need to erase the disk completely without doing anything else, I can tell you, because I understand the overwhelming desire, and I don't believe in censorship  :) But as I said, this won't make any "small" difference, or "unlikely" difference, it will be NO difference.

If you love to tinker, I see you having great fun with Gnu/Linux and Ubuntu. It is a endlessly long road of information, gentle learning curve as much as you desire, and everything along the way is fun to learn. At least that has been my experience.

---

### Post by zxy on 2009-03-01
dam

thought linux would be easier...

---

### Post by thtrgremlin on 2009-03-01
Installing an OS is getting easier, but that initial setup has potential to trouble anyone. It can be easy, and it can be hard. Personally, Installing XP and Vista go nice and easy... but if you run into any problems at all, you can get really fubar'd unless you are some kind of Windows master. The difference is that many new computers come with Windows already setup. With Ubuntu, until recently, everyone suddenly had to learn how to install an OS. In my experience, and especially with these forums, problems can often be quickly resolved, and almost never requiring another computer. Windows? Every problem requires AT LEAST another machine and floppies or CD's, or being forced to make your own install disk! GAH!!! (sorry, recent awful experience)

Sounds like so far you had a smooth install, you just got the wrong disc.

Points on your patience though. You're getting there.

---

### Post by zxy on 2009-03-01
forget uninstalling it now

i read on another post if i install the right one, it makes the server one goes away


and i think i downloaded the desktop version honestly cause the iso file still on my vista screen and it says 8.10-desktop-i386

but i also removed ubuntu from the desktop uninstaller....not sure how that will affect me

---

### Post by zxy on 2009-03-01
and im pretty positive i downloaded desktop version

but i never remember it asking me for a username or pass and i never saw a gui when i load it up

---

### Post by thtrgremlin on 2009-03-01
Honestly, you have me pretty lost. When you started up the computer from the live cd, you should have been able to boot to a totally working desktop. From there, if you run the 'installer' on the desktop, it should ask for a bunch of information, and after that, it installs taking about 15-20 to put everything into place. If this doesn't sound like your experience, you should try again.

---

### Post by SunnyRabbiera on 2009-03-01
there is the possibility of a bad burn

---

### Post by pspsampsp on 2009-03-01
could you please tell me if there is any text at all on the screen and what that text is.

---

### Post by zxy on 2009-03-01
sure, imma load it up again right now

---

### Post by pspsampsp on 2009-03-01
also as another idea could you use a camera to take a picture

---

### Post by zxy on 2009-03-01
since ive uninstalled it from windows uninstaller this comes up now

trying hd(1,0)
and keeps doing it up to 3

and now gives me this error

cannot find GLRDR in any device, press ctrl+alt+del to restart.

but when i start my laptop up, it still ask ubuntu or vista

---

### Post by zxy on 2009-03-01
also about to eat dinner so i will try getting pics in a couple of minutes

---

### Post by pspsampsp on 2009-03-01
do you have a windows vista cd that you can use to repair your vista installation and did you use wubi to install ubuntu?

---

### Post by zxy on 2009-03-01
erm.... i downloaded ubuntu straight from this site and burned it to a cd, i dont know what wubi is and i think i still have the box and vista cd

---

### Post by pspsampsp on 2009-03-01
ok so from what i understand you can boot windows vista fine if you select it from the menu but when you choose ubuntu it comes up with an error? if i am right i would say you need to boot off your windows vista cd/dvd and do a repair install and that should get your windows vista back to normal and then you can start fresh with dual booting ubuntu

---

### Post by zxy on 2009-03-01
kk ty

---

