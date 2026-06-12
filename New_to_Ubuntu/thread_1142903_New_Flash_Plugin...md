---
title: "New Flash Plugin.. ?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Muninn_EMS on 2009-04-29
Just reformatted and installed Ubuntu 9.04, only real problem now is any flash player is ******. For example, Zero Punctuation flash movies just cause tons of lag and never do anything. 
 
I'm using an Adobe SWF plugin apparenlty... can't seem to get rid of it. I seem to remember using apt-get to get some new player plugins, but can't remember what they would be. 
 

Any idea on the problem?

---

### Post by kansasnoob on 2009-04-29
Go to System > Administration > Synaptic Package Manager and click on Search (not Quick search) and type flash. The only 2 packages that you want installed in that field are ubuntu-restricted-extras and adobe-flashplugin (which will be installed by installing the restricted-extras).

Any other packages (gnash, swfdec-*, etc.) should be marked for complete removal (which is the same as running "purge remove"). Then click on apply and when it's done running restart Firefox.

I've also found that Flashblock is very helpful as an Add-on in Firefox (it replaces flash objects with a button) as it reduces the demand on system resources when visiting flash heavy sites. But the version in the repos is very outdated, you can get the new version simply by going to Tools > Add-ons > Get add-ons in Firefox and searching for, then installing the new Flashblock. You'll be prompted to restart Firefox again.

---

### Post by Muninn_EMS on 2009-04-29
Ah, thank you! I had to do a quick search for 'swf' because it didn't come up under a standard search for 'flash,' but after I removed it everything is working smoothly!

I'll check out flashblocker too, thanks!

---

