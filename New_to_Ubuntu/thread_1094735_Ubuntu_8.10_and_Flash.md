---
title: "Ubuntu 8.10 and Flash"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by nml on 2009-03-12
I know, this has been covered in multiple angles ad nauseum...but not only an I an EXTREME Noob, I think I'm stupid..

Saying that, I've read tons of threads about being able to view flash files on YouTube.....but I can't make this installation do it.  Not only that, but I've installed and uninstalled so many things (so many times), that I can't get any type of flash files to work...initially my FF had flash 9, since I've been all over the web trying STUFF, I don't know what I've still got installed.....

I need so much help, the beginners board is probably to advanced....

So...what can I post to begin getting help to be able to view videos on YouTube.....and possibley be able to view any other flash file through FireFox 3.

Oh yeah, I'm sure I'll have tons of difficulties with even the most simple of requests....but I'll try like crazy.. 

TIA,

Mick
(and I really have spent time reading the files on beginning Ubuntu)

---

### Post by humphreybc on 2009-03-12
Hi there, I'm not a guru or anything but all it took for me to get flash up and running was to go to youtube and try to watch a video in firefox, then when the thing pops down click "install missing plugins" and it'll install flash... restart firefox and you're good to go. In theory.

---

### Post by nml on 2009-03-12
*try to watch a video in firefox, then when the thing pops down click "install missing plugins" and it'll install flash.*

Unfortunately, I've done so much installing, updating and uninstalling....I don't get any flash popups any more....I don't even get the box.....just a white space..

---

### Post by suitedaces on 2009-03-12
I can't give you commands (sorry) but I fixed this problem by removing all flash updates and re-installing just one. If you have a quick look you might find it.

---

### Post by DGortze380 on 2009-03-12
Open System -> Administration -> Synaptic Package Manager

Search for Ubuntu-Restricted-Extras

Check the box, click apply.

---

### Post by suitedaces on 2009-03-12
> **suitedaces said:**
> I can't give you commands (sorry) but I fixed this problem by removing all flash updates and re-installing just one. If you have a quick look you might find it.

Found the post that worked for me.

> **ubu_dynamite said:**
> Do you have both adobe flashplayer and flashplugin-nonfree instalt?

remove all flash
```
sudo aptitude purge mozilla-plugin-gnash
sudo aptitude purge adobe-flashplugin
sudo aptitude purge flashplugin-nonfree
```
and just install flashplugin-nonfree
```
sudo aptitude install flashplugin-nonfree
```
or if you realy want flash 10 just install it from the site but don,t install them both it will not work

---

### Post by nml on 2009-03-12
*Search for Ubuntu-Restricted-Extras*

just reinstalled this, restarted FF and still can't play Flash vids on YouTube...Says I need to get the latest Flash update (again)....I've gone to the Adobe site multiple times and installed the player (by way of the 8.04 deb file)...not really sure how to install the other methods (though I spent several hours last night trying)

Mick

---

### Post by suitedaces on 2009-03-12
> **nml said:**
> *Search for Ubuntu-Restricted-Extras*

just reinstalled this, restarted FF and still can't play Flash vids on YouTube...Says I need to get the latest Flash update (again)....I've gone to the Adobe site multiple times and installed the player (by way of the 8.04 deb file)...not really sure how to install the other methods (though I spent several hours last night trying)

Mick

Try my above suggestion. I can't guarantee, but I had similar problems and it worked a charm.

---

### Post by nml on 2009-03-12
> **suitedaces said:**
> Try my above suggestion. I can't guarantee, but I had similar problems and it worked a charm.

I'll do it..........back in a 'flash'.. (sorry, bad humor)

---

### Post by suitedaces on 2009-03-12
> **nml said:**
> I'll do it..........back in a 'flash'.. (sorry, bad humor)

:lol: A fella after my own heart!

---

### Post by humphreybc on 2009-03-12
> i'll do it..........back in a 'flash'.. (sorry, bad humor)

lol

---

### Post by nml on 2009-03-12
suitedaces....you da man....

It works....everything seems to work....I can't believe how much I read and how much stuff I've tried to get this result..

Man, you've made my night...

Many thanks....

---

### Post by suitedaces on 2009-03-12
Don't thank me, thank ubu_dynamite. I only knew the answer because it tortured me for ages too! Just glad to have popped my advice-giving cherry!

---

