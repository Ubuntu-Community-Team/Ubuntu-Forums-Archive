---
title: "Google Street View plugin ?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Drakkor on 2009-04-27
Yeah,on Google Maps,street view , it's all just a black screen :confused:

---

### Post by b0b138 on 2009-04-27
You need to install flash.

---

### Post by jrlii on 2009-04-27
I have Flash installed and Google Street View doesn't work on my system either. 

I just thought dial-up was too slow. . .

---

### Post by waspbr on 2009-04-27
did you install the ubuntu-restricted-extras package via medibuntu?

if not then copy and paste this into your terminal window

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

then at your terminal window type

```
sudo apt-get install ubuntu-restricted-extras
```


[Ref] [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Drakkor on 2009-04-27
Yeah, I did all that, still not working..........black

---

### Post by BDNiner on 2009-04-27
It doesn't work for me either! I just tried.

---

### Post by ShutterAce on 2009-04-27
Works fine for me.

Is this related to Jaunty or possibly the location your trying to load?

---

### Post by celem on 2009-04-27
Just tried it on my Dell 910 e/w Ubuntu 8.04 and it works like a champ!

---

### Post by waspbr on 2009-04-28
I have jaunty on 4 different machines and they all work fine...

perhaps google maps has got a glitch? Is that location available in other machines or  operating systems?

---

### Post by Drakkor on 2009-04-28
Works fine with Vista :confused:

---

### Post by ShutterAce on 2009-04-28
> **Drakkor said:**
> Works fine with Vista :confused:

Oh the horror!:lolflag:

---

### Post by halovivek on 2009-04-29
it is also not working for me also.

---

### Post by Rompues on 2009-04-29
It doesn't work for me either. Using 9.04 on Asus laptop. Works on my dual boot Vista OS and I already have Ubuntu restricted extras loaded.

---

### Post by fireoftroy on 2009-05-03
> **Rompues said:**
> It doesn't work for me either. Using 9.04 on Asus laptop. Works on my dual boot Vista OS and I already have Ubuntu restricted extras loaded.

Ditto.

---

### Post by HuckleSmothered on 2009-05-05
I am having this problem as well on a recent Jaunty clean install. I went to:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) 
... to test my flash install. Flash works, but Shockwave does not. I had removed swfdec-mozilla due to some other suggestions I had found. Didn't work. 

I already have the ubuntu-restricted-extras, flashplugin-nonfree, and medibuntu all setup.

Tried purging flashplugin-nonfree and then reinstalling. Same problem. Removing cache and history doesn't seem to help. Same problem in Epiphany and Firefox.

---

### Post by HuckleSmothered on 2009-05-05
Just in case the Street View uses Java, I installed sun-java6-jre and sun-java6-plugin. Tested here: 
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
Java works, but Street View still does not.

BTW, when testing Flash here:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)
Firefox pops up saying that additional plugins are required. I click on Find Missing Plugins and it comes up empty, nothing available to install.

I checked the latest version avail from Adobe here:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
It is 10.0.22.87.
Same as what flashplugin-nonfree says it is at.

---

### Post by crl0901 on 2009-05-05
I have this exact same problem.  I'm running Jaunty, have Flash installed and it won't work, just get a black screen.  The weird thing is, I have a T40 with Jaunty installed on it and it works.  Weird.

---

### Post by crl0901 on 2009-05-05
Well, I went to Synaptics and removed a couple packages and it works now.  The two I removed are:

swfdec-mozilla
mozilla-plugin-gnash

---

### Post by HuckleSmothered on 2009-05-05
I can confirm the fix.

Just for giggles, I uninstalled both packages, saw that it worked, reinstalled swfdec-mozilla (since removing it by itself earlier did not work) and it still works.

Thus the fix is:
sudo apt-get purge mozilla-plugin-gnash

---

### Post by crl0901 on 2009-05-06
> **HuckleSmothered said:**
> I can confirm the fix.

Just for giggles, I uninstalled both packages, saw that it worked, reinstalled swfdec-mozilla (since removing it by itself earlier did not work) and it still works.

Thus the fix is:
sudo apt-get purge mozilla-plugin-gnash

Good point.  You definitely need that swfdec-mozilla package to view things like Youtube videos.

---

