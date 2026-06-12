---
title: "Problems with Flash/YouTube"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Curt1944 on 2009-04-26
Not sure if this is the right section for this... but I figure I am an absolute beginner because I just installed Ubuntu for the first time today.  I am absolutely loving it, but right now I cannot play videos in YouTube, or most other video sites.  I searched the forum here but i couldn't find something that solved my issue.

I installed the flash plugin through Firefox when it prompted me to.  A little later I realized that YouTube is not working.  I can see the player and all that, but the video just doesn't play, or begin to buffer or anything.  I then looked around a bit for a solution.  I installed the flashplugin-nonfree thing through Synaptic.  I downloaded and installed the .deb right from Adobe for Flash Player 10.  Still the same thing, of course restarting the browser after each attempt to fix the problem.  

I tried playing youtube videos via the Movie Player app that comes in the installation.  It said I had to get some plugins, so I got them.  I can actually only get sound when I try to play YouTube through the movie player.  It says I need to get more plugins still but when it tries to search for them it says it can't find a suitable one.  And then Movie Player crashed haha.  

It actually says the same thing when i go to the Flash test page in Firefox, that I need more plugins but it can't find anything suitable.  It appears flash is working for other purposes, although I get a big ugly grey Play symbol over any flash content, but after I press it, it seems to run.  I tried a bunch of other video sites.  To be completely honest the only video I could get to work was youporn lol.  No idea what my problem is here but I would appreciate some help.

---

### Post by hw-tph on 2009-04-26
Try uninstalling swfdec-mozilla and libswf.

---

### Post by billgoldberg on 2009-04-26
> **hw-tph said:**
> Try uninstalling swfdec-mozilla and libswf.

and gnash

--

When firefox prompted you to install the flash player, it didn't install adobes one but another one, that is known to cause problems.

---

### Post by Curt1944 on 2009-04-26
Thanks, I uninstalled those things... it still didn't work, but then I disabled flash within Firefox and enabled it again and that sprung it to life lol, working now.  Thanks again.

---

### Post by Curt1944 on 2009-04-26
huh, spoke too soon... it stopped working again.  I had uninstalled the flashplugin-nonfree thing earlier, so i reinstalled that, and it worked again.  But once again when i navigated away and came back it didn't work.  Now i can't get it to work at all again.  This is strange.  I'm starting to think its not actually a flash issue because the player loads and all that but it just can't seem to transfer any video.  Any more ideas?

---

### Post by talsemgeest on 2009-04-26
> **Curt1944 said:**
> huh, spoke too soon... it stopped working again.  I had uninstalled the flashplugin-nonfree thing earlier, so i reinstalled that, and it worked again.  But once again when i navigated away and came back it didn't work.  Now i can't get it to work at all again.  This is strange.  I'm starting to think its not actually a flash issue because the player loads and all that but it just can't seem to transfer any video.  Any more ideas?
Remove all flash players you have installed, then install the package "ubuntu-restricted-extras" ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by BugFixBug on 2009-04-26
as said by others you have multiple flash players installed. you will have to deinstall some of them because they are interfering with each other.

you can get the official adobe flash player [here]("http://get.adobe.com/flashplayer/"). just download the debian package and let synaptic do the work for you. 

[URL="http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/"]
i came across the same problem friday when i updated and made a blogpost about it. This probarly will solve your problem as well.[/URL]

---

### Post by talsemgeest on 2009-04-26
> **BugFixBug said:**
> as said by others you have multiple flash players installed. you will have to deinstall some of them because they are interfering with each other.

you can get the official adobe flash player [here]("http://get.adobe.com/flashplayer/"). just download the debian package and let synaptic do the work for you. 

[URL="http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/"]
i came across the same problem friday when i updated and made a blogpost about it. This probarly will solve your problem as well.[/URL]
I would have to disagree with the .deb from there. Many users have been having trouble with it, and you will not get automatic updates. It is better just to install the "ubuntu-restriced-extras" meta-package.

---

### Post by BugFixBug on 2009-04-26
> **talsemgeest said:**
> I would have to disagree with the .deb from there. Many users have been having trouble with it, and you will not get automatic updates. It is better just to install the "ubuntu-restriced-extras" meta-package.

will this give updates? i asume it has the same contents as the download form adobe.com
```

sudo apt-get install flashplugin-nonfree

```

---

### Post by talsemgeest on 2009-04-26
> **BugFixBug said:**
> will this give updates? i asume it has the same contents as the download form adobe.com
```

sudo apt-get install flashplugin-nonfree

```
Well, it certainly should. Anyway, I have never had any problems with it, and everything works beautifully for me.

