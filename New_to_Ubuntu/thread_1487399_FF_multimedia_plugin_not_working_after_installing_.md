---
title: "FF multimedia plugin not working after installing ClamTK"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by llumi on 2010-05-18
Hello, 

I'm running Lucid and Firefox 3.6.3. After installing ClamAV and ClamTK the Virus Scanner decided it wanted to be the default program with which to open videos online. I'd much prefer them to be opened with the Firefox plugin, even if they wouldn't be virus scanned this way. I installed the Virus Scanner mainly for files occasionally imported from Windows machines. 

So I uninstalled both ClamAV and the GUI, but now FF won't use the totem or the VLC plugins anymore. It either gives me a box saying:"You have chosen to open... This is a Windows Media Video. Would you like to save this file" Or alternatively, it'll default to the xine plugin, which isn't the plugin for wmv or mpeg files, as far as FF preferences are concerned. In the preferences, the default plugin is VLC one...

Both totem and VLC plugins are installed, FF recognises both and says they're up to date. Medibuntu and w32codecs are installed and both plugins used to work correctly. 

I tried to re-install the totem plugin, but no help. Tried to google for solutions, but only came up with missing plugins and how to install them.

Now what? Thanks for any ideas.

---

### Post by -humanaut- on 2010-05-19
You should open a terminal and type: locate clam
then if theres any files left over try purging them with sudo apt-get purge clamav or you can try sudo rm /clam/files.

---

### Post by llumi on 2010-05-19
> **-humanaut- said:**
> You should open a terminal and type: locate clam
then if theres any files left over try purging them with sudo apt-get purge clamav or you can try sudo rm /clam/files.

Thanks for the tip. There were a bunch of files found with "locate clam". Purged both clamav and clamtk. Afterwards the same bunch of files is still found with *locate clam*, but the /clam/files folder can't be destroyed with rm. The terminal only reports *No such file or directory*.

The plugins still not working.

---

### Post by lovinglinux on 2010-05-19
My machine doesn't see an anti-virus for ages. Anyway, if it is causing problems why don't you simple change anti-virus? Try BitDefender. It's really nice.

About the plugins, I wouldn't recommend having multiple plugins for the same type of content installed. VLC player is awesome, but in terms of plugin, I believe gecko-mediaplayer is a much better option.

---

### Post by llumi on 2010-05-19
> **lovinglinux said:**
> My machine doesn't see an anti-virus for ages. Anyway, if it is causing problems why don't you simple change anti-virus? Try BitDefender. It's really nice.

About the plugins, I wouldn't recommend having multiple plugins for the same type of content installed. VLC player is awesome, but in terms of plugin, I believe gecko-mediaplayer is a much better option.

I might try BitDefender for Antivirus, but the problem is apparently first getting rid of ClamAV. 

As for the plugins, you might be right that multiple ones are confusing. Right now most of them are not really working (the only one for multimedia that seems to work is the xine plugin). I disabled the VLC one, but no change in FF behavior.

---

### Post by -humanaut- on 2010-05-19
Alright, sometimes for reasons unknowin to me I had major trouble getting rid of openoffice.org on A Xubuntu machine but if you open synaptic type clam and check "Mark for Complete removal" that sometimes works if rm and apt-get fail.

---

