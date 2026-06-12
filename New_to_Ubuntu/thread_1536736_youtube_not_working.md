---
title: "youtube not working"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by H43N15 on 2010-07-22
ive done a ton of searching and ive tried countless commands, installed the restricted software, installed a number of adobe flash and plugins but nothin to get youtube to f ing work....do i need to remove the ones i did install to make the right one work????? can someone just post the link to the teminal command or post it here to make a youtube video work for ubuntu 10.04 desktop gnome???? pretty please????? love you ubuntu ninjas......thanks!

---

### Post by snowpine on 2010-07-22
The correct command is:

```
sudo apt-get install flashplugin-installer
```

Sorry, but since I do not know the "countless commands" you have already tried, I don't know how to undo them. ;)

---

### Post by mike555 on 2010-07-22
"i give up "  is not conducive to getting help , perhaps more info on what you have tried ...

---

### Post by H43N15 on 2010-07-22
> **snowpine said:**
> The correct command is:

```
sudo apt-get install flashplugin-installer
```Sorry, but since I do not know the "countless commands" you have already tried, I don't know how to undo them. ;)
that was the 1st one i tried......still nothing

---

### Post by snowpine on 2010-07-22
Type:

```
about:plugins
```

in your Firefox address bar, and it will tell you whether or not Flash is installed (and which version).

---

### Post by Paqman on 2010-07-22
> **H43N15 said:**
> that was the 1st one i tried......still nothing

Can you try the command again in a terminal and post the output. That command really should work.

---

### Post by Rubi1200 on 2010-07-22
> **mike555 said:**
> "i give up "  is not conducive to getting help , perhaps more info on what you have tried ...

Agreed!

Also, what version of Ubuntu are you using and do have any addons enabled like NoScript?

Take a look here as well:

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

[http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

---

### Post by H43N15 on 2010-07-22
it said it sucessfully installed, but know the youtube says 'error occred' instead of 'need to install.."

---

### Post by H43N15 on 2010-07-22
it says its installed on the about page

---

### Post by Darkness Des on 2010-07-22
"There's an addon for that."

I got flash to work but I am rather sick of said resource hungry application, so you can make all youtube videos work with the built in MPlayer by using this addon.
[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

---

### Post by QIII on 2010-07-22
Do you have swfdec or gnash installed?  They conflict with Flash.

Also, see here:

[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)

Look especially at Flash-Aid. It will clean up the crap and get the right stuff set up.

He may bite me, but I would recommend against the 64-bit version since it is no longer supported by Adobe and has security holes.  But maybe he will be nice if I say that he is the Ubuntu god when it comes to all things Firefox.

---

### Post by RJARRRPCGP on 2010-07-22
> **H43N15 said:**
>  youtube says 'error occred' 

YouTube had a bug that caused you to randomly get that error message.

---

### Post by Rubi1200 on 2010-07-22
Try clearing out the cache and cookies in Firefox, then give it another go.

---

### Post by Paqman on 2010-07-22
Uninstall absolutely everything related to Flash, delete your Firefox profile (located at ~/.mozilla) and try again with the correct command.

---

### Post by H43N15 on 2010-07-22
ok i ran that add on thing Mplayer and its still not working, trying flash aid now, working on this really old slow @$$ computer makes it more difficult

---

### Post by corrytonapple on 2010-07-22
You have an issue with flash. Are you on 64-bit? Here is a link to lovinglinux's how to: [Link]("http://ubuntuforums.org/showthread.php?t=1491268").Try his plug-in, I use it and it works.

---

### Post by H43N15 on 2010-07-22
im 32 bit

---

### Post by corrytonapple on 2010-07-22
That's good, 64-bit has issues with flash.

---

### Post by H43N15 on 2010-07-22
maybe i should start fresh..... how do i clear everything out from adbe and the run the original command?
and how do i remove that 
MPlayer thing

---

### Post by H43N15 on 2010-07-23
update... that mplayer worked once i downloaded that no script......thanks for all the help u guys

---