---

### Post by Curt1944 on 2009-04-26
So uninstalled the flash players that I could find, that being the flashplugin-nonfree one.  I installed the ubunutu-restricted-extras.  Still having issues.  The actual problems seems to be I can only play some videos and not others.

Your probably right that it is because of multiple flash players.  I don't know how to uninstall the .deb i downloaded from Adobe.  If i click to download it again it only gives me the option to reinstall and not uninstall.  I also searched for the package name it gives in Synaptic and I couldn't find it.  I'm still new at this so I don't really know what to do with the terminal unless given a command i can copy/paste haha.  There is also the shockwave flash plugin that was installed by Firefox itself I think, don't know if that is a seperate one or how to get rid of that either, or if I need to.

I also installed all the GStreamer plugins to get Amarok to play M4A files... could that be interfering as well some how?  Just trying to think of stuff I may have done that would be out of the ordinary.

---

### Post by Curt1944 on 2009-04-26
So I googled how to uninstall the .deb from Adobe, was able to do it though the terminal.  Now YouTube tells me that I don't have Flash installed at all.  Although I have the ubuntu-restricted-extras package...

---

### Post by gandaran on 2009-04-26
> **Curt1944 said:**
> So uninstalled the flash players that I could find, that being the flashplugin-nonfree one.  I installed the ubunutu-restricted-extras.  Still having issues.  The actual problems seems to be I can only play some videos and not others.

Your probably right that it is because of multiple flash players.  I don't know how to uninstall the .deb i downloaded from Adobe.  If i click to download it again it only gives me the option to reinstall and not uninstall.  I also searched for the package name it gives in Synaptic and I couldn't find it.  I'm still new at this so I don't really know what to do with the terminal unless given a command i can copy/paste haha.  There is also the shockwave flash plugin that was installed by Firefox itself I think, don't know if that is a seperate one or how to get rid of that either, or if I need to.

I also installed all the GStreamer plugins to get Amarok to play M4A files... could that be interfering as well some how?  Just trying to think of stuff I may have done that would be out of the ordinary.
the .deb package from adobe.com is adobe-flashplugin, you can find it in synaptic, also remove any open source flash gnash or swfdec.
now which ubuntu are you runnig? if ubuntu 9.04 flashplugin-installer is the new flash package to install for flash, for ubuntu 8.10 or older install flashplugin-nonfree, but you need to have the system fully updated or flashplugin-nonfree and adobe-flashplugin may not work at all!

---

### Post by Curt1944 on 2009-04-26
I'm running 9.04, I'm pretty sure its completely up to date, it prompted me to install some updates right after I installed it, and I did.  I installed flashplugin-installer, still lead to the same problems, so then I uninstalled ubuntu-restricted didn't make a difference.  I am sure that the flashplugin-installer is the only flash package I have right now.  I can play some youtube videos.  Others I can't... it seems to be about 50-50.  Not sure what the difference maker there is.

---

### Post by gandaran on 2009-04-26
> **Curt1944 said:**
> I'm running 9.04, I'm pretty sure its completely up to date, it prompted me to install some updates right after I installed it, and I did.  I installed flashplugin-installer, still lead to the same problems, so then I uninstalled ubuntu-restricted didn't make a difference.  I am sure that the flashplugin-installer is the only flash package I have right now.  I can play some youtube videos.  Others I can't... it seems to be about 50-50.  Not sure what the difference maker there is.
post the output of this code, type in firefox url bar
```
about:plugins
```

---

### Post by kjkoec on 2009-04-26
However, Gnome is a dependency of swfdec.  Is uninstalling safe in that case?

---

### Post by leandrogdesa on 2009-04-27
Efetue os seguintes procedimentos:

[B][I]# apt-get remove flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper adobe-flashplugin

# apt-get install adobe-flashplugin [/I][/B]

OBS.: Mantenha o Firefox fechado. Por fim, execute o Synaptic

***# synaptic***

E instale os seguintes pacotes:

[B]sun-java6-bin
sun-java6-jre
sun-java6-plugin
java-common
libcommons-lang-java[/B]

