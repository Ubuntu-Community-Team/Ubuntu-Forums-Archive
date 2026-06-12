---
title: "iso burner like imgburn or better?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by mrpervie on 2009-12-08
hello everyone im just wondering if anyone knows of any image burning software that will run on ubuntu 9.10...some thing similar to imgburn if your familiar with win apps....somthing capable of burning wii and 360 images ..i can find a few im just not sure wich ones are actually GOOD...thanks, any help is appreciated...i herd kb3 might be ok...but  after readig around some people say no ..i dont know..opinions?

---

### Post by Marvin666 on 2009-12-08
If you can see it in the package manager, then it has to be at least half decent.

---

### Post by mrpervie on 2009-12-08
actually thats good info haha!...sorry im new to ubuntu still learning my way around..im just not willing to waist a lot of DLdvds they are still kind of pricey ..ya know?....well can anyone at least verify they have burned wii isos and or 360 isos  with k3b

---

### Post by mrpervie on 2009-12-08
well  i guess ill just attempt to install imgburn in wine...ill keep an eye out for post if anyone has any suggestions

---

### Post by sandyd on 2009-12-08
nerolinux, braserio, k3b

---

### Post by ramjet_1953 on 2009-12-08
If you want to create your own iso's, [COLOR="Red"]ISO Master[/COLOR] is quite good.

You can install it using Synaptic Package Manager, just search for [COLOR="Blue"]isomaster[/COLOR].

Or just use the command:
```

sudo apt-get install isomaster
```

Regards,
Roger:D

---

### Post by mrpervie on 2009-12-08
thank you both....i was just looking at iso master and k3b. here <http://allmyapps.com/ubuntu-9.10/desktop/video/disc-burning/1>..sure you guys already know about them kind of sites tho...alot of good stuff i seen....i did manage to get imgburn to run on wine...ubuntu is turning out to be  A LOT easier to work with than i imagined!!..although ..id rather have a native application for burning my isos just to keep things simple and get the feel for the linux...so im going to check those out..thanks again..oh and..im sorry i just have to say it....i just found out that ...GOOGLE CHrOME IS ON LINUX WOOO!!!!!! why didnt anyone tell me huh! HUH! huh?...just kidding...im a big fan of chrome...going to  try it now...see ya!!!

---

### Post by sgosnell on 2009-12-08
k3b is a KDE app, brasero is the gnome equivalent.  Both will work fine for burning any disks you want, either .iso or normal CD/DVDs.  I use brasero because I use the gnome desktop, and don't want to have to install a ton of kde libraries just to get one program running.

---

### Post by Temposs on 2009-12-08
Yeah, why aren't you just using the default burning software that comes with Ubuntu? No need to hunt around for software when it's already right there. Go to Applications->Sound & Video->Brasero Disc Burner. It works just fine.

---

### Post by LuisGMarine on 2009-12-08
> **sgosnell said:**
> k3b is a KDE app, brasero is the gnome equivalent.  Both will work fine for burning any disks you want, either .iso or normal CD/DVDs.  I use brasero because I use the gnome desktop, and don't want to have to install a ton of kde libraries just to get one program running.

Agreed, brasero is just right for THE GNOME desktop. :popcorn:

---

### Post by MelDJ on 2009-12-08
gnomebaker. available in the repos

---

### Post by mrpervie on 2009-12-08
thank you!...guess i should have stated im running with gnome..i think you just saved me some hassle....but u guys can stop now..i get it....theres alot of options.haha..thanks again

---

### Post by jeu on 2009-12-27
> **Temposs said:**
> Yeah, why aren't you just using the default burning software that comes with Ubuntu? No need to hunt around for software when it's already right there. Go to Applications->Sound & Video->Brasero Disc Burner. It works just fine.

Biggest reason I use IMGBurn; Verify.

Pretty standard in most Windows based burners. In IMGBurn, one tick.

None the hailed Ubuntu application has this feature.

---

### Post by Temposs on 2009-12-27
> **jeu said:**
> Biggest reason I use IMGBurn; Verify.

Pretty standard in most Windows based burners. In IMGBurn, one tick.

None the hailed Ubuntu application has this feature.

umm, I'm sorry, but you're wrong. 

If you go to Tools->Check Integrity in Brasero, you can "Verify" any disc you'd like. 

And if you go to Edit->Plugins, you can do "one tick" and Brasero will automatically check the integrity of the individual files or the entire disc(or both) once a burn is completed.

---

### Post by jeu on 2009-12-27
> **Temposs said:**
> umm, I'm sorry, but you're wrong. 

If you go to Tools->Check Integrity in Brasero, you can "Verify" any disc you'd like. 

And if you go to Edit->Plugins, you can do "one tick" and Brasero will automatically check the integrity of the individual files or the entire disc(or both) once a burn is completed.

Indeed you are correct, those options are there. Thanks! 

Interesting that it use "checksums" to verify.

ImgBurn simply (and reliably) do a byte comparison after open/close cycle of drive.

Why would Brasero use "checksum", I'm curious?

---

### Post by sgosnell on 2009-12-27
Checksum is the standard accepted way to check the integrity of a file or disk, without having to take the time to go byte by byte, which can take a very long time.  It gives the same result, but much more efficiently.

---

### Post by Methuselah on 2009-12-27
Yeah, the chance of a random write error producing the same checksum as the original file is very very small indeed.
K3b is a really nice image burner as well and has a verify option too.

K3b is a KDE application but there is nothing stopping you from using it in gnome.
It will introduce the Qt library but if you are using skype and a number of other applications chances are good you already have them.

So see if you like Brasero and if you neeed something else check out K3b.
There's Nero for linux as well but who'd use that :p.

---

### Post by jeu on 2009-12-27
> **sgosnell said:**
> Checksum is the standard accepted way to check the integrity of a file or disk, without having to take the time to go byte by byte, which can take a very long time.  It gives the same result, but much more efficiently.

I don't really know much about this stuff so pardon the questions. In order to create the checksum, does the program not read every single byte anyway in order to create the checksum?

---

### Post by sgosnell on 2009-12-29
[http://en.wikipedia.org/wiki/MD5](http://en.wikipedia.org/wiki/MD5)

---

