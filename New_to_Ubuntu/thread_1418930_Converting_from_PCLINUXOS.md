---
title: "Converting from PCLINUXOS"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by notwatson on 2010-03-01
Hi everybody.

I used an Ubuntu live CD at the weekend to rescue a friend's Windows XP PC - we copied all essential data off using the Live CD - it was very smooth.

I have been using PCLINUXOS for 3 years now (currently running KDE 3.6), but am now looking to convert to Ubuntu.

I have a couple of questions first though...(3 actually !)

First question (most important one):
I use Thunderbird for my email and Firefox for my browsing.
If I convert to Ubuntu, can I copy my Thunderbird and Firefox identities to a DVD-R and simply copy them onto my new freshly installed Ubuntu system ?

The reason I ask this is that I want to retain all of my email folders and my settings for browsing.

Second question:
Sometimes I create DVDs using devede - is this available under Ubuntu ?
Also, I imagine that CUPS is supported ? (I print to an HP Laserjet 400 using CUPS at the moment).

Last question:
Is there anything else that I should do or know or be asking before I take the (what I hope will be a rather pleasant) plunge ?

I hope to become a new Ubuntu user in the next couple of days/weeks....

Thanks in advance.

Jon

---

### Post by halitech on 2010-03-01
I'm not 100% sure on the thunderbird/firefox question but I don't see why it wouldn't work. I've done it on windows so it should work fine in Ubuntu.

Devede is certainly supported and in the repos for easy installation

Yes, CUPS is supported as well.

Welcome to the forum and Ubuntu :)

---

### Post by mastablasta on 2010-03-01
> **notwatson said:**
> 
First question (most important one):
I use Thunderbird for my email and Firefox for my browsing.
If I convert to Ubuntu, can I copy my Thunderbird and Firefox identities to a DVD-R and simply copy them onto my new freshly installed Ubuntu system ?
Jon
 
TEBE and FEBE add onns could be what you are looking for since the great Mozbackup only works in Win.
 
[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)
 
Also you could just move the profile i think...

---

### Post by clive littlewood on 2010-03-01
Hi

Welcome to Ubuntuland !!

Your firefox and thunderbird bookmarks and saved files can be saved across to Ubuntu.The files will be something like .mozilla and will be hidden in the home directory. To show just select "show hidden files" in your file manager.

Printing with HP is fine in Ubuntu and it even has an HP manager to check ink levels etc.

Devede is in the Ubuntu repos.

Hope this helps

Clive

---

### Post by mastablasta on 2010-03-01
> **clive littlewood said:**
> Hi
 
Your firefox and thunderbird bookmarks and saved files can be saved across to Ubuntu.The files will be something like .mozilla and will be hidden in the home directory. To show just select "show hidden files" in your file manager.
 

 
and here is more on this:
How To Manage Profiles
[http://www.mozilla.org/support/thunderbird/profile#backup](http://www.mozilla.org/support/thunderbird/profile#backup)
 
Same goes for Firefox only then the folder is a bit different.

---

### Post by notwatson on 2010-03-01
Many thanks - those answers are really useful and have set my mind at ease.

Would you recommend Kubuntu (as I am used to KDE) or straight Ubuntu - what's the consensus ?

I have to admit that I am really quite looking forward to this !

Jon

---

### Post by halitech on 2010-03-01
Personally I prefer XFCE but try what you are used to. If KDE runs okay on  your system with PCLINUX then why change?

---

### Post by clive littlewood on 2010-03-01
Hi

I'm a gnome man myself (actually over 6')

Seriously this is the beauty of linux, try them all and decide or you can have both KDE and Gnome choosing at login.

Clive

---

### Post by notwatson on 2010-03-01
good answer Halitech !

I think I may try KDE....

Clive - how interesting - how do you do that ? (gnome and KDE choosing at login...)

Thanks,

Jon

---

### Post by clive littlewood on 2010-03-01
Hi

Check out this link   [www.psychocats.net/ubuntu/kde]("www.psychocats.net/ubuntu/kde")

Clive

---

### Post by baddnady23 on 2010-03-01
> **notwatson said:**
> good answer Halitech !

I think I may try KDE....

Clive - how interesting - how do you do that ? (gnome and KDE choosing at login...)

Thanks,

Jon

Just be advised you will get a little software bloat, but hey the more the merrier!