Abra o navegador e acesse o seguinte link, onde sera mostrado se o JAVA foi instalado corretamente: 
**[http://www.java.com/pt_BR/download/installed.jsp?detect=jre&try=1](http://www.java.com/pt_BR/download/installed.jsp?detect=jre&try=1)**

Se, aparecer a mensagem abaixo, o JAVA foi instalado corretamente:

[I][B]Versão do Java verificada
Parabéns!

Você tem o Java recomendado instalado (Version 6 Update 13). 
[/B][/I]

Após, estes procedimentos, feche o navegador, e logo em seguida, abra novamente, e o problema estará solucionado.

---

### Post by talsemgeest on 2009-04-27
> **leandrogdesa said:**
> Efetue os seguintes procedimentos:

[B][I]# apt-get remove flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper adobe-flashplugin

# apt-get install adobe-flashplugin [/I][/B]

OBS.: Mantenha o Firefox fechado. Por fim, execute o Synaptic

***# synaptic***

E instale os seguintes pacotes:

[B]sun-java6-bin
sun-java6-jre
sun-java6-plugin
java-common
libcommons-lang-java[/B]

Abra o navegador e acesse o seguinte link, onde sera mostrado se o JAVA foi instalado corretamente: 
**[http://www.java.com/pt_BR/download/installed.jsp?detect=jre&try=1](http://www.java.com/pt_BR/download/installed.jsp?detect=jre&try=1)**

Se, aparecer a mensagem abaixo, o JAVA foi instalado corretamente:

[I][B]Versão do Java verificada
Parabéns!

Você tem o Java recomendado instalado (Version 6 Update 13). 
[/B][/I]

Após, estes procedimentos, feche o navegador, e logo em seguida, abra novamente, e o problema estará solucionado.
Please, these forums are supposed to be english only. :)

---

### Post by gandaran on 2009-04-27
> **kjkoec said:**
> However, Gnome is a dependency of swfdec.  Is uninstalling safe in that case? 
the gnome package is only a meta package that installs some chosen open source software for those that want a truly free open source desktop environment no proprietary software like adobe flash.
you can install individually every package that makes up the gnome meta package without installing gnome (swfdec is a dependency of gnome) and yes you can remove swfdec it wont break anything.

---

### Post by Curt1944 on 2009-04-29
OK, so now I've realized that the same thing is happening to me in Windows lol.  So maybe its not even a Ubuntu problem.  Have no idea what to do about this.
 
In trying to fix this problem I actually uninstalled and re-installed firefox.  Then I tried installing Flash Player 9, when I try to play a video Firefox just crashes after about a second or two haha.  I have no clue how to get rid of Flash 9 now.  I downloaded the installer from here and installed the linux version:
 
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2)
 
Yeah, so now basically I have Flash 9 installed in Firefox in Ubuntu, so Firefox crashes on youtube all the time.  And I am having the same problem in Windows even most videos just don't even start... or may start after a very long wait.  No idea what to do.

---

### Post by Cresho on 2009-04-29
well, i just fixed the problem.  In nvidia settings, under x server xvideo settings, disable sync to vblank


update, never mind its still broken

---

### Post by Curt1944 on 2009-04-29
> **Cresho said:**
> well, i just fixed the problem. In nvidia settings, under x server xvideo settings, disable sync to vblank
 
 
update, never mind its still broken
 are you having the same issue?

---

### Post by Cresho on 2009-04-29
ya lots of people are having issues.  I went back to hardy since I use flash alot and besides,etqw was not running as well as i liked.

---

### Post by Curt1944 on 2009-04-30
So I've still been trying to fix this... I was able to uninstall the Flash 9 plugin I installed manually by deleting the file in mozilla plugins directory.  I then decided to try the Gnash plugin instead of Flash.  So I made sure all the flash plugins were gone and I installed Gnash.  Had the same problems with that where some videos played fine and others did not start.
 
What I can't believe is the same thing is happening in my WINDOWS installation as well now.  The exact same videos won't play and in both Windows and Ubuntu, its about a 50-50 split it seems for videos that will play and ones that just don't start.  Sometimes after a very long wait the video starts but this doesn't seem to be true all time either.  So I'm thinking this isn't even an issue with flash for me, or even Ubuntu because the same thing is happening in Windows and Ubunutu.  Although it started directly after I installed Ubuntu, so I figure that must have something to do with it.  I've googled around and I can't find anyone with the same problem.  Maybe its just something weird with my connection and it was just a coincidence that it started then, I don't know.  But I don't know what to do about this now and it is very annoying.

---

### Post by giantclam on 2009-05-06
I did a search for ubuntu-restricted-extras in synaptic and installed them and youtube now works beautifully.  

"Restricted", in this case, just means that these plugins could not come pre-packaged with ubuntu for various country-related legal reasons.   These are commonly used multimedia plugins and they may just do the trick.

---

### Post by servicetech on 2009-05-10
Unistallign all flash players then installing medibuntu resolved the issue for me.

---

### Post by jkd18 on 2009-05-12
Hey, thanks guys! All of u helped me get back my flash player up and running! :-) 
cheers. 
jkd

---

