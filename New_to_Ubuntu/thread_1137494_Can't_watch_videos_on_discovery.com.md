---
title: "Can't watch videos on discovery.com"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by curiousnoob on 2009-04-25
I am not able to watch any video on discovery.com for some reason.  It uses flash and I have no problem with any other sites that I know about and I use to be able to view it just fine.  
I attempted to download the latest version of Flash thinking that would solve the problem but when I do that I get an error saying I already have a newer version so I am at a loss what the issue might be.  
Here is the link to one of the videos I am having trouble with: 
[http://dsc.discovery.com/videos/mythbusters-homemade-surround-sound.html](http://dsc.discovery.com/videos/mythbusters-homemade-surround-sound.html) 

Any ideas or suggestions would be greatly appreciated.

---

### Post by curiousnoob on 2009-04-25
Just as a clarification.  I am not talking about the Discovery.com Player which shows full episodes.  I know that that is currently incompatible with linux currently.  I am just talking about the streaming clips like the one in my link.

---

### Post by llamabr on 2009-04-25
How did you install flash?  From apt or synaptic, or from some webpage?

---

### Post by curiousnoob on 2009-04-25
> **llamabr said:**
> How did you install flash?  From apt or synaptic, or from some webpage?

I went to 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) 
and downloaded the deb

---

### Post by fballem on 2009-04-25
> **curiousnoob said:**
> I went to 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) 
and downloaded the deb

Are you running 32-bit ubuntu or 64-bit ubuntu? The reason that I ask is that the deb you identified is 32-bit, which requires specialized installation on 64-bit ubuntu.

---

### Post by Joomla12 on 2009-04-25
Yeah, Adobe started hosting the Linux Flash plugin pretty recently I believe.

I'm having problems with Flash things all together. I always have a grey "Play" symbol over a Flash object and YouTube videos stream horrible. They're always showing colorful pixels at the beginning at don't ever have the option to play again. I'm guessing it's just a bug in Jaunty.

As for you, try removing the Flash plugin from the Synaptics Manager and then re-installing the Debian from Adobe.

---

### Post by curiousnoob on 2009-04-25
> **Joomla12 said:**
> Yeah, Adobe started hosting the Linux Flash plugin pretty recently I believe.

I'm having problems with Flash things all together. I always have a grey "Play" symbol over a Flash object and YouTube videos stream horrible. They're always showing colorful pixels at the beginning at don't ever have the option to play again. I'm guessing it's just a bug in Jaunty.

As for you, try removing the Flash plugin from the Synaptics Manager and then re-installing the Debian from Adobe.

I reinstalled Flash doing what you said but that did not resolve the issue.  
I am also running the 32 bit version of Ubuntu.  
Not sure what the heck is going on.

---

### Post by mike555 on 2009-04-25
They may be using "silverlight " , you could install "moonlight" on your Linux computer to watch it .....
  [http://mono-project.com/Moonlight](http://mono-project.com/Moonlight)

---

### Post by curiousnoob on 2009-04-25
> **mike555 said:**
> They may be using "silverlight " , you could install "moonlight" on your Linux computer to watch it .....
  [http://mono-project.com/Moonlight](http://mono-project.com/Moonlight)

This looks very interesting but I am not sure how to install it.  I have downloaded the .xpi file and extracted it but I see no way of actually intsalling it.

---

### Post by albinootje on 2009-04-25
> **curiousnoob said:**
>  Here is the link to one of the videos I am having trouble with: 
[http://dsc.discovery.com/videos/mythbusters-homemade-surround-sound.html](http://dsc.discovery.com/videos/mythbusters-homemade-surround-sound.html) 

Any ideas or suggestions would be greatly appreciated.
I'm using this on Hardy :
```

ii flashplugin-nonfree 9.0.159.0ubuntu1~hardy1 Adobe Flash Player plugin installer

```
works fine, both in Firefox and Galeon.

---

### Post by mike555 on 2009-04-25
> **curiousnoob said:**
> This looks very interesting but I am not sure how to install it.  I have downloaded the .xpi file and extracted it but I see no way of actually intsalling it.

You drag it (the .xpi file ) into the add-ons window of Firefox.....

---

### Post by albinootje on 2009-04-25
> **mike555 said:**
> You drag it (the .xpi file ) into the add-ons window of Firefox.....

I'm not using that Moonshine addon, and I also don't have compiz in use, and that video works fine for me.

Which Ubuntu release is it ? 
And is it an upgrade or a fresh Ubuntu installation ?

---

### Post by wizard10000 on 2009-04-25
> **mike555 said:**
> They may be using "silverlight " , you could install "moonlight" on your Linux computer to watch it .....
  [http://mono-project.com/Moonlight](http://mono-project.com/Moonlight)

Nah - it's flash.  I have flashblock installed and it blocked the video until I pressed the button to let it run.

Ran fine, though.

---

### Post by curiousnoob on 2009-04-26
> **albinootje said:**
> I'm using this on Hardy :
```

ii flashplugin-nonfree 9.0.159.0ubuntu1~hardy1 Adobe Flash Player plugin installer

```
works fine, both in Firefox and Galeon.

I'm sure this is a dumb question but how to I install that version?

---

### Post by Efros on 2009-04-26
Adblock will also block these videos from the discovery site, disabling that will allow you to play them.

---

### Post by curiousnoob on 2009-04-26
> **Efros said:**
> Adblock will also block these videos from the discovery site, disabling that will allow you to play them.

You, my friend, have just become my favorite person in the world.  That totally worked and I can't believe I didn't try it sooner.  
=D>

---

### Post by albinootje on 2009-04-26
> **curiousnoob said:**
> I'm sure this is a dumb question but how to I install that version?

Good that you solved the problem now! :)

And just for the record, you would remove the other flash package you got installed, and then install the package  "flashplugin-nonfree" from within Synaptic Package Manager (or, much faster, with apt-get in a terminal).

---

### Post by philinux on 2009-04-26
[http://dsc.discovery.com/videos/mythbusters-homemade-surround-sound.html](http://dsc.discovery.com/videos/mythbusters-homemade-surround-sound.html)
Refuses to play here using adobe player and FF safe mode.
Going to the home page on this site plays flash fine.

Plays all other flash on that page and flash on other sites.

Fine in windblows.

---

### Post by Efros on 2009-04-26
> **curiousnoob said:**
> You, my friend, have just become my favorite person in the world.  That totally worked and I can't believe I didn't try it sooner.  
=D>
The only reason I figured it out was the videos wouldn't work on Firefox on a MacBook, Common denominator was adblock!

---

### Post by philinux on 2009-04-27
Weird, works fine on my desktop with adblock and flashblock on. But wireless lappy is a no no.

---

