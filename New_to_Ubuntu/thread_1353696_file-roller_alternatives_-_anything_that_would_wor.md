---
title: "file-roller alternatives - anything that would work"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by siddartha on 2009-12-13
I have installed ubuntu-network-remix on a laptop and I am impressed of how slim that remix is. One of the issues is that file-roller comes bundled in. And that is a bad choice. On the desktop I have ark installed and never had a problem. With file-roller things are quite the opposite. Each time there is a new install and the defaults kick in there you have that crap. Untill last year that junk was unable in some random cases to open the current directory for saving up the contents of the archive. You had to repass start just like in monopoly, go to home and go all the way down the fs tree in order to reach that directory again and save it. I say it's one year becase it's one year since I have last used the bloody thing.

Now I needed to open up a rar file. Cool. Double clicked it and there I have file roller again telling me that rar is not supported. If it's not supported why in the world would file roller consume battery and processor power to start? Anyway, went up and installed unrar-free. And file roller told me this time that everything is ok. I checked the directory and there was no sign of the file. Redone. Everything went fine, yet no file. Thought about that issue above (not the only one) and repassed the whole fs tree. Still... no answer. Went up manual and the terminal informed me that unrar-free does not handle that archive. The morons writing that file roller had no idea... well, they had no idea they should not start the app for an unsupported archive. So I went back, installed the unrar tool and did it all from the terminal. Now... I see no reason to waste resources on a graphical interface when I do my work at the command line and as it does not seem to be a kde version of the notebook remix - is there another option? Is there a gnome developed archive manager that does not have trivial issues? I mean that is only a dumb wrapper which uses other people's work... yet for the Gnome guys that is waaaay too much to ask. Is there an independent project that uses gtk, yet does not share that "push as many libs as you can" Gnome philosophy?

---

### Post by Physical Hook on 2009-12-13
Try [COLOR=Green]squeeze[/COLOR].

---

### Post by siddartha on 2009-12-13
> **Physical Hook said:**
> Try [COLOR=Green]squeeze[/COLOR].

Sadly they subscribe to the same Gnome-ish philosophy. It requests a bunch of libs, including thunar. Now that thunar is another nautilus... yet nautilus is bound for this notebook remix. Something that is an archive manager and not a file manager plugin...?

---

### Post by 3rdalbum on 2009-12-13
If you install the "unrar" package (not the unrar-free package) you should be able to extract RARs.

Also, you can drag and drop the contents of archives from File Roller to an open file browser window. It's easier and more intuitive.

---

### Post by siddartha on 2009-12-13
> **3rdalbum said:**
> If you install the "unrar" package (not the unrar-free package) you should be able to extract RARs.

Also, you can drag and drop the contents of archives from File Roller to an open file browser window. It's easier and more intuitive.

Well, probably you have read another message related with my thread. I did that. The hacks writing that app have considered that "everything went fine" includes "the used version can't perform that operation" as well. I admit I don't have the willingness to test crap apps for each version and subversion (fspot and pidgin pop into my mind), but file roller used to have problems with drag and drop. Amazingly ark (KDE) over nautilus can do a fine job. In this case I don't want to install KDE to run an ugly mix of doubling the used libs in memory. I don't care about the interface inconsistencies, only about resource waste. I would do that for my desktop - brasero can't hold a candle to a deprecated version of k3b, kopete can do video years before pidgin and without changing names every two years, konky can do video thumbnailing without totem integration, heck, most working video players are on KDE...

So I am looking for what file roller promises without deliver and if possible without extra dependencies. Pretty much like uninstalling network manager and installing wicd can solve most connection problems and all that with less packs and less dependencies.

---

### Post by andrew.46 on 2009-12-14
Hi siddartha,

Would you consider using the simple commandline utilities available to Ubuntu to create, view and extract archives?

Andrew

---

### Post by siddartha on 2009-12-14
> **andrew.46 said:**
> Hi siddartha,

Would you consider using the simple commandline utilities available to Ubuntu to create, view and extract archives?

Andrew

Do you actually read before hitting reply? To quote from myself: > I see no reason to waste resources on a graphical interface when I do my work at the command line and as it does not seem to be a kde version of the notebook remix - is there another option?

---

### Post by andrew.46 on 2009-12-15
Hi siddartha,

> **siddartha said:**
> Do you actually read before hitting reply? 

My apologies, in fact I did actually misread your original post.

All the best,

Andrew

---

### Post by siddartha on 2009-12-15
For the moment I found the solution alone: peazip. It's larger than fileroller. But after working with quite a few archive types I had no problem. It supports a lot more formats, it seems a little bit faster (probably because it's not just a dumb front-end). I said to give file roller a final chance and at the third archive it announced everything ok, but the files weren't there. So that's the final for file-roller for the future. On the desktops there is only ark from KDE and on the laptop it is going to be peazip which integrates well and without extra libs needed.

---

### Post by IcarusR on 2009-12-15
If you have problems & 'lack of functionality' with the default apps why not  create your own tailor made install with Linux From Scratch. 
Then you could have only the apps you like & want installed & would then possibly get more enjoyment & functionality out of your Linux box.

[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

---

### Post by siddartha on 2009-12-15
> **IcarusR said:**
> If you have problems & 'lack of functionality' with the default apps why not  create your own tailor made install with Linux From Scratch. 
Then you could have only the apps you like & want installed & would then possibly get more enjoyment & functionality out of your Linux box.

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Hahahaha

---

