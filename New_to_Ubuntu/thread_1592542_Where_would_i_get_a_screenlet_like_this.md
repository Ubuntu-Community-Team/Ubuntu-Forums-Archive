---
title: "Where would i get a screenlet like this?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-10-10
Ive been looking for screenlets like these for ages, ive looked on Gnomelook and found nothing. Has anyone got any other cool screenlets like this i should install? 

cheers :)

---

### Post by Tibuda on 2010-10-10
this is [conky]("apt://conky").

check the conky megathread on the cafe: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

EDIT: check also conky-colors: [http://gnome-look.org/content/show.php/CONKY-colors?content=92328](http://gnome-look.org/content/show.php/CONKY-colors?content=92328)

---

### Post by Rave Gloves on 2010-10-10
ive installed it but i have no idea where it's been installed too, ive checked everywhere :/

---

### Post by Rave Gloves on 2010-10-10
im very very confused how to install this. Ive done all the startup applications stuff now im not quite sure how to install the weather thing. All i want is the weather none of the system monitoring things :P dose conky have an interface or anything?

---

### Post by Rave Gloves on 2010-10-15
Is there a tutorial on how to use this? i got it to give me a system bar at the bottom but i have no idea how to add themes and such to it like how to get the screen shot above D:

---

### Post by Astnya on 2010-10-15
> **Rave Gloves said:**
> im very very confused how to install this. Ive done all the startup applications stuff now im not quite sure how to install the weather thing. All i want is the weather none of the system monitoring things :P dose conky have an interface or anything?
I assume you've installed conky from the repositories. If not:
```
sudo apt-get install conky
```Anyway. All configuration of conky, including its appearance, behavior, and the information it displays, is controlled by the **.conkyrc** file, which should be located in your home folder. (It's hidden, so press Ctrl+H if you can't see it.) 

If you know how, you can edit the .conkyrc file to change various aspects of conky. Additionally, if you just want to use someone else's conky setup, you can download their .conkyrc (which they've hopefully provided, of course) and replace yours with theirs, then restart conky (run 'killall conky' and then 'conky'). Of course, if their .conkyrc uses plugins or functions that your system doesn't support or enable, then those aspects won't work.

You can have a look at some basic conky configurations and what they look like here:[ http://conky.sourceforge.net/screenshots.html]("http://conky.sourceforge.net/screenshots.html")

And as already mentioned, there's a thread in which people share their .conkyrc files: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

If you want help designing something specific, you could look around for a .conkyrc that already contains what you want, or you can join #conky on irc.freenode.net to speak to the helpful people there.

---

### Post by fishbulb1022 on 2010-11-05
Thats not conky, its the wide weather screenlet. [http://www.omgubuntu.co.uk/2009/04/wide-weather-screenlet/]("http://www.omgubuntu.co.uk/2009/04/wide-weather-screenlet/")

---

### Post by trikster_x on 2010-11-06
[http://gnome-look.org/content/show.php/Flat+Clean+Clear+Weather+Theme?content=103510]("http://gnome-look.org/content/show.php/Flat+Clean+Clear+Weather+Theme?content=103510")  
Another option for a minimal graphics approach to a weather screenlet.

---

### Post by karthick87 on 2010-11-06
See the links below to setup conky and view conky examples [here]("http://ca.ubuntuforums.org/showthread.php?t=281865")

[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

[http://ubuntuforums.org/showthread.php?p=6365702](http://ubuntuforums.org/showthread.php?p=6365702)

---

### Post by cracker89 on 2010-11-06
Conky!

---

### Post by yetiman64 on 2010-11-06
> **fishbulb1022 said:**
> Thats not conky, its the wide weather screenlet. [http://www.omgubuntu.co.uk/2009/04/wide-weather-screenlet/](http://www.omgubuntu.co.uk/2009/04/wide-weather-screenlet/)

I'm not using conky here, but have screenlets installed. I found this very useful info and now have a decent weather screenlet. Thank you, I appreciate you posting that link.

---

