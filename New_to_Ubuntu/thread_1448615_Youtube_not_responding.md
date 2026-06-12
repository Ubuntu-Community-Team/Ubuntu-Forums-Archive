---
title: "Youtube not responding"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by RobMcL on 2010-04-06
Hey guys, I just installed compiz-fusion, and my effects are looking nice and fancy! But, youtube videos won't work. It'll play, but I can't pause, change the resolution, go fullscreen, or anything else like that. What should I do? 

P.S. You guys rock. Solved every one of my problems so far :guitar:

---

### Post by mike2357 on 2010-04-06
When youtube's controls don't work, it's sometimes a sign that you don't have Adobe Flashplayer installed.  I suggest you check that first, and then post back.

---

### Post by NightwishFan on 2010-04-06
You may either need a experimental flash player or to temporarily disable compiz. 

You can get a alpha flash by running this command:
```
sudo add-apt-repository ppa:brandonsnider/experimental-flash && sudo aptitude update && sudo aptitude reinstall flashplugin-installer
```

---

### Post by emanuel.b on 2010-04-06
It may be because you are using one of the open source flash players, instead of the official plugin. Go to [http://get.adobe.com/flashplayer](http://get.adobe.com/flashplayer) to get the official plugin. (Be sure to download the .deb file) You could also search "adobe-flashplugin" in synaptic. :)

---

### Post by ssulaco on 2010-04-06
[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1)

Quote from lovinglinux  Flash optimization
> First you need to enable the muliverse repository. Go to &#8220;System >> Administration >> Software Sources&#8221;, then tick the option &#8220;Software restricted by copyright or legal issues (multiverse)&#8221;, then click &#8220;Close&#8221; and then &#8220;Reload&#8221;.

To remove other flash plug-ins and install only the one from Adobe open &#8220;Applications >> Accessories >> Terminal&#8221;, then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree

worked great for me..

---

### Post by NightwishFan on 2010-04-06
The new one is natively 'flashplugin-installer' however 'flashplugin-nonfree' links to it. I believe it also conflicts with the other plugins, but manually removing them is always a safe bet.

---

### Post by RobMcL on 2010-04-07
> **ssulaco said:**
> [http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1)

Quote from lovinglinux  Flash optimization

worked great for me..

Yup, worked like a charm. Thanks.

EDIT: Crap, nevermind, it only works sometimes. I'm gonna check some of the other solutions

---

### Post by J V on 2010-04-07
run us a uname -m please...

---

### Post by RobMcL on 2010-04-07
Lol, nevermind again! I got it working.

[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1)

```
Some people reported improvements doing this (original source):
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

```

---

### Post by Jazmac on 2010-04-17
> **RobMcL said:**
> Lol, nevermind again! I got it working.

[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1)

```
Some people reported improvements doing this (original source):
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

```

Great find RobMCL.  This fix worked for me as well.  I'm running Beta 2 Lucid Lynx and this youtube control issue was bugging me out.  Nothing worked but this seems to be the trick.  I'll keep testing and if it gets weird again, I'll post it.

-JazMac

---

