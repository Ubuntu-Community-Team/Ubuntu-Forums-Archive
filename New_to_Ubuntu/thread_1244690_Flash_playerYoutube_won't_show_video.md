---
title: "Flash player/Youtube won't show video"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by xFlowx on 2009-08-19
**This has been solved. Thanks for all your help, guys! 8D**

Okay! So I've been using Ubuntu for about ...almost two months. Today, my computer started to act up and I was trying to install updates. While I was doing that, it was giving me an error that there wasn't any space for it in drive "/". After that, I tried to get rid of things that I didn't use to try and clear up space. I'm still new to this, so I didn't know what to do.

But I kept trying to post a question here, and Firefox wouldn't stay open long enough for me to ask questions. I finally broke down and re-installed Ubuntu 9.04 on my computer...Now my main problem is how videos won't work on Youtube. However, I get audio. Before the video stopped working, I watched one video with no problem(other than how I couldn't use the volume on the site), and now I only see black and hear music.

Is there any way to fix this? Or did I do something wrong?

This is frustraiting...but that's why I'm asking.

Thanks for any and all help!

---

### Post by chazn85 on 2009-08-19
i think what you are going to be missing is the flashplayer.  in the repos as flashplugin-nonfree so you you should be able to install it with apt.

---

### Post by herbertportillo on 2009-08-19
The quickest way to do it is to use the terminal. Go to Applications -> Accessories -> Terminal and type "sudo apt-get install flashplugin-installer" and then it'll ask you for your password. That should do it.

---

### Post by datacw on 2009-08-19
ok download wine then install it then flash and it should work

(or u have java script disabled if so go to edit preferences content and javascript it should be ticked)

hope i helped:lolflag:

---

### Post by xFlowx on 2009-08-19
> **herbertportillo said:**
> The quickest way to do it is to use the terminal. Go to Applications -> Accessories -> Terminal and type "sudo apt-get install flashplugin-installer" and then it'll ask you for your password. That should do it.

Oops, haha. You have Xubuntu. My mistake.

Nooo, I have Ubuntu Jaunty Jakalope XD I'm pretty sure it's normal Ubuntu?


```
But when I do that, I got 
 Reading state information... Done
flashplugin-installer is already the newest version.
flashplugin-installer set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
flow@flow-desktop:~$ 
```

---

### Post by xFlowx on 2009-08-19
> **datacw said:**
> ok download wine then install it then flash and it should work

(or u have java script disabled if so go to edit preferences content and javascript it should be ticked)

hope i helped:lolflag:

Uuh, Javascript is checked...It was working but quit XP I'm installing wine right now

---

### Post by herbertportillo on 2009-08-19
Then I guess you can do what "chazn85" said.

Go to System -> Administration -> Synaptic Package Manager and type in your password. Then in the search bar at the top type in "flash" and then click on flashplugin-nonfree and install it.

I just installed Ubuntu two weeks ago; I'm pretty new to this as well.

---

### Post by xFlowx on 2009-08-19
> **chazn85 said:**
> i think what you are going to be missing is the flashplayer.  in the repos as flashplugin-nonfree so you you should be able to install it with apt.

Wait, what?

It's already been installed and only gives me the option of 'reinstallation'....

---

### Post by xFlowx on 2009-08-19
> **herbertportillo said:**
> Then I guess you can do what "chazn85" said.

Go to System -> Administration -> Synaptic Package Manager and type in your password. Then in the search bar at the top type in "flash" and then click on flashplugin-nonfree and install it.

I just installed Ubuntu two weeks ago; I'm pretty new to this as well.

Okay, I did thaat...and...it says 'reinstall' it, so I'm doing that.

And yaaay~ You're a newbie like me 8D


But this still didn't fix my problem Dx

---

### Post by herbertportillo on 2009-08-19
I guess you could try installing the restricted extras package.

Go back to Synaptic Package Manager and search for "restricted" and download the package called "ubuntu-restricted-extras". That should add the flash plugin, DVD support and some other goodies, as well.

---

### Post by running_rabbit07 on 2009-08-19
The best way I know of to get flash player up and running is go to myspace.com. As soon as the page loads it will offer you a choice of three flash players. Has worked with every install I have done. 

I hope this helps.

---

### Post by chazn85 on 2009-08-19
you can also verify firefox actually has this plugin in $HOME/.mozilla/plugins/    you should see libflashplayer.so

---

### Post by xFlowx on 2009-08-19
> **running_rabbit07 said:**
> The best way I know of to get flash player up and running is go to myspace.com. As soon as the page loads it will offer you a choice of three flash players. Has worked with every install I have done. 

I hope this helps.


Eew, myspace. It did nothing..Dx

---

### Post by murderslastcrow on 2009-08-19
C'mon guys, this is DAVID BOWIE we're helping out here. Can't you be a bit more helpful? XD

K, first thing you wanna' do is go into your native Linux browser and type about:plugins into the address bar. Press enter.

It should list all of your available plugins. Shockwave Flash or something similar should be listed, and should have a version number. If it's 9, or 9.anything, that's your problem. If this is the case, you should go to the synaptic package manager (System>Administration>Synaptic Package Manger).

Click the reload button, and make sure the list on the left is set to "all." Type in flash and uninstall non-free and any other related packages. Then type in swf, and make sure there are no swfdec-mozilla packages, or anything similar to that. Click the box to uninstall these, then go back into your browser and download the deb from the official adobe flash site.

After it's done downloading, close Firefox (or what have you), and install the deb package. After this, go back into Firefox and type about:plugins again. It should list the plugin as Flash 10.

Tell me if this was at all helpful, or if you still have version 10 in the first place.

---

### Post by herbertportillo on 2009-08-19
Do this, it should do the trick. If it doesn't, I don't know what else to tell you, sorry.

Go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download the .tar.gz version to your desktop.

When it's done downloading, double click it and extract it to the desktop. There should be a file called "libflashplayer.so".

Open up a terminal and type "cd ~" to make sure you're in the home directory.

Then type "cd Desktop" to navigate into the desktop.

Then type "sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins".

THAT should do it, haha

---

### Post by xFlowx on 2009-08-19
> **murderslastcrow said:**
> C'mon guys, this is DAVID BOWIE we're helping out here. Can't you be a bit more helpful? XD

K, first thing you wanna' do is go into your native Linux browser and type about:plugins into the address bar. Press enter.

It should list all of your available plugins. Shockwave Flash or something similar should be listed, and should have a version number. If it's 9, or 9.anything, that's your problem. If this is the case, you should go to the synaptic package manager (System>Administration>Synaptic Package Manger).

Click the reload button, and make sure the list on the left is set to "all." Type in flash and uninstall non-free and any other related packages. Then type in swf, and make sure there are no swfdec-mozilla packages, or anything similar to that. Click the box to uninstall these, then go back into your browser and download the deb from the official adobe flash site.

After it's done downloading, close Firefox (or what have you), and install the deb package. After this, go back into Firefox and type about:plugins again. It should list the plugin as Flash 10.

Tell me if this was at all helpful, or if you still have version 10 in the first place.

Hahah, David Bowie's wife, actually (XD; I wish!) I did have version 9 and this seemed to fix the problem!

Thank you! 8D

---

### Post by murderslastcrow on 2009-08-19
No problem. Hopefully this doesn't show up in Karmic. Just another 'papercut'.

---

### Post by running_rabbit07 on 2009-08-19
> **xFlowx said:**
> Eew, myspace. It did nothing..Dx

I am glad to hear you got it working. 

My fix only works when there isn't a Flash player already installed.

---

### Post by zerhacke on 2009-08-19
> **datacw said:**
> ok download wine then install it then flash and it should work

(or u have java script disabled if so go to edit preferences content and javascript it should be ticked)

hope i helped:lolflag:

wine has absolutely nothing to do with flash.  You don't need wine to make flash run.  Installing wine needlessly when he already said he had disk space problems is a BAD idea.

---

