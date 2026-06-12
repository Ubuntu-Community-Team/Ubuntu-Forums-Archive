---
title: "adobe flash player"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by sarah90 on 2009-07-29
hey, so i dont claim to be computer literate and the guy that put linux onto my computer is no longer talking to me, so i need help.
basically i'm trying to access a website that is telling me i'm trying to install flash on an unsupported system.  and when i go to the flash download page, i have four choices.  i would like to know which one i install.  i am running ubuntu eee, dont member which version and my choices are YUM, .tar.gz, .rmp, and .deb for ubuntu 8.04+.
any help would be appreciated.

---

### Post by philinux on 2009-07-29
Welcome to the forums.

Click the restrictedformats link and medibuntu below.

Any queries post back.

---

### Post by pmlxuser on 2009-07-29
if ubuntu choose the .deb less hassles.

---

### Post by sarah90 on 2009-07-29
i tried the .deb version and i still cannot use the site.

---

### Post by halitech on 2009-07-29
are you running the 32bit version or the 64bit version of Ubuntu?

---

### Post by sarah90 on 2009-07-29
> **halitech said:**
> are you running the 32bit version or the 64bit version of Ubuntu?

...how would i find that out?

---

### Post by halitech on 2009-07-29
open a terminal and paste the output of
```
uname -m
```

---

### Post by sarah90 on 2009-07-29
> **halitech said:**
> open a terminal and paste the output of
```
uname -m
```
i686

---

### Post by MelDJ on 2009-07-29
go to synaptic and search for flashplugin-nonfree. tick to install it

---

### Post by upapilot on 2009-07-29
that means you have the 64 bit version.....

---

### Post by Bölvaður on 2009-07-29
can you post the url for the website and check out if you can see videos on youtube.


if both of them do not work then click this link to install flash player again [INSTALL FLASH ]("apt:flashplugin-nonfree")(this is not from a website, but the ubuntu software repositories which is a safe place)

It will ask you for your password and then it will automatically download and install flash.
After that you will have to close firefox or what ever browser you are using and then open it again. Make sure there is no instance of firefox running before opening the website again.

---

### Post by Bölvaður on 2009-07-29
> **upapilot said:**
> that means you have the 64 bit version.....

no it doesnt!!!!

i686 is a newer version of i386 and those are both x86 which is 32 bit


this is what you are looking for.
```
$ uname -m
x86_64

```

the problem is not about 32 vs 64 bits.. unless if s/he has the 64 version... which I doubt... and if s/he does then going by my advice here above will solve it.

---

### Post by upapilot on 2009-07-29
or perhaps you could try 
sudo apt-get flashplugin-nonfree ?

---

### Post by sarah90 on 2009-07-29
> **Bölvaður said:**
> can you post the url for the website and check out if you can see videos on youtube.


if both of them do not work then click this link to install flash player again [INSTALL FLASH ]("apt:flashplugin-nonfree")(this is not from a website, but the ubuntu software repositories which is a safe place)

It will ask you for your password and then it will automatically download and install flash.
After that you will have to close firefox or what ever browser you are using and then open it again. Make sure there is no instance of firefox running before opening the website again.

i'm am trying to use this site "www.whotune.com" and i can watch videos on youtube.

---

### Post by MelDJ on 2009-07-29
steps:
1.click system then synaptic package manager. 
2. enter your password and click on search
3. type flashplugin-nonfree and press find
4. Right click the package which reads flashplugin-nonfree and press mark for installation.
5. Press apply and wait for it to finish downloading
6. After it's finish, close synaptic and restart firefox
7. Go to youtube or wherever and enjoy :popcorn:

---

### Post by upapilot on 2009-07-29
so you say YouTube works eh? then perhaps something is wrong with the site you are trying to watch the video on

---

### Post by sarah90 on 2009-07-29
> **MelDJ said:**
> go to synaptic and search for flashplugin-nonfree. tick to install it
it is installed.

---

### Post by upapilot on 2009-07-29
> **MelDJ said:**
> steps:
1.click system then synaptic package manager. 
2. enter your password and click on search
3. type flashplugin-nonfree and press find
4. Right click the package which reads flashplugin-nonfree and press mark for installation.
5. Press apply and wait for it to finish downloading
6. After it's finish, close synaptic and restart firefox
7. Go to youtube or wherever and enjoy :popcorn:
true but the fact is: if she indeed didnt have flash, YouTube wouldnt work either! but it works so we know there is some compatibility error with the wesite

---

### Post by Bölvaður on 2009-07-29
> **sarah90 said:**
> i'm am trying to use this site "www.whotune.com" and i can watch videos on youtube.

this website works perfectly, I could listen to their radio even though I didnt log in I would assume everything works.

you may need to uninstall the flash from adobe's website. But first check if this works

(THIS IS NOT NEEDED ANY MORE, but for everyone telling everyone to use synaptic.... just use the apt plugin for firefox.. much easier)
[Click here to install flash]("apt:flashplugin-nonfree")

> **sarah90 said:**
> it is installed.

---