I would suggest taking an hour of so and really reading through the [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index") website that clive littlewood mentioned.  It's a wonderful resource if your just starting to get your feet wet in linux, especially ubuntu.  Even if you already have an understanding of linux, it's still great.  Enjoy and welcome!

Feel free to ask whatever questions you have on these forums, there are great people here to help and they have no let me down yet.

---

### Post by mkvnmtr on 2010-03-01
I have used and like both. The difference I see is the deb packaging seems to nallow me to add more programs from outside the repositories thus I use some form of Ubuntu mostly. The switch between the two is very easy.

---

### Post by frito on 2010-03-01
You also might want to look at Linux MINT a lot of people like that too.

> Clive - how interesting - how do you do that ? (gnome and KDE choosing at login...)
You can do this in PCLinuxOS too, just install 'Gnome' (i think thats the name) from the repo.
It gives you a choice of which environment to use at login, ubuntu does the same.

Also Im curious as to why you're switching.

Nothing should be that different between Ubuntu and any other type of linux when it comes to things like selecting Desktop environments, Ubuntu is just packaged in a way a lot of people like... (basically buts its also Debain and stuff) 
Im just trying to say its the same thing underneath.

When I look at distros I basically look at: 
release cycles (Ubuntu is every 6 months, PCLOS is whenever they think there is a big enough change to make a big difference)
Distro goals (Ubuntu and PCLOS aim at simplicity, Arch aims at ultimate power over your comp :P)
Nice default stuff (Ubuntu has Ubuntu One neato, others have firewalls and codecs and things)

---

### Post by Lord Stig on 2010-03-01
> **frito said:**
> You can do this in PCLinuxOS too, just install 'Gnome' (i think thats the name) from the repo.
If gives you a choice of which environment to use at login, ubuntu does the same.

Also Im curious as to why you're switching.

Nothing should be that different between Ubuntu and any other type of linux when it comes to things like selecting Desktop environments, Ubuntu is just packaged in a way a lot of people like... (basically buts its also Debain and stuff) 
Im just trying to say its the same thing underneath.

What worked for me, to get GNOME, was ```
sudo apt-get install ubuntu-desktop
```

EDIT: ah, but that wasn't from PC Linux OS though. Oh well, worth a try

---

### Post by natravis on 2010-03-01
> **notwatson said:**
> Clive - how interesting - how do you do that ? (gnome and KDE choosing at login...)

After you install the various desktop managers (XFCE, gnome, KDE, LXDE, etc), when you boot ubuntu to the splash screen, there will be a drop down box on the bottom that allows you to choose which you would like to boot into. I prefer Gnome, but that may be inertia (if it aint broke ...). Try them all then remove what you dont need later.

---

### Post by nothingspecial on 2010-03-01
You don`t need to install the whole of Ubuntu to try gnome
```

sudo apt-get install gnome-core gdm network-manager-gnome 
human-theme tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils
```

---

### Post by notwatson on 2010-03-03
At the moment I have one HDD (on a single plug IDE cable) and two DVD drives on the other IDE channel (both on one cable [slave/master]).  The HDD is set to master and contains PCLINUXOS.

I have got another hard disk and a twin plug IDE cable.

So, I want to replace the single IDE cable with the double - install the new hard disk and install Ubuntu on the new hard disk. This, I plan to be a temporary measure, as I want to check that my Thunderbird 2 and Firefox profiles work with Thunderbird 3 and Firefox in Ubuntu.  Once I have established this to be the case and had a play for a few days, I'll simply install Ubuntu to the present master (which is larger anyway).

So - here's my question...

If I leave the present master disk as master, set the new hard disk to slave and boot up from the Ubuntu live CD, can I install Ubuntu onto this new hard disk without touching the other hard disk - or will I need to change the master/slave settings around ?  (at the moment, the master has two partitions, system and swap).  If there is something else I should do, please let me know...

I know this seems like a lot of hand-holding, but I just really want to make sure....

I am very keen to get this up and running !

Thanks in advance for any help.

Jon

---

### Post by notwatson on 2010-03-04
> **frito said:**
> You also might want to look at Linux MINT a lot of people like that too.


You can do this in PCLinuxOS too, just install 'Gnome' (i think thats the name) from the repo.
It gives you a choice of which environment to use at login, ubuntu does the same.

Also Im curious as to why you're switching.

Nothing should be that different between Ubuntu and any other type of linux when it comes to things like selecting Desktop environments, Ubuntu is just packaged in a way a lot of people like... (basically buts its also Debain and stuff) 
Im just trying to say its the same thing underneath.

When I look at distros I basically look at: 
release cycles (Ubuntu is every 6 months, PCLOS is whenever they think there is a big enough change to make a big difference)
Distro goals (Ubuntu and PCLOS aim at simplicity, Arch aims at ultimate power over your comp :P)
Nice default stuff (Ubuntu has Ubuntu One neato, others have firewalls and codecs and things)

In answer to that very good question, Frito, I am thinking of changing because I have been using the same distribution since 2007 and I have neglected to update it  (because it has been working so well) and now the repository has so many new packages that it is (apparently) quite unlikely that marking all upgrades will be successful.  Also, the release cycle seems a bit slow for me and KDE 4 is slow to be supported.   Firefox3 was so unstable that I turned back to firefox 2 and now I get messages from sites like Youtube that my browser will not be supported for much longer.

One big difference that I really like is the size of the community (don't get me wrong - over on PCLINUXOS forums, the people are brilliant) and the ease of updating the system,

Finally - I want a change - Ubuntu seems extraordinarily well polished to me - I quite fancy a bit of that !!!

Just waiting for a break in my working day to install the new hard disk and plunge in !

Jon

---

