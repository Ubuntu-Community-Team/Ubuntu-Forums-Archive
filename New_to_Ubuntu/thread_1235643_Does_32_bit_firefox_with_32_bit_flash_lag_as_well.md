---
title: "Does 32 bit firefox with 32 bit flash lag as well?"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by lems on 2009-08-09
I have 64 bit firefox and 64 bit flash installed and it's lagging like non other. Will downgrading help or is this just a linux prob?

---

### Post by gn2 on 2009-08-09
Is it from the repositories, or is it a download from the Adobe website?
I have found that the one from Adobe works best.

Download it here (link at bottom of page): [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Installation how-to: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by jerome1232 on 2009-08-09
It's just an adobe prob.

If you installed from repos your actually using the 32bit version. Try the 64bit ver on their site.

For some reason when I have you tube switch to hd the fullscreen lag clears up.

/shrug

---

### Post by gn2 on 2009-08-09
> **jerome1232 said:**
> ~ If you installed from repos your actually using the 32bit version.....

...with nspluginwrapper which is the culprit for slowing things down and running the CPU up to 100%.
Nasty.

---

### Post by lems on 2009-08-09
> **gn2 said:**
> Is it from the repositories, or is it a download from the Adobe website?
I have found that the one from Adobe works best.

Download it here (link at bottom of page): [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Installation how-to: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

I have that one installed. Still lags. I mean it's fine on youtube, but when I go full screen it's unbearable. Other sites don't run as smoothly as youtube. Some sites I go to are flash heavy with flash ads etc... these lag A LOT.

---

### Post by gn2 on 2009-08-09
All I can say is I have 64-bit 8.04 and flash is smooth both minimised and fullscreen using the Adobe version.

:idea: ...but I don't have any desktop effects enabled.
Have you tried turning them off yet?

---

### Post by pissedoffdude on 2009-08-25
I'm having the same issue too, and it's definitely a problem with 64-bit flash and high resolutions. 

I've only tried 32-bit flash with chromium, and it was not laggy at all.

My laptop that runs at 1360x768 and works just fine with 64-it flash.

Make sure you have the latest nvidia drivers too.  The latest ones will give you better performance than the ones you get from the restricted drivers.

---