### Post by sarah90 on 2009-07-29
> **upapilot said:**
> so you say YouTube works eh? then perhaps something is wrong with the site you are trying to watch the video on
it is possible, i suppose.  my mate is on it, which is the reason i am trying to use it, he wants me to see something.  so im not sure why it would work for him and not me...

---

### Post by MelDJ on 2009-07-29
> **upapilot said:**
> so you say YouTube works eh? then perhaps something is wrong with the site you are trying to watch the video on

ya. it must be something wrong with the website. i tried going to the website too. and got the same pop up.

---

### Post by philinux on 2009-07-29
> **sarah90 said:**
> i'm am trying to use this site "www.whotune.com" and i can watch videos on youtube.

Have you got adblock or flashblock addons running on firefox?

---

### Post by sarah90 on 2009-07-29
> **philinux said:**
> Have you got adblock or flashblock addons running on firefox?
um...i dont think so.

---

### Post by MelDJ on 2009-07-29
have you ever gone to this website in windows? Did it show you the same message?

---

### Post by upapilot on 2009-07-29
Try to unistall than install once more and see if that works

---

### Post by sarah90 on 2009-07-29
> **MelDJ said:**
> have you ever gone to this website in windows? Did it show you the same message?
no i haven't...i may try that.

---

### Post by MelDJ on 2009-07-29
i use flashblock and it said that the flash played on the screen is named* playerProductinstall.swf* . Seems fishy to me

---

### Post by upapilot on 2009-07-29
> **MelDJ said:**
> i use flashblock and say that the flash played on the screen is named* playerProductinstall.swf* . Seems fishy to me

indeed! maybe the site sort of uninstalls the plugin? ill scan it with some internet antivirus and post the result here soon

---

### Post by philinux on 2009-07-29
Site plays just fine here.

---

### Post by upapilot on 2009-07-29
uh NOTHING....the website clean

---

### Post by MelDJ on 2009-07-29
???? i could not access it anyway i tried:confused:

---

### Post by Bölvaður on 2009-07-29
make sure you got flash player 10.

it might not be in the standard repos if you are running "old" version of ubuntu


In firefox go to Tools &#8594; Add-ons &#8594; Plugins
scroll down to Shockwave Flash and tell us what version you have.

mine is Shockwave Flash 10.0 r22

---

### Post by sarah90 on 2009-07-29
> **Bölvaður said:**
> make sure you got flash player 10.

it might not be in the standard repos if you are running "old" version of ubuntu


In firefox go to Tools &#8594; Add-ons &#8594; Plugins
scroll down to Shockwave Flash and tell us what version you have.

mine is Shockwave Flash 10.0 r22
yeah, i have already discovered this.  i only have shockwave 9.

---

### Post by Bölvaður on 2009-07-29
> **sarah90 said:**
> yeah, i have already discovered this.  i only have shockwave 9.
Im not 100% sure what is the best way to go up to 10, but I suspect you are running old version of ubuntu and that's why you are getting old version of flash (newer versions arent added to the official software repositories)

Let's begin by deleting the older flash you have got.

Press ALT+F2 and type/copy paste : gksu nautilus /usr/lib
enter your password
look for the firefox you are using (it should have about 10 directories and about 10-11 other items)

delete flash plugin (shift+delete to delete it intsantly)

/usr/lib/firefox-3.0.12/plugins/libflashplayer.so  &#8592; this is the file I would have to delete

then restart firefox to make sure it is no longer there.



next install the new one

[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29&g=](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29&g=)

---

### Post by philinux on 2009-07-29
Click the backports link below. You could well get flash your upgraded automagically by enabling backports.

---

### Post by sarah90 on 2009-07-29
ok, i am using firefox 3.0.12 also, but when i go into my plugins file as per your instructions, its empty.

---

### Post by mikewhatever on 2009-07-29
> **philinux said:**
> Click the backports link below. You could well get flash your upgraded automagically by enabling backports.

I am afraid it's a bad idea, I mean, why add backports just to upgrade flash to version 10? Wouldn't a bunch of other things be upgraded too? It's like killing flies with a cannon. :) Why not simply remove the existing version of flash and install the latest one?

Sarah90, are you running Ubuntu 8.04? It seems likely, since I can't think of another reason for flash 9 being installed. You can check with the following command: **cat /etc/lsb-release**.
I'd simply advise removing the installed version of flash and installing the latest one using the .deb file from adobe. Close your browser while doing that.

---

### Post by philinux on 2009-07-29
Backports are just fine. 
> This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.

---

### Post by Bölvaður on 2009-07-29
> **sarah90 said:**
> ok, i am using firefox 3.0.12 also, but when i go into my plugins file as per your instructions, its empty.

hmm ok well I guess you can open the terminal (applications &#8594; accessories &#8594; terminal) and paste this (ctrl + shift + v)

sudo apt-get purge flashplugin-nonfree


there also might be other places where the plugin might be located

/usr/lib/firefox-addons/plugins
/usr/lib/xulrunner/plugins (probably not)

---

### Post by MelDJ on 2009-07-29
> **philinux said:**
> Click the backports link below. You could well get flash your upgraded automagically by enabling backports.

did this..and now i dont have shockwave at all in firefox! I must reinstall flashplugin-nonfree now....:(

---

