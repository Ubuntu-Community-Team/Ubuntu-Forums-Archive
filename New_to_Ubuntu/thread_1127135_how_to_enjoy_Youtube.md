---
title: "how to enjoy Youtube?"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by dan1973 on 2009-04-16
Have freshly installed Xubuntu and want to be able to access youtube videos. What do i need to do? and how do I do it? Many thanks in advance.

---

### Post by Penguin Guy on 2009-04-16
Go onto the site and it should bring up a bar saying that you need to download stuff to view the site properly - click on the bar and download everything it tells you to. Simple!

---

### Post by freak42 on 2009-04-16
you need the flash plugin:

```
sudo apt-get install adobe-flashplugin

```

---

### Post by dan1973 on 2009-04-16
When i feed in the command line, i get the message:

E: Couldn't find package adobe-flashplugin

What could be the problem?

I also tried through the adobe site, i downloaded 'flash player 10 for linux (.deb) However when package tried to install the following message was relayed:

Error: Wrong architecture 'i386'. What does this mean and what needs to be done?

Many thanks in advance,

---

### Post by LowSky on 2009-04-16
```
sudo apt-get install xubuntu-restricted-extras
```

Or under applications go to add/remove, look for xubuntu resrticed extras, you will have to change the top tab to all availible software.

This package will give you Flash and java, and mp3 suport and Microsft type fonts, and a couple of other things too. You should be able to visit nearly any website without an issue after this

---

### Post by LostMagix on 2009-04-16
> **dan1973 said:**
> When i feed in the command line, i get the message:

E: Couldn't find package adobe-flashplugin

What could be the problem?

I also tried through the adobe site, i downloaded 'flash player 10 for linux (.deb) However when package tried to install the following message was relayed:

Error: Wrong architecture 'i386'. What does this mean and what needs to be done?

Many thanks in advance,

You got the wrong package, you need a the 64bit not the i386 package

---

### Post by rockerphil on 2009-04-16
ok, the reason you weren't able to fetch the package with apt-get is because more than likely you don't have all the repositories enabled. this is pretty easy to do. simply run this code:

```
sudo nano /etc/apt/sources.list
```

then simply delete the # from any line that begins with either "deb" or "deb-src" once that's done hit Ctrl+X then Y to save. then run:

```
sudo apt-get install adobe-flashplugin
```

again. once that's done simply restart any running browsers and you should be able to watch YouTube videos to your heart's content. hope this helps,

Phil

edit: if it's unable to locate the "adobe-flashplugin" package you should try:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by dan1973 on 2009-04-16
thanks to all for their help, matter resolved, Rockerphill's advice sealed the deal.

---

### Post by stchman on 2009-04-16
> **freak42 said:**
> you need the flash plugin:

```
sudo apt-get install adobe-flashplugin

```

No such package.

Install the following:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by billgoldberg on 2009-04-16
Some of you guys should really get your "stuff" together before giving advise.

The guy is asking how to install the flash plugin for crying out loud, someone even had him diving into the cli and editing his sources.list file with a cli text editor.

I can understand giving an apt-get command, but nano? 

What are you thinking?

> 
Open up synaptic, search for flash.

Install the package "flashplugin-nonfree".

Or if you prefer using a terminal, open one and use
```

sudo apt-get install flashplugin-nonfree
```


4 simple lines, it's not that hard.

---

### Post by oldos2er on 2009-04-16
> **dan1973 said:**
> 
I also tried through the adobe site, i downloaded 'flash player 10 for linux (.deb) However when package tried to install the following message was relayed:

Error: Wrong architecture 'i386'. What does this mean and what needs to be done?

 For 64-bit Flash, see [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

