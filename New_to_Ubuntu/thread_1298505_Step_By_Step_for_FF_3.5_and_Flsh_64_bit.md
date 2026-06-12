---
title: "Step By Step for FF 3.5 and Flsh 64 bit?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-10-22
i downloaded firefox 3.5 over my old ff and no flash so i get the 64 bit flash puging put the .so in the pluging folder under firefox and it still dosent work these are the steps i used for my old firefox on a 64bit linux why wont it work now?

---

### Post by tarps87 on 2009-10-23
Why don't you just install Firefox and flash from the repos?

---

### Post by R3fr4cti0n on 2009-10-24
64 bit

---

### Post by steveneddy on 2009-10-24
> **R3fr4cti0n said:**
> i downloaded firefox 3.5 over my old ff and no flash so i get the 64 bit flash **puging** put the .so in the **pluging** folder under firefox and it still **dosent** work these are the steps i used for my old firefox on a 64bit linux why wont it work now?

The spelling and grammar aside, I mean really, punctuation, capitalization and spelling can't be that hard.
/rant

This link has been on the forums for what seems like forever:

[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

I believe the **plugin** goes in these folders:

**/usr/lib/mozilla/plugins**

 **/usr/lib/firefox-addons/plugins**

Install the **plugin** in these folders, restart and see what happens.

---

### Post by tarps87 on 2009-10-25
> **tarps87 said:**
> Why don't you just install Firefox and flash from the repos?

> **R3fr4cti0n said:**
> 64 bit

I don't understand your answer, the 64 bit packages are in the repos too

---

### Post by b0b138 on 2009-10-25
First run this command. It will remove anything that might be installed ```
sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash nspluginwrapper swfdec-mozilla
```

Then download the plugin here [http://labs.adobe.com/downloads/flashplayer10.htmlsudo](http://labs.adobe.com/downloads/flashplayer10.htmlsudo) Extract the file and copy it to

/usr/lib/mozilla/plugins/
or
/home/your_user/.mozilla/plugins/

The one in the repos is 32bit and runs with nspluginwrapper. 64bit is still in alpha

---

### Post by oldos2er on 2009-10-25
> **tarps87 said:**
> I don't understand your answer, the 64 bit packages are in the repos too

 64-bit flash is not in the repos.

---

### Post by tarps87 on 2009-10-27
> **oldos2er said:**
> 64-bit flash is not in the repos.

Sorry, you are correct, I assumed the package for the 64 bit architecture was 64 bit compiled.

---

