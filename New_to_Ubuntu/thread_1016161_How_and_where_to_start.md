---
title: "How and where to start?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Aksha on 2008-12-19
Ok basically i have been wanting to try Ubuntu for a long time but i have never found out how to partition so i can run windows xp or Ubuntu and switch between them. If someone could give me pointers on how to start doing this(partitioning and installing ubuntu without a cd) that would be greatly appreciated.

Thanks,
Justin Black

---

### Post by SuperSonic4 on 2008-12-19
The live CD is best

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

explains it all the way through :]

---

### Post by ATL™ on 2008-12-19
I suggest trying out [Wubi]("http://wubi-installer.org"). It will allow you to install Ubuntu (along with other flavors) as a "Windows program" which will add the distribution to your Add/Remove list in Windows like it was an actual application you installed.

---

### Post by Aksha on 2008-12-19
> **ATL&#8482 said:**
> I suggest trying out [Wubi]("http://wubi-installer.org"). It will allow you to install Ubuntu (along with other flavors) as a "Windows program" which will add the distribution to your Add/Remove list in Windows like it was an actual application you installed.

It will still function normally this way? Is this install simple and effective? Will it do all the partitioning for me? Sorry so many questions.

---

### Post by Michael.Godawski on 2008-12-19
There are some minor glitches with Wubi, but nevertheless it is a great option to test Ubuntu.

Make sure you have a back-up of your important data. Playing around with new operating system can be fun and an exciting experience, but also very frustrating when you loose your files.

So safe yourself a lot of trouble. I do not say Ubuntu is scary and will destroy everything it touches.:p But it is wise to be prepared.

The guide posted above is good.

If you have any questions concerning installation, partitions, or anything else, feel free to ask. We are here to help.

---

### Post by Aksha on 2008-12-19
i have already tested it at a friends house, i want to use it for good. Will Wubi not give me the full deal? (Only keeping xp so my family doesn't get mad). I have backed up my files to external harddrive and spare flash drives. Only problem is i have no way to burn the disk and little partitioning knowledge.

---

### Post by jmszr on 2008-12-19
Aksha,
       If you want to dual boot without a CD you will need to install Wubi. True dual booting can be done in the future. This guide can can help you: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) -- look under: Installing a dual boot without partitioning.

---

### Post by Aksha on 2008-12-19
so wubi is not true dual booting? So i use it maybe until they send me the cd?

---

### Post by EnGorDiaz on 2008-12-19
installing under a guided partition is the best way it doesnt take up the harddrive and you have grub a fully functionaly good bootlaoder which you can configure easily later on

---

### Post by SuperSonic4 on 2008-12-19
I don't think you can install wubi before they send the CD out.

---

### Post by Aksha on 2008-12-19
> **SuperSonic4 said:**
> I don't think you can install wubi before they send the CD out.

[http://wubi-installer.org/](http://wubi-installer.org/)

Does this not work?

---

### Post by Michael.Godawski on 2008-12-19
Wubi creates a virtual operating system.
Real dual-booting installs two or more operating systems to the harddrive.

> a dual-boot allows you to choose at boot-up whether you would like to use one operating system or another).> Wubi allows you to install Ubuntu as a dual-boot by installing it as a huge file inside of Windows and then modifying the Windows boot loader to add an entry for Ubuntu. 
The nice thing about this approach from a Windows-user standpoint is that there is no risk of accidentally deleting your entire drive, you don't have to know anything about partitions, and you can easily remove Ubuntu from the dual-boot if you want to go back to a strictly Windows-only system. 
taken from psychocat's site

[> ]("http://wubi-installer.org/")[http://wubi-installer.org/](http://wubi-installer.org/)

Does this not work?

worth a try
 did not know the site, learning whole the time...

---

### Post by bodhi.zazen on 2008-12-19
See here : 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)


And this link :

[uhelp]community/Installation[/uhelp]

On the second link there is a section on no CD ...

---

### Post by Aksha on 2008-12-19
ok so with wubi will everything on the os still function properly? programs etc

---

### Post by SuperSonic4 on 2008-12-19
> **Michael.Godawski said:**
> 

[URL="http://wubi-installer.org/"]

worth a try
 did not know the site, learning whole the time...

Seconded, give it a go :]

---

### Post by jmszr on 2008-12-19
Aksha,
       Absolutely use it until you get a cd,it is as close to true dual booting as you'll get. I used Wubi for 5 months until I went Ubuntu only. Here is another guide that will help: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Also, you can download and burn the cd. This might help: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Michael.Godawski on 2008-12-19
