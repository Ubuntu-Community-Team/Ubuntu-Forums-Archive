---
title: "Upgrades, fresh installs and the /home partition"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by M1ke on 2010-01-08
I currently have two machines running Ubuntu 9.10, and both are set up with a separate partition for /home which I understand stores all my configurations and settings. The thinking behind this was that in future, should I need a fresh installation I could cut down on a lot of tweaking and customisation time post-install, but I don't know exactly what would be preserved and what wouldn't be.
 
Obviously all the files I place in /home and it's subdirectories would still be there unless I formatted the partition, but what about preferences and settings for the OS itself? Things like keyboard and mouse sensitivities, window behaviour, my personalised settings for installed apps and so on? Or even the apps themselves? Am I correct in thinking each app I install is buried somewhere in / rather than /home?
 
Basically - precisely what is preserved by keeping my /home partition as it is following a clean installation of Ubuntu?
 
It's thanks to this community that I'm getting on so well with the monumental shift from Windows. Thank you all!

---

### Post by audiomick on 2010-01-08
Hallo.
I don't know exactly everything, but I have re-mounted my home a couple of times, and haven't noticed anything go missing.
Apart from my files, I have retained
my desktop configuration (background, theme, icons in Taskbar ect.)
Evolution config inc. contacts, calendar, e-mail account setup etc.
Indexing in F-Spot for my photos

You can see what is in home by selecting "show hidden files" in the view menu in Nautilus (the file manager). A lot of the stuff there has fairly easily understandable file names, so you can guess what it has to do with.

The apps themselves are in / somewhere, but the config files that are set as user preferences are generally in /home.

---

### Post by happyhamster on 2010-01-08
> **M1ke said:**
> Obviously all the files I place in /home and it's subdirectories would still be there unless I formatted the partition, but what about preferences and settings for the OS itself? Things like keyboard and mouse sensitivities, window behaviour, my personalised settings for installed apps and so on?
All of those settings should be stored in /home.

> 
 Or even the apps themselves? Am I correct in thinking each app I install is buried somewhere in / rather than /home?
Yes. The binaries, libraries are somewhere in /, but the user configuration files aren't. In other words: when doing a re-install (and formatting / only), all apps were gone, but their configurations remain (in /home). That also means it's handy if you have a list of the non-default apps you manually installed, so you can install those again on the fresh system. They should install without touching the already present configuration files.

>  
Basically - precisely what is preserved by keeping my /home partition as it is following a clean installation of Ubuntu?
/home keeps configuration and user stuff. If you want to take a look: open your home folder with nautilus (the default file-browser) and press Ctrl-h to be able to see hidden files (the stuff starting with a .).

That said, it's possible that some app does store some configuration stuff in / instead of /home, and it's also possible that some app will overwrite configuration files (in /home) when re-installing, so the transition might not be perfect.

Note that root system settings will be completely gone. So any tweaks on stuff as grub (bootparameters for example) will have to be re-done manually.

Good luck.

---

### Post by M1ke on 2010-01-08
> **happyhamster said:**
> ...In other words: when doing a re-install (and formatting / only), all apps were gone, but their configurations remain (in /home). That also means it's handy if you have a list of the non-default apps you manually installed, so you can install those again on the fresh system. They should install without touching the already present configuration files.
 
So if I'm reading this correctly, in theory some freshly-installed non-default apps might even pick up their old settings from /home? That would provide great piece of mind if/when it comes to upgrade time in April.
 
> **audiomick said:**
> Apart from my files, I have retained
my desktop configuration (background, theme, icons in Taskbar ect.)
Evolution config inc. contacts, calendar, e-mail account setup etc.
Indexing in F-Spot for my photos
 
Excellent, that's very reassuring! It's taken me a while to get my panels looking the way I'd like to keep them, functional but clutter-free.
 
Thank you for your helpful responses :D

---

### Post by happyhamster on 2010-01-08
> **M1ke said:**
> So if I'm reading this correctly, in theory some freshly-installed non-default apps might even pick up their old settings from /home?
Yes. :)

---

### Post by MattM11 on 2010-01-08
"Save Markings" in Synaptic allows you to save a list of what's been installed. Just pop it in your home folder, then, after re-installing, load the file in Synaptic and it'll reinstall everything. (Except third-party software, of course).

---

### Post by audiomick on 2010-01-08
> in theory some freshly-installed non-default apps might even pick up their old settings from /home

I have a starter in my task bar for opensync. After a re-install, it disappered. After I had re-installed all the opensync stuff, it re-appeared all by itself. Gotta like that!;)

---

### Post by M1ke on 2010-01-08
> **MattM11 said:**
> "Save Markings" in Synaptic allows you to save a list of what's been installed. Just pop it in your home folder, then, after re-installing, load the file in Synaptic and it'll reinstall everything. (Except third-party software, of course).
 
How wonderfully intuitive! Again, thank you everyone! Marking this thread solved, then :)

---

