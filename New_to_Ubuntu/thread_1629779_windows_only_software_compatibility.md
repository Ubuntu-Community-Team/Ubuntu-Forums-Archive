---
title: "windows only software compatibility"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by philosophers-stone on 2010-11-24
I am using ubuntu for over two months.To be honest I love ubuntu over windows.;)
I don't like to restart back to windows to run autocad or play any games.It's annoying you know...#-oI tried to use virtual xp by virtual box ,qemu,and vmware..But nothing worked that fine for me when trying to play game like nfs most wanted and so on. Autocad works but not that far i expect..Wine installs most wanted,when trying to play i get a black screen and only sound!!](*,)
You guys at this community are realy great! Everything quest is answered by someone.Could you guys make the windows software compatibility better!!!!!!! That would end my journey with windows.


[COLOR=Blue]**Anybody having a good solution to run these windows only apps,Please!please!please! help me.........**[/COLOR]

My system specifications
Intel core2duo E7500(with intel VT)
320GB hard disk 2GB ddr3 ram
Gigabyte motherboard with intel G41 chipset
OS= Ubuntu Maverick Meerkat

---

### Post by Spice Weasel on 2010-11-24
Try Wine:

[http://www.winehq.org/](http://www.winehq.org/)

In a terminal -

sudo apt-get install wine

---

### Post by shoo_ash on 2010-11-24
Yeah,
and you might want to check Wine Applications database [http://appdb.winehq.org/](http://appdb.winehq.org/)
There is a lot of information concerning software that does or does not run under wine (as well as instructions how to run apps that don't work "out of the box").

---

### Post by Yougo on 2010-11-24
AutoCAD is a VERY complex mountain of software and an absolute nightmare to ever get working half-decent with wine. i believe they got an old version kind-of-running on wine. check [http://appdb.winehq.org/](http://appdb.winehq.org/) for what runs and how well it runs with wine

Games are tough. if they rely on Directx, rather than OpenGL, you'll have a hard time running it decently outside of windows.

a virtual machine running windows could be a solution, but you need quite a bit of RAM and a recent CPU, since you'll be running Ubuntu+Windows+Autocad.  
most games need hardware graphics accelleration, which virtual machines don't really offer (if they do, please tell me, VirtalBox says it can, but doesn't play nice)
so you'd still be stuck with low graphics.

there has been talk about Autodesk making a Linux version of AutoCAD, since they made one for OSX, and there are some projects to make a autocad-lookalike for linux from scratch, but don't hold your breath...

---

### Post by Zzl1xndd on 2010-11-24
As other have suggested WINE (or one of its derivatives) is about the only way to go. 

Crossover, a commercial WINE derivative, is really rather good.

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Also I say it a lot, but I find it always works out better if you can find a Linux alternative. 

CAD isn't something I know a lot about, but I know some companies have Linux versions.

[http://www.cad-schroer.com/Software/MEDUSA4/M4Personal/](http://www.cad-schroer.com/Software/MEDUSA4/M4Personal/)

---

### Post by philosophers-stone on 2010-11-25
Thanks a lot to all of you guys for quick reply...
I am trying games on virtual box but for me games requiring direct 3d does not start...Don't know why though..#-o
wine can only run little softwares on my machine....:|
I could not install any programme not listed on cross over ...maybe i have not done all things correctly....:confused:
[COLOR=Indigo]Any way to get around with this.......................[/COLOR]:popcorn:

---

### Post by mastablasta on 2010-11-25
windows games and especially new ones that are based on directx will mostly run only in windows. linux lack native clients for games.
 
not everyhitng will be able to be installed in linux. Only some work, while some work only partially (lower graphics, slower...).

---

### Post by Tekno.Statik on 2010-11-25
Yeah, I had to drop a few of my favorites on Windows myself, but the sacrifice came to be quite enjoyable xD

And I just remembered that I still have Windows XP on my other hard drive, I just haven't used it in a long time. lol

---

### Post by philosophers-stone on 2010-11-25
> **mastablasta said:**
> windows games and especially new ones that are based on directx will mostly run only in windows. linux lack native clients for games.
 
not everyhitng will be able to be installed in linux. Only some work, while some work only partially (lower graphics, slower...).
 
Will that ever be possible to run thes directx apps???

---

### Post by mastablasta on 2010-11-25
> **philosophers-stone said:**
> Will that ever be possible to run thes directx apps???
 
directX is made by microsoft. it is therefore unlikely they will give out the code.
 
as already mentione i think directX9 can be installed but games using it might run quite slow. or not, depends.... as i understand to get anything working in linux there is much reverse engineering invoved or finding some other solutions. maybe one day directx11 will be available in linux as well, but by the time it is MS will porbably already have DirectX15 :-D

---

### Post by philosophers-stone on 2010-11-25
Guys !
Do i need any extra graphics card to play games in wine?
I can not play even those mentioned platinum games in wine database.
Only some software runs in my machine.
By the way I have built in G41 express chipset.....Can i do with it?

Thanks in advance for reply!:popcorn:

---

