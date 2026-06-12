---
title: "Gstreamer vs. restricted extras"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by tonsil on 2010-04-26
I was just glancing at Ubuntu software center. Which one is better to install; gstreamer codecs or restricted extras?

---

### Post by arrrghhh on 2010-04-26
Depends on what you're trying to acheive.  On a desktop install, I'd say the restricted extras, just because you get ALL the recommended restricted extras (flash, java, etc) in addition to the ability to play all the stuff related to the gstreamer codecs (aac, mp3, etc).

So if you're going minimal and don't mind cherry picking packages, you can go the gstreamer route.

For ease, restricted-extras.

---

### Post by 3rdalbum on 2010-04-26
Restricted Extras will install the gstreamer codecs as well as a lot of other useful things.

---

### Post by WinterRain on 2010-04-26
As far as I can recall, restricted extras does not give you gstreamer-ugly, or w32codecs. I always do (once I get the medibuntu repos)
```
sudo apt-get install non-free-codecs
```
which will basically give you everything.

---

### Post by tekkidd on 2010-04-26
I install gstreemer plugins. never got the restricted extras to work

---

### Post by fishtopher on 2011-03-20
Are the restricted extras just a wrapper for the gstreamer codecs?  I'm presently having a hard time knowing which codecs have been installed and which havn't.  On my system its not a big deal, but this is my brothers computer and I'd like him to be all set up to watch or listen to whatever he happens to come across without having to call me to figure it out.

Is there a good way to manage the codecs one has installed?

---

### Post by mcduck on 2011-03-20
> **fishtopher said:**
> Are the restricted extras just a wrapper for the gstreamer codecs?  I'm presently having a hard time knowing which codecs have been installed and which havn't.  On my system its not a big deal, but this is my brothers computer and I'd like him to be all set up to watch or listen to whatever he happens to come across without having to call me to figure it out.

Is there a good way to manage the codecs one has installed?

No, the ubuntu-restricted-extras isn't just gstreamer codecs, but also install other restricted stuff that people commonly want. Like unrar and Microsoft's fonts.

There's also the ubuntu-restricted-addons -metapackage which adds some gstreamer codecs together with Flash and JAva plugins.

What kind of "codec management" are you hoping to do? Synaptic Package Manager will allow you to list the available & installed codec packages. (just like any other packages, of course)

---

### Post by Old_Man_Unix on 2011-03-20
> **fishtopher said:**
> Are the restricted extras just a wrapper for the gstreamer codecs?  I'm presently having a hard time knowing which codecs have been installed and which havn't.  On my system its not a big deal, but this is my brothers computer and I'd like him to be all set up to watch or listen to whatever he happens to come across without having to call me to figure it out.


"[FONT=Courier New]*buntu-restricted-extras[/FONT]" are metapackages for your distribution.  What that means, very briefly, is that it is a package that installs other packages.  Among the packages it installs are a number of codecs.

About the only generally used codec that isn't installed automatically by  the "[FONT=Courier New]*buntu-restricted-extras[/FONT]"   is "libdvdcss"  for decrypting DVDs.  It's in there, but you have to run a separate command (one time only) in the terminal to get it going. 

BTW, the "[FONT=Courier New]*buntu-restricted-extras[/FONT]" do install codecs from the "ugly set".

> **fishtopher said:**
>   Is there a good way to manage the codecs one has installed?

Easiest way in Ubuntu - open the Ubuntu Software Center;  Click on "installed software",; note the codec packages that have been installed - the name generally starts with "gstreamer"; select the package; click on "More Info" button.

AFAIK, there is no independent  "codec-manager" application as such.  However, there is a running process that detects missing codecs if they are called for and offers to install them.

---

### Post by Frogs Hair on 2011-03-20
Having had trouble downloading the URE package more than once I installed Gstreamer plugins . When all is said and done I don't appear to be missing anything.

---

