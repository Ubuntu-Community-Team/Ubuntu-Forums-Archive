---
title: "Dual monitor problem with 10.10"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by purelife70 on 2010-10-16
I have Dual monitor problems with 10.10, like a lot of people it seems.

I cannot get the extended desktop @ 3840X1080, I can only get mirrored.

I am using an ATI gfx card, I tried this below but it did not work for me.

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

Any help would be greatly appreciated.

thx

---

### Post by Crusty Old Fart on 2010-11-02
Howdy purelife70:

The following tutorial may be helpful:
[How to: Extend desktop across dual monitors]("http://ubuntuforums.org/showthread.php?p=10061029#post10061029")

Good Luck,

Crusty

---

### Post by scottyab on 2010-11-12
did any other newbie hit Ctrl+Alt+F1 and go wtf a terminal?? how do I follow the rest of the steps :S

I switch to other pc to follow the rest... So i ran Stop gdm/X and generated the xrog conf, but how do i edit files in the tty1 virtual shell? i get a write permission error when i type edit ~/xorg.con.new

Help mucho appreciated

---

### Post by Crusty Old Fart on 2010-11-12
> **scottyab said:**
> did any other newbie hit Ctrl+Alt+F1 and go wtf a terminal?? how do I follow the rest of the steps :S

I switch to other pc to follow the rest... So i ran Stop gdm/X and generated the xrog conf, but how do i edit files in the tty1 virtual shell? i get a write permission error when i type edit ~/xorg.con.new

Help mucho appreciated
Howdy Scottyab:

Sorry to have yanked the rug out from under you.

The very first step in the procedure I described was:
> 

[LIST=1]
[*]Press the key combination [COLOR=Blue]**Ctrl+Alt+F1**[/COLOR] to drop to tty1 virtual shell.
[/LIST]
I had mistakenly assumed that anyone who read the first step would understand that the procedure would have to be performed without the graphical desktop being available, especially after performing step 3, which instructs the user to stop the gdm service.

Evidently I made a very faulty assumption. In order to mitigate the possibility of surprising people with the unexpected consequences of dropping into a virtual shell, I have placed the following warning above the first step in the tutorial.

[COLOR=Red]_**NOTE:**_ [/COLOR][COLOR=Red]The  commands in the following procedure need to be entered in a virtual  shell. While doing so, the graphical desktop will not be available.  Consequently, if the steps presented below have not been committed to  memory, written down, printed out, displayed on another computer, or are  not available for reference by any other means, they will be impossible  to perform.
[/COLOR]
I'm hoping that will spare people from freaking out when everything on their screen goes black except for the login prompt. If you have any more comments, that would serve to mitigate this problem further, I sure would appreciate the opportunity to read them. I began programming computers way back in the day when there were no terminals and every line of code we wrote was recorded by punching holes in [Fortran cards]("https://secure.wikimedia.org/wikipedia/en/wiki/File:FortranCardPROJ039.agr.jpg"). After so many decades of experience, I find it difficult at times to anticipate every little glitch that may flatten a newbie. Sorry about that. But, I have to tell you, it's damned near impossible for me to put my brain in newbie mode anymore. So, I would be grateful to receive any comments that y'all have that will help me make my suggestions more newbie-friendly.

With regard to your question concerning how the ~/xorg.conf.new file can be edited in the virtual shell:

[COLOR=Black]You will need to use **sudo** in front of commands that manipulate files that were created by root. The owner of the file xorg.conf.new ends up being: **root**, even though it is created in your home (~) directory because it was generated using the command:
```

sudo X -configure

```This command needs root privileges, hence: the **sudo** prefix. Consequently, root ends up owning: ~/xorg.conf.new.

In order to edit ~/xorg.conf.new, you'll need to elevate your user privileges to root by using **sudo** at the beginning of your edit command.[/COLOR] For example:
```

sudo nano ~/xorg.conf.new

```A thousand apologies from me for not making this clear. I'll go back to my tutorial and try to fix it up in this area as well.

Thanks for letting me know of my oversights.

Hope this has helped.

---

### Post by sandyd on 2010-11-12
> **purelife70 said:**
> I have Dual monitor problems with 10.10, like a lot of people it seems.

I cannot get the extended desktop @ 3840X1080, I can only get mirrored.

I am using an ATI gfx card, I tried this below but it did not work for me.

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

Any help would be greatly appreciated.

thx

you using open source drivers or proprety drivers?

---

### Post by nishant.singh28 on 2010-11-12
Use the open source driver. That lets you go for multiple displays.

---

### Post by Crusty Old Fart on 2010-11-14
To scottyab:

After editing my last post several times, I finally quit screwing around and got it to a version that I hope will be genuinely helpful.

I'd appreciate any feedback you may wish to give.

Thanks,

Crusty

By the way, when you're in a virtual shell, and as long as the gdm service is still running, you can instantly return to your graphical desktop by pressing the key combination [COLOR=Blue]**Ctrl+Alt+F7**[/COLOR] (or **[COLOR=Green]Ctrl+Alt+F8[/COLOR]** if you have managed to hang tty7 -- Don't laugh. That's not a joke. I've managed to hang tty7 and have no idea how I did it.  -- Okay, you can laugh at that.).

Ordinarily, there are seven tty processes running. The first six are the virtual shells that are available and can be accessed using **Ctrl+Alt+F1** through **Ctrl+Alt+F6**, and the seventh is used by gdm (**Crtl+Alt+F7**).

Consider this:
```

ps -ef | grep tty

[COLOR=Red]***~~~ output ~~~***[/COLOR]
root       822     1  0 21:55 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       832     1  0 21:55 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       843     1  0 21:55 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       845     1  0 21:55 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       851     1  0 21:55 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1179     1  0 21:55 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      1182   988 15 21:55 tty7     00:00:16 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-FIxElE/database -nolisten tcp vt7
1000      1722  1705  0 21:57 pts/0    00:00:00 grep --color=auto tty

```

---

