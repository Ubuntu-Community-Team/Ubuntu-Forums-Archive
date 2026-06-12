---
title: "Ubuntu Paranoia !!"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-19
Hi,

I seriosuly love ubuntu - I am on it every second that I can!

I have my PC running to perfection - and I am a little fearful that, as has happened in the past, something for no apparent reason goes wrong and I, again, have to re-install ubuntu.

So, my question is, is it worth me to sort off stop all future updates and downloads and just simply block all updates to prevent possible corruptions?

(I ask this because my sound just disappeared from Ibex which I found weird and very annoying, but I still LOVE ubuntu).

T H A N K S

---

### Post by taurus on 2009-02-19
Why not just do a backup system before you run the update in case you need to reverse it.

You can use partimge, [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage), or clonezilla, [http://www.clonezilla.org/](http://www.clonezilla.org/).

---

### Post by listerdl on 2009-02-19
Thats a great tip thanks - ill defintely look into it. Regards, Henry

---

### Post by Thelasko on 2009-02-19
You can install older versions of software in Ubuntu using Synaptic.  The trick is figuring out which package broke your sound.

---

### Post by listerdl on 2009-02-19
> **Thelasko said:**
> You can install older versions of software in Ubuntu using Synaptic.  The trick is figuring out which package broke your sound.

Exactly...id love to know which package broke my sound and that is the reason why i am paranoid because i really dont want to have to re-isntall everything again....

---

### Post by Thelasko on 2009-02-19
> **listerdl said:**
> Exactly...id love to know which package broke my sound and that is the reason why i am paranoid because i really dont want to have to re-isntall everything again....

Apparently if you go into file>history in Synaptic it gives you a history of your updates.

---

### Post by listerdl on 2009-02-19
amazing thanks!!!!!!!!!!!!!

---

### Post by mkvnmtr on 2009-02-19
I finally took the advice of everybody and began using a home partition. Now a reinstall or upgrade only takes about an hour and a couple of days messing around little by little to get all my apps back. I even rob some of the hidden files to put in my other distros.

---

### Post by bodhi.zazen on 2009-02-19
> **listerdl said:**
> Hi,

I seriosuly love ubuntu - I am on it every second that I can!

I have my PC running to perfection - and I am a little fearful that, as has happened in the past, something for no apparent reason goes wrong and I, again, have to re-install ubuntu.

So, my question is, is it worth me to sort off stop all future updates and downloads and just simply block all updates to prevent possible corruptions?

(I ask this because my sound just disappeared from Ibex which I found weird and very annoying, but I still LOVE ubuntu).

T H A N K S

As you become more experienced it is easier to fix problems when they occur.

"Reinstalling" == "learning"

My rule of thumb, re-installing takes 20 minutes. If it takes longer then 20 minutes to solve (for the sanity of my family) re-install.

Sure you can "learn" by fixing a broken system, so it is worth an attempt, but you can also learn from a working system :twisted:

What I do is enable automatic security only updates and review non-security updates. I update no more often then once a week (in general).

See this post : [http://ubuntuforums.org/showpost.php?p=6764763&postcount=9](http://ubuntuforums.org/showpost.php?p=6764763&postcount=9)

---

### Post by EvilRobotDrew on 2009-02-20
My suggestion would be to make a separate /home partition, and use ReMasterSys ([http://klikit.pbwiki.com/Remastersys+FAQ](http://klikit.pbwiki.com/Remastersys+FAQ)). You can make a liveDVD of your current setup and reinstall it whenever you need to (I would recommend installing a vew useful liveCD applications like GParted, ClamAV, or anything else that may be useful in repairing a system). With a separate /home partition getting your machine back to working order is easy. ReMasterSys will even bring over your wireless drivers, and having a live CD that lets you use your wireless is a godsend for me. 


Of course once you have a quick and easy way to get your machine in working order, it is time to start distro-hopping. :D

---

### Post by bodhi.zazen on 2009-02-20
> **EvilRobotDrew said:**
> My suggestion would be to make a separate /home partition, and use ReMasterSys ([http://klikit.pbwiki.com/Remastersys+FAQ](http://klikit.pbwiki.com/Remastersys+FAQ)). You can make a liveDVD of your current setup and reinstall it whenever you need to (I would recommend installing a vew useful liveCD applications like GParted, ClamAV, or anything else that may be useful in repairing a system). With a separate /home partition getting your machine back to working order is easy. ReMasterSys will even bring over your wireless drivers, and having a live CD that lets you use your wireless is a godsend for me. 


Of course once you have a quick and easy way to get your machine in working order, it is time to start distro-hopping. :D

... or use a data partition and keep your data separate from both /home and /

You can always use links

ln -s /media/data/music ~/music

and on

---

### Post by Thelasko on 2009-02-20
> **mkvnmtr said:**
> Now a reinstall or upgrade only takes about an hour and a couple of days messing around little by little to get all my apps back.

You can save a list of your installed apps in Synaptic, and then load it after a reinstall.  This should cut that couple of days down to about an hour.

---

### Post by EvilRobotDrew on 2009-02-20
> **Thelasko said:**
> You can save a list of your installed apps in Synaptic, and then load it after a reinstall.  This should cut that couple of days down to about an hour.

Unless you switch to a new distro; for re-installing ubuntu this kind of list could be a godsend though.

---

### Post by listerdl on 2009-02-22
> **bodhi.zazen said:**
> 
My rule of thumb, re-installing takes 20 minutes. If it takes longer then 20 minutes to solve (for the sanity of my family) re-install.




Since I posted this thread, a program has now failed to open. The program is audacious, the music player.

Whatever I do it will not open at all. Are you suggesting to re-install the entire OS again? Ive done that like ten times now....but I am at a loose end here. I mean I have tried to re-istall in synaptics but nothing....

Odd....

---

### Post by bodhi.zazen on 2009-02-22
Run audacious from the command line and see what error message it gives you.

---

### Post by listerdl on 2009-02-22
> **bodhi.zazen said:**
> Run audacious from the command line and see what error message it gives you.

Hi thanks for help. Well I did the above by going to ALT + F2 and hit audacious but it just does nothing, it closes the Run Application Manager.

Is that strange?

---

### Post by listerdl on 2009-02-22
In fact, I thought to replace audacious in the add/remove program but this message comes up - 

[I]Cannot remove 'audacious'

One or more applications depend on audacious. To remove audacious and the dependent applications, use the Synaptic package manager.[/I]

---

### Post by simtaalo on 2009-02-22
> **listerdl said:**
> Hi thanks for help. Well I did the above by going to ALT + F2 and hit audacious but it just does nothing, it closes the Run Application Manager.

Is that strange?

run it from the terminal not using alt+f2. the terminal will give some output which will help to solve the problem.

---

### Post by tekkieguy on 2009-02-22
nononononononono!!!!!. Most of the time, the supprots HELP your computer and fix bugs. I wouldreccomend that you do disable all other third party updates and unsupported updates because those are usually the ones that cause problems

---

### Post by bodhi.zazen on 2009-02-22
> **tekkieguy said:**
> nononononononono!!!!!. Most of the time, the supprots HELP your computer and fix bugs. I wouldreccomend that you do disable all other third party updates and unsupported updates because those are usually the ones that cause problems

That is a generalization. The most common cause of problems with audacious is corrupt configuration files in $HOME.

---

### Post by listerdl on 2009-02-22
> **simtaalo said:**
> run it from the terminal not using alt+f2. the terminal will give some output which will help to solve the problem.

What code do i enter at the terminal?

I entered the following to 'run' the program...

```
lister@DELL-laptop:~$ run audacious
bash: run: command not found
lister@DELL-laptop:~$ 

```

Obviously wrong run code! Sorry must be a very easy question for you!!

---

### Post by oldos2er on 2009-02-22
"What code do i enter at the terminal?"

 audacious

---

### Post by bodhi.zazen on 2009-02-22
Jut open a terminal and enter the command audacious

```
audacious
```

---

### Post by listerdl on 2009-02-22
THANKS!!!!!!!!!!!!!

This is what came up:

```
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
Segmentation fault

```

---

### Post by bodhi.zazen on 2009-02-22
Try deleting the audacious config file :

```
rm -rf ~/.config/audacious/config
```

You *may* need to remove the audacious directory

```
rm -rf ~/.config/audacious
```

It is "OK" to delete those files, they just hold personal preferences and they will be regenerated when you re-run audacious (which you can do from the main menu).

---

### Post by listerdl on 2009-02-22
> **bodhi.zazen said:**
> Try deleting the audacious config file :

```
rm -rf ~/.config/audacious/config
```

You *may* need to remove the audacious directory

```
rm -rf ~/.config/audacious
```

It is "OK" to delete those files, they just hold personal preferences and they will be regenerated when you re-run audacious (which you can do from the main menu).

AMAZING!!!!!!!!!!!!!!

THAT WORKED!!!!!!!!!!!!!!!

THANKS!!!!!!!!!

STRANGE....do you think that I will have to do that again?

What caused that do you think? - honestly thanks again, this is truly an amazing forum and frankly the major reason why i am still with ubuntu and hopefully always will be - thanks!

---

### Post by bodhi.zazen on 2009-02-22
I do not know the cause of the problem, my guess is a corruption in the config file.

Audacious needs this kind of cleansing , but rarely.

---

