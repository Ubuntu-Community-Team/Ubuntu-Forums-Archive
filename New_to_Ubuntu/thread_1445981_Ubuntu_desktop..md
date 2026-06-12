---
title: "Ubuntu desktop."
date: 2010-04-03
forum: New to Ubuntu
---

### Post by sinhanikhil.5 on 2010-04-03
I have seen so many features of Ubuntu desktop, all those 3d effects, windows tilting and many more in Youtube and other websites.

But i can't even apt-get install 3ddesktop coz it gives me error that 

cannot find package 3ddeasktop, forget bout other features.

please help.
feedback sincerely welcomed.



[COLOR=White].[/COLOR]

---

### Post by buddyd16 on 2010-04-03
I recommend you read through the folowing thread:
[http://ubuntuforums.org/showthread.php?t=809695]("http://ubuntuforums.org/showthread.php?t=809695")

---

### Post by heepie on 2010-04-03
First make sure you have the right drivers for it

System > Administration > Hardware drivers

Run the wizard and make sure you have the latest drivers for you graphic card.

Then go to:

System > Preferences > Appearance

Go to the last tab that says visual effects and try the normal or extra option. You may like to also intall CompizConfig Setting Manager from the repos..

Hope this helps

---

### Post by coffeecat on 2010-04-03
> **sinhanikhil.5 said:**
> But i can't even apt-get install 3ddesktop coz it gives me error[COLOR=White].[/COLOR]

The previous posters have answered your question about compiz, so I'll limit myself to one comment. You can't simply 'apt-get install' something you've thought up. The package name must be something the package manager knows about from the package metadata that a 'sudo apt-get update' downloads. So, 'sudo apt-get install gthumb' will work (for example), but 'sudo apt-get install OneMillionDollars' won't. Unfortunately. :wink:

Where did you get 'apt-get install 3ddesktop' from? A howto? :?

---

### Post by howefield on 2010-04-03
> **coffeecat said:**
> so I'll limit myself to one comment. You can't simply 'apt-get install' something you've thought up.

Probably unlikely, but the poster could be referring to...  

[http://packages.ubuntu.com/dapper/utils/3ddesktop](http://packages.ubuntu.com/dapper/utils/3ddesktop)

---

### Post by sinhanikhil.5 on 2010-04-03
i am so so So glad for ur so valuable feedkack, and guess wot i lacked compiz config manager, i installed it and got a new playground for myself:) now i have every thing sphere deformation , desktop cube, magic lamp burn;) n many many more...hahahaha(LOL)
thanx a lot to all.



[COLOR=White].[/COLOR]

---