> ok so with wubi will everything on the os still function properly? programs etc 	

Yes. If something goes wrong you can delete Wubi/Ubuntu like a "normal" windows application using the add/remove app.

If everything goes according to the plan, and it is very likely that it will; 
like 99.98 % sure :p

---

### Post by Aksha on 2008-12-19
so is there a way to install besides installing it as a windows program, without a cd? im reading this [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) and i don't really understand what to do, is this better then using wubi?

---

### Post by Michael.Godawski on 2008-12-19
wubi is definitely easier and more user friendly than this geek-language guide ):P
(which is cool later:p, when you have some experience)

---

### Post by Aksha on 2008-12-19
thanks for the help everyone, i think i will use wubi until i receive the install cd in the mail :) that way i wont have to worry about not having a cd and trying to install it with these weird ways. (I could figure out the other ways(i'm not a noob with computers) but i guess i'll wait and take my time

---

### Post by Aksha on 2008-12-19
would anyone suggest getting rid of xp and using only ubuntu or not?

---

### Post by Michael.Godawski on 2008-12-19
What do you suspect will be the answer on the **ubuntuforums**. :p

Now without joking...
Start with dual-booting.
Gain experience, you should feel secure on your new Ubuntu system. 

Linux is not Windows. There are some differences, both in the way of thinking and acting.

Do not rush things. Take your time....

---

### Post by Aksha on 2008-12-19
ok different problem now and good news. I have found a cd that can hold 700 mb! now how to start?

---

### Post by ATL™ on 2008-12-19
> **Aksha said:**
> would anyone suggest getting rid of xp and using only ubuntu or not?

It depends on what you use Windows for. If you're a "gamer" (gamer in the sense of heavy 3D games such as Counter-Strike: Source, Team Fortress 2, any heavy 3D game that's developed for Windows only) then it's something you have to weigh the pro's and con's for. A con being there's no native Linux support for the games mentioned. A pro being that it's definitely possible with the help of Windows API emulators.

Me personally, I play the mentioned games above. The only reason I keep Windows installed is because of the lack of native Linux support.

Also, anything you can do and/or run in Windows, there's usually an open-source Linux alternative. An example for applications is [here]("http://www.linuxalt.com/").

Other than that, it's really just up to you. If you think you're ready to blow off Windows and dive into the Linux world and learn new things, then I'd say go for it. If not, you might want to keep a copy of Windows installed.

---

### Post by jmszr on 2008-12-19
Aksha,
        These two should get you going: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  and [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso) Try the psychocats first but read them both and you'll have a good grasp on what you need to do.

---

### Post by Michael.Godawski on 2008-12-19
I add also my link :p

[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

but the reference is psychocat's site.

---

### Post by donkyhotay on 2008-12-19
When I started linux I completely wiped my windows (mostly because I had no choice) and it was very rough first month. Not something I recommend doing unless you are only planning on testing/experimenting/breaking/fixing your system alot. If people have a choice I recommend dual-booting so that if something goes wrong you can temporarily go back to windows to get your work done until you're ready to tackle linux again. Spend enough time with it and you'll become just as comfortable (if not more so) with it then with windows, thats the time to start thinking about reformatting everything and dumping windows but not before then.

---

### Post by Aksha on 2008-12-19
time to do the install thanks everyone :)

---

### Post by Michael.Godawski on 2008-12-19
You are welcome.
And please report back if the installation was successful. :p

---

### Post by I-75 on 2008-12-19
My personal belief is that the easiest and fool proof way is to get another hard drive or two. Swap out hard drives and install Ubuntu (or some other Linux OS) on it. 

This way you get to test out the Linux distro and if it works out or didn't work out to your expectations ...nothing was lost, except maybe some time. If it didn't work out, just swap out the hard drive again and go back to your original OS.

This is not very expensive project either, all you need is as little as a 10 GB hard drive for testing purposes and 10 GB hard drives can be found on E-bay for as little as $5 or $6 each. 160 GB hard drives can often be found for under $75 at Micro Center and elsewhere. Mark each hard drive with a black marker with the name of the OS.

Purchase a bunch of 10 or 20 GB hard drives and try out Ubuntu, Open Suse, Knoppix 5.3, Mandriva on each. Whatever the case, enjoy experimenting and Linux.

---

### Post by Aksha on 2008-12-20
> **Michael.Godawski said:**
> You are welcome.
And please report back if the installation was successful. :p

i used wubi actually and its running smooth but i wish it was partitioned, i'm getting some new cd's tomorrow because i burned it wrong on a cd-r(my last cd). The Os is running fine.

---

