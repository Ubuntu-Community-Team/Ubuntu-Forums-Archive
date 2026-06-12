---
title: "Java/flash problems"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by dsg158 on 2009-05-13
I started using ubuntu about a month ago..i started on intrepid and then upgraded to jaunty. after installing jaunty, my java/flash started acting up. Example below:


[IMG]http://i267.photobucket.com/albums/ii286/dsgreenly/flash.png?t=1242238472[/IMG]

i did the whole install the lastest flash thing and the restricted drivers thing..but this still shows up for ads on a page, youtube videos, and flash games. If i click on the youtube videos, the real video shows up but its really choppy. if i do the same for the flash games then it turns white and doesnt load or play. is there anything i can do?

thansk

---

### Post by XCan on 2009-05-13
Which flash/java are you using? Are you running 32bit or 64bit?

Although alternatives are plenty, personally, I find that the "sun-java6-plugin" and adobe's flash plugin works best.

---

### Post by Johan Karl Johansen on 2009-05-13
i had some problems because i had both suns java and openJDK java installed at the same time.

---

### Post by AZinOH on 2009-05-13
> **dsg158 said:**
> I started using ubuntu about a month ago..i started on intrepid and then upgraded to jaunty. after installing jaunty, my java/flash started acting up. Example below:


[IMG]http://i267.photobucket.com/albums/ii286/dsgreenly/flash.png?t=1242238472[/IMG]

i did the whole install the lastest flash thing and the restricted drivers thing..but this still shows up for ads on a page, youtube videos, and flash games. If i click on the youtube videos, the real video shows up but its really choppy. if i do the same for the flash games then it turns white and doesnt load or play. is there anything i can do?
thansk

Since you didn't mention how you "did the whole install lastest flash thing", I will tell you what worked for me.  I uninstalled what I had, and downloaded the .deb from the Adobe site and installed that. In doing so, I got a message that I needed a certain MPEG-4 codec. After installing that, it works okay so far.

---

### Post by dsg158 on 2009-05-13
I'm using the 32bit version.

And when it comes to uninstalling everything...does it mean just that? Just uninstall every java thing i have?

what would be the best thing to install then for youtube and flash games.

---

### Post by XCan on 2009-05-13
In firefox, take a look at Tools -> Add-Ons, you should there be able to identify which add-ons that are enabled. Using that information should give you a hint on which packages to uninstall. My guess is that, for flash, you've installed gnash or perhaps knash instead of the flashplugin (can be found in synaptics). For java, maybe the plugin you're running is icedtea as it is one of the alternatives offered automatically when you let firefox install plugin when first entering a java site.

---

### Post by gandaran on 2009-05-13
all you have to remove is the open source flash (swfdec-mozilla) plugin you have installed, keep or install only adobe flash!

---

### Post by dsg158 on 2009-05-13
> **gandaran said:**
> all you have to remove is the open source flash (swfdec-mozilla) plugin you have installed, keep or install only adobe flash!
thanks! that worked perfectly!

---