### Post by fireoftroy on 2009-05-06
I went to remove mozilla-pluging-gnash and it said it wasn't installed.  That made me curious so I checked swfdec-mozilla and that wasn't there either.  Even after I added that, Street View still doesn't load.  What else am I missing?

---

### Post by crl0901 on 2009-05-06
> **fireoftroy said:**
> I went to remove mozilla-pluging-gnash and it said it wasn't installed.  That made me curious so I checked swfdec-mozilla and that wasn't there either.  Even after I added that, Street View still doesn't load.  What else am I missing?

I have flashplugin-installer and swfdec-mozilla installed.  I DO NOT have flashplugin-nonfree installed.  Maybe that's where it's tripping up?

---

### Post by Frantic_Earthling on 2009-05-07
> **crl0901 said:**
> Well, I went to Synaptics and removed a couple packages and it works now.  The two I removed are:

swfdec-mozilla
mozilla-plugin-gnash


Neither *swfdec-mozilla* nor *mozilla-plugin-gnash* are installed on my system

I am running 9.04 and Street View does not work for me either.

---

### Post by fireoftroy on 2009-05-08
> **crl0901 said:**
> I have flashplugin-installer and swfdec-mozilla installed.  I DO NOT have flashplugin-nonfree installed.  Maybe that's where it's tripping up?

I removed flashplugin-nonfree and that still didn't fix it (the other two are there).

---

### Post by HuckleSmothered on 2009-05-08
You *need* flashplugin-nonfree
Make sure it is installed and working correctly.
Visit this site to check: [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

1. Close Firefox

2. Install the flash plugin
**sudo apt-get install flashplugin-nonfree**

3. Uninstall gnash plugin
**sudo apt-get purge mozilla-plugin-gnash**

4. Reopen Firefox and retry

If it doesn't work, what is it doing? 
Black screen, error, crashing? 
Test the flash install at the adobe link above.
Let us know the results.

---

### Post by fireoftroy on 2009-05-08
The camera icons appear on the map, but as soon as they fully render, the layer reloads and the process continues over and over.  Some street labels also appear, render, then reload with the camera icons.

---

### Post by Drakkor on 2009-05-08
I have flashplugin-nonfree, I don't have the  mozilla-plugin-gnash
I get a black screen !

---

### Post by fireoftroy on 2009-05-13
Reinstalled and verified Flash.  No joy; same as before.

---

### Post by adambh on 2009-05-14
> **crl0901 said:**
> Well, I went to Synaptics and removed a couple packages and it works now.  The two I removed are:

swfdec-mozilla
mozilla-plugin-gnash

I removed swfdec-mozilla 
and added mozilla-plugin-gnash which i didnt have

restarted firefox et voila, it works.

---

### Post by Frantic_Earthling on 2009-05-14
> **adambh said:**
> I removed swfdec-mozilla 
and added mozilla-plugin-gnash which i didnt have

restarted firefox et voila, it works.

Did the same.
No joy.
Doesn't work:confused::confused::confused:

---

### Post by garfield185 on 2009-06-09
Hi everybody.

I just did what clr0901 wrote, look some posts before.

I uninstalled these packages:

swfdec-mozilla
mozilla-plugin-gnash

Then, tried to open street view, but google maps said: "You must install the last flash version" with a link to it.  I installed it, and finally, it worked.

Thanks everybody!

---

### Post by Drakkor on 2009-06-09
Thanks, garfield185 , didn't have gnash, but swfdec-mozilla, removed that,
and now it finally works !  :p

---

### Post by noteviljoe on 2009-06-15
> **Drakkor said:**
> Thanks, garfield185 , didn't have gnash, but swfdec-mozilla, removed that,
and now it finally works !  :p

So removing swfdec-mozilla worked for me :-), will I loose anything by removing this?

---

### Post by HuckleSmothered on 2009-06-15
Removing swfdec-mozilla did not affect anything that I could find whatsoever for me.

---

### Post by Frantic_Earthling on 2009-06-15
> **HuckleSmothered said:**
> Removing swfdec-mozilla did not affect anything that I could find whatsoever for me.

Please see:

[http://ubuntuforums.org/showthread.php?t=1174754](http://ubuntuforums.org/showthread.php?t=1174754)

That did it for me!

---

