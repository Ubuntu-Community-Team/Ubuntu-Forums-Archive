---
title: "Problem installing Flash Plugin"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by vivek.purushoth on 2011-06-08
Hello

Thank you . I would be very glad if someone can help me out with this. I need to install the flash Player and plugin because the browser says missing plugin and install flash player .
I am not able to install from this link [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect) .
And i am not able to install using the terminal code
sudo apt-get install adobe-flashplugin
It gives an error message
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another.
Can anyone give me the perfect link to the file to be downloaded and installed or the correct working terminal code which would give me the latest version of flash player with the latest update .

---

### Post by wolfen69 on 2011-06-08
From that link download the .tar.gz flash file, right click, extract here, and put the libflashplayer.so file into ~/.mozilla/plugins folder. You can find that folder by going to your home folder and doing Ctrl-H, then you'll see the .mozilla folder. Inside that, create the plugins folder. Restart firefox if open.

---

### Post by cottfcfan on 2011-06-08
You need to go into synaptic & make sure that "canonical partners" & "independant" are ticked in your software sources.
Then go into a terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```
This will give you Flash, Java & any other codecs you're likely to need.

If you just want the Flash player its:
```
sudo apt-get install flashplugin-installer
```

---

### Post by 3xp10r3r|X13 on 2011-06-08
> **wolfen69 said:**
> From that link download the .tar.gz flash file, right click, extract here, and put the libflashplayer.so file into ~/.mozilla/plugins folder. You can find that folder by going to your home folder and doing Ctrl-H, then you'll see the .mozilla folder. Inside that, create the plugins folder. Restart firefox if open.

As far, as I'm concerned you insert the libflashplayer.so into "/usr/lib/mozilla/plugins" ?

For me it worked that way :)

---

### Post by ivanovnegro on 2011-06-08
> **cottfcfan said:**
> You need to go into synaptic & make sure that "canonical partners" & "independant" are ticked in your software sources.
Then go into a terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```This will give you Flash, Java & any other codecs you're likely to need.

If you just want the Flash player its:
```
sudo apt-get install flashplugin-installer
```

+1 That is actually the good solution. Why to bother with external stuff.
@OP: Use Synaptic or the Software Center, it is made to install new stuff/software/plugins you need for your Ubuntu system.

In general if you want to install new software, use your repositories.

---

### Post by wolfen69 on 2011-06-08
> **3xp10r3r|X13 said:**
> As far, as I'm concerned you insert the libflashplayer.so into "/usr/lib/mozilla/plugins" ?

For me it worked that way :)

That's another way to do it.

---

### Post by 3xp10r3r|X13 on 2011-06-08
fair enough :)

---

### Post by vivek.purushoth on 2011-06-08
@wolfen69- Thanks .I tried what u have said . Even after i tried that it said download plugin in these kind of pages
[http://www.gamegecko.com/game/708/dots-and-boxes](http://www.gamegecko.com/game/708/dots-and-boxes)
Even when i say download plugin it says plugin not found.
@cottfcfan - Thanks . I am an Amateur in Ubuntu . How to go to Synaptic(U mean Synaptic Manager??).I couldn't find those options in Synaptic Manager.
I tried that code in terminal
sudo apt-get install ubuntu-restricted-extras.
And after it processed then
i opened this page [http://www.gamegecko.com/game/708/dots-and-boxes](http://www.gamegecko.com/game/708/dots-and-boxes)
in Google chrome , it still says missing plug-in   
I use Google Chrome.

---

### Post by ivanovnegro on 2011-06-08
> **vivek.purushoth said:**
> @wolfen69- Thanks .I tried what u have said . Even after i tried that it said download plugin in these kind of pages
[http://www.gamegecko.com/game/708/dots-and-boxes](http://www.gamegecko.com/game/708/dots-and-boxes)
Even when i say download plugin it says plugin not found.
@cottfcfan - Thanks . I am an Amateur in Ubuntu . How to go to Synaptic(U mean Synaptic Manager??).I couldn't find those options in Synaptic Manager.
I tried that code in terminal
sudo apt-get install ubuntu-restricted-extras.
And after it processed then
i opened this page [http://www.gamegecko.com/game/708/dots-and-boxes](http://www.gamegecko.com/game/708/dots-and-boxes)
in Google chrome , it still says missing plug-in   
I use Google Chrome.

Refresh your the site or reopen the browser.

If you want to go to Synaptic, just hit the Windows key and then type Synaptic if you are on 11.04.

---

### Post by no2498 on 2011-06-08
in fire fox click tools abought plugins install flash aid
then run it
restart fire fox

---

### Post by 3xp10r3r|X13 on 2011-06-08
or insert the "libflashplayer.so" file into "/usr/lib/mozilla/plugins", as already mentioned. It should work!!!

Well, surely do the usual stuff afterwards (restarting firefox)

---

### Post by cottfcfan on 2011-06-08
vivek.
I use Google Chrome and that site works fine.
Try logging out & in again, then open the browser and try again.
In synaptic package manager, click settings, repositories, other software, and make sure "canonical partners" & "independant" are checked then reload synaptic & install any upgrades.
Although this shouldn't be necessary to get Flash working.

---

### Post by iansane on 2011-06-08
Is your system 11.04? 32 or 64 bit?

That makes a difference as adobe only has a test version of the 64 bit. 

I'm using 11.04 64 and my firefox is working fine but the flash plugin is a symbolic called flashplugin-alternative that points to /etc/alternatives/firefox-flashlugin which is another symbolic link pointing to the /var/lib/flashplugin-installer/npwrapper.libflashplayer

So, dropping the file from adobe in the /user/lib/firefox/plugins directory may not work in this case because firefox is using a different file name.

However, I also use chrome which is working fine, and I use 64bit swiftfox and the method described by wolfen69 worked for swiftfox even though it is the 32 bit flashplayer.so file.

But all this is irrelevant if you are using 32bit. Just wanted to add info that might help

---

### Post by cottfcfan on 2011-06-09
Iansane..
You don't have to touch the flashplugin directory.
Installing ubuntu-restricted-extras in 32 or 64bit and Flash just works on both Firefox & Chrome, without having to do anything else.

---

### Post by rimibchatterjee on 2011-06-17
Thanks Wolfen69, got your mail with libflashplayer attached. Have downloaded as instructed. Logging out now to restart firefox. Wish me luck!

---

### Post by shibu_sawyer on 2011-06-17
I had this flash problem,flash player and flash plugin's are available in software center of ubuntu, try that, i installed it, worked fine.. My second opinion is,installing restricted extras if not working, installing restricted extras will definitely solve the prob..

---

