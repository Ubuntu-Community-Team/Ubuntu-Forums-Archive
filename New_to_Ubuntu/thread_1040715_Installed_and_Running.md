---
title: "Installed and Running"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-01-15
I got my CD in the mail today, I have it installed, and all is well almost. I am very happy with this product so far I love it... My problem is it runs sluggish and takes a really long time to download stuff. I am wondering if it is something I might have did during installation, or something I didn't do?

I was running Win Xp till today, I have a 80 gig HD, 2.4 GHz Intel pentium processor, and 256 mb RAM...Even with the sluggishness and slow downloads I am totaly Thrilled, Happy, and Excited... I Love UBUNTU!!!

Just wondering if there is anything I can do to help correct this problem...Thanx in advance for any and all assistance. I am sure I will be back, for I am totaly new to all this Linux stuff...

Your Friend,

Leo

P.S. I am getting allot of double typed letters here...What may be the cause of that?

---

### Post by vegetarianshrimp on 2009-01-15
About your last question, try going to System >Preferences > Keyboard and moving Delay more towards long.

About the sluggishness.
You said it was slow at downloading stuff, right? Well, are you downloading programs from the Internet like you would in windows XP? For a beginner in Ubuntu, you should probably go to Application > Add/Remove and, when you are more familiar with Ubuntu and GNU/Linux, System > Administration > Synaptic Package Manager.
But, maybe you are already doing that. In that case, I don't really know!

---

### Post by Leo Dragonheart on 2009-01-15
I will check out the keyboard thing, and I got the files to download to where I want but they just take forever to download... as for the add and remove thing, I don't even know where that is...I found the add and remove thing thanx, I will use it. Thank you for the info...

---

### Post by vegetarianshrimp on 2009-01-15
I'm glad I could help. Tell me whether the keyboard thing works.

About the Add/Remove, I STRONGLY recommend using that. PLEASE don't download from the Internet. 
It is in the **Applications **menu, near the bottom.

---

### Post by Leo Dragonheart on 2009-01-15
Yes the keyboard thing did work...Why do you say don't download from internet? How do I get stuff from online...?

---

### Post by vegetarianshrimp on 2009-01-15
Great! Glad I could help
before I explain about the Add/Remove thing, I want to say that I am a beginner-ish myself and that I might be wrong about this.
1. The applications are from the official ubuntu repository (unless you add another one), so you can make sure the applications you are downloading don't have viruses, and most of them have official support.
2. Add/Remove is much easier and faster. (you don't have to go looking for .deb files or go through a series of commands in the Terminal that you don't understand when you try to install tarballs or bin files.

---

### Post by Vantrax on 2009-01-15
For the double keys try going system > preferences > keyboard and making the delay a little longer. That should help a bit.

Gnome (the desktop manager) takes a fair bit of computing power. So it might just be your a little on the slow side for it, but we can see about that.

To install applications start by using the Add/Remove programs in your applications menu, thats the easy way.

There are also two other methods, one using Synaptic Package manager, the other using the terminal.

All of these methods are preferable to downloading something from a website so check if there is something in the repository first. (If you dont know what a repository is click [here]("http://www.matthewlye.com/index.php/component/content/article/34-ubuntu-ed/59-ubuntu-repositories-and-additional-repositories"))

Applications can be installed from the terminal like this:

sudo apt-get install ubuntu-restricted-extras

Sudo means super user do, or in simple words install as administrator
apt-get is a program that manages packages
install is a modifier to say you want to install (can also remove this way)
ubuntu-restricted-extras is the package you want to install (in this case a handy package with all sorts of goodies in it like video codecs, java, and ms fonts)

---

### Post by 73ckn797 on 2009-01-15
> **Leo Dragonheart said:**
> I got my CD in the mail today, I have it installed, and all is well almost. I am very happy with this product so far I love it... My problem is it runs sluggish and takes a really long time to download stuff. I am wondering if it is something I might have did during installation, or something I didn't do?

I was running Win Xp till today, I have a 80 gig HD, 2.4 GHz Intel pentium processor, and 256 mb RAM...Even with the sluggishness and slow downloads I am totaly Thrilled, Happy, and Excited... I Love UBUNTU!!!

Just wondering if there is anything I can do to help correct this problem...Thanx in advance for any and all assistance. I am sure I will be back, for I am totaly new to all this Linux stuff...

Your Friend,

Leo

P.S. I am getting allot of double typed letters here...What may be the cause of that?


Add/Remove will be your best bet for programs.

256Mb ram may be your reason for slow. Recommend at least 512 but better 1Gib memory.

What type Internet connection do you have?

---

### Post by abn91c on 2009-01-15
anything else you looking for like Eye candy, themes, icons etc.. get from here [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by albinootje on 2009-01-15
> **Leo Dragonheart said:**
> 
I was running Win Xp till today, I have a 80 gig HD, 2.4 GHz Intel pentium processor, and 256 mb RAM...Even with the sluggishness and slow downloads I am totaly Thrilled, Happy, and Excited... I Love UBUNTU!!!

Cool! :)

256 Mb RAM is not that much, 512 Mb would be much nicer, but.. it depends on which programs you run.

OpenOffice can take long to load, but you can tweak it :
[http://lifehacker.com/software/optimization/speed-up-openoffice-270775.php](http://lifehacker.com/software/optimization/speed-up-openoffice-270775.php)

The Ubuntu desktop itself is a bit sluggish. 
Try some other themes or customize your theme.

Try alternative browsers : midori, galeon, epiphany-browser. konqueror.
Try alternative file managers : thunar, pcmanfm

Try Xubuntu from your installation :
[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by Leo Dragonheart on 2009-01-15
OK Thanx for all the help...I may have solved the sluggish problem and in turn made another question. I had like 10 browser windows opened at once... How is that and how can I check to see if they are closed when I close them...?


Thank you all for all your help...:-)

---

### Post by Leo Dragonheart on 2009-01-15
I don't see a thanx medal but yes you helped and Thanx...

---

### Post by albinootje on 2009-01-15
> **Leo Dragonheart said:**
> OK Thanx for all the help...I may have solved the sluggish problem and in turn made another question. I had like 10 browser windows opened at once... How is that and how can I check to see if they are closed when I close them...?


You can open the System Monitor 
-> System -> Administration -> System Monitor
Then go to Processes, and sort the order for Memory.
There can watch, and shut down programs if needed.
But normally when you shut down all your firefox instances, they should be .. off. :)

---

### Post by Leo Dragonheart on 2009-01-15
Two last things for the day... I need to know where the thanx medal is and it won't let me mark the tread as solved...what am I doing wrong? it lets me subscibe and everthing else just not mark it as solved...

---

### Post by albinootje on 2009-01-16
> **Leo Dragonheart said:**
> Two last things for the day... I need to know where the thanx medal is and it won't let me mark the tread as solved...what am I doing wrong? it lets me subscibe and everthing else just not mark it as solved...

The thanks and solved options were removed for the time being in order to find out more about the instability of the forum software.
They might be back after some time.

---

### Post by Leo Dragonheart on 2009-01-16
OK Thanx, now I can stop looking for them...:-p

---

### Post by 73ckn797 on 2009-01-16
> **Leo Dragonheart said:**
> OK Thanx for all the help...I may have solved the sluggish problem and in turn made another question. I had like 10 browser windows opened at once... How is that and how can I check to see if they are closed when I close them...?


Thank you all for all your help...:-)


If using Firefox you may need to designate new pages be opened in a new tab and not a new window. See attached screenshot.

---

