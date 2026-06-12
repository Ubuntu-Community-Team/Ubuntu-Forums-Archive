---
title: "Firefox and shockwave"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-10-17
How can i install shockwave player on firefox...i am using
Shiretoko

---

### Post by dj-toonz on 2009-10-17
The only way to run shockwave player under Ubuntu or any other linux distro's is by using the windows version of firefox via wine

I have discovered a way to get Shockwave working under Linux.  I am using Ubuntu 6.06 (Dapper Drake), Wine 0.99.22, Firefox 1.5.0.7, and Shockwave 10.1.4.020.

   1. Install Wine.  For those who don't know, this is a program which will allow you to run Windows-based programs from within Linux.  Wine will automatically associate .exe files with itself.  More information on Wine is available at [http://www.winehq.com](http://www.winehq.com) .
   2. Download the Windows version of Firefox and install.  Wine will ensure the installer functions correctly.
   3. Install the Windows version of Shockwave for Mozilla.  I downloaded and installed it manually (slim install).

After these steps, I had a working Shockwave player from within Firefox.  Note that to use the Shockwave player, you must start the Windows version of Firefox, which will be running under Wine support.

taken from a 3 year old post but still works

---

### Post by vinutux on 2009-10-17
From wikipedia...*"]"[COLOR="Sienna"]Unlike Flash, the Shockwave browser plugin is not available for Linux or Solaris despite intense lobbying efforts. However, the Shockwave Player can be installed on Linux with CrossOver or by running a Windows version of a supported browser in Wine (with varying degrees of success)".[/COLOR]*

---

### Post by winotree on 2009-10-17
*Stupid Question Time*

This is a cut and paste from about plugins on my ASUS EeePC 701(B) 4GB, Xubuntu 9.04 with restricted extras 31 added from the repositories:

**Shockwave Flash**

 File name:  /usr/lib/flashplugin-installer/libflashplayer.so 
Shockwave Flash 10.0 r32

If this isn't the real Shockwave Flash then it must be a decent imitation -- it works just fine on my device.   What's your take on this?

NOTE -- no Windows, no Wine, no attempt to start an argument -- just an honest question.  :)

EDIT - as a matter of fact, every time I've gone to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) these past two years I've come away with Shockwave Flash as mentioned....

---

### Post by mcduck on 2009-10-17
> **winotree said:**
> *Stupid Question Time*

This is a cut and paste from about plugins on my ASUS EeePC 701(B) 4GB, Xubuntu 9.04 with restricted extras 31 added from the repositories:

**Shockwave Flash**

 File name:  /usr/lib/flashplugin-installer/libflashplayer.so 
Shockwave Flash 10.0 r32

If this isn't the real Shockwave Flash then it must be a decent imitation -- it works just fine on my device.   What's your take on this?

NOTE -- no Windows, no Wine, no attempt to start an argument -- just an honest question.  :)

EDIT - as a matter of fact, every time I've gone to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) these past two years I've come away with Shockwave Flash as mentioned....

That's the Flash plugin, not the Shockwave plugin. Shockwave and Shockwave Flash are two completely different things.

[http://en.wikipedia.org/wiki/Adobe_Flash]("http://en.wikipedia.org/wiki/Adobe_Flash")
[http://www.adobe.com/products/flashplayer/]("http://www.adobe.com/products/flashplayer/")

[http://en.wikipedia.org/wiki/Adobe_Shockwave]("http://en.wikipedia.org/wiki/Adobe_Shockwave")
[http://www.adobe.com/products/shockwaveplayer/]("http://www.adobe.com/products/shockwaveplayer/")

(The "Shockwave" in the Flash plugin's name is just a leftover from the time when Shockwave became popular, and Macromedia thought it would be a good idea to append "Shockwave" in all their product's names. So Flash became "Shockwave Flash", Freehand became "Shockwave Freehand", and so on.. )

---

### Post by winotree on 2009-10-17
Ohh -- so calling it so doesn't necessarily make it so!  :D  And an old man adds to his education and knowledge -- thanks.

---

### Post by coldReactive on 2009-10-17
And as far as I know, not many sites actually use Shockwave, I myself, have only run into one: Gaia Online.

---

### Post by mcduck on 2009-10-17
> **coldReactive said:**
> And as far as I know, not many sites actually use Shockwave, I myself, have only run into one: Gaia Online.

True, Shockwave was most popular in times before broadband internet, it was commonly used to create multimedia CD-ROMs. It had some use in the Internet when Flash was only able to handle vector graphics, since Shockwave could also do bitmap graphics, video content (and embedded Flash). But distributing such content over the slow network connections made sure that it never gained as great popularity in web as Flash did.

Now Flash has gained the most important features from Shockwave, and can handle most of the stuff people need. Shockwave is still used to some extent, mostly because it can do hardware-accelerated 3D graphics. There are some online game sites that use Shockwave, and the kids games you might find in cereal boxes and such are often created with Shockwave as well. Also I know that at least some years ago the Australian army used a Shockwave-based training application so it's not only for games.

---

