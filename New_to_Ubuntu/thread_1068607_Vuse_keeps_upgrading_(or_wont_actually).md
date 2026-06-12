---
title: "Vuse keeps upgrading (or wont actually)"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by quietbear on 2009-02-13
Just installed vuse (azerus) and ran it, I installed it from terminal...

Now when I run it, it just keeps saying it downloaded an upgrade and needs to restart, but when I restart it, it does the same thing again, and again, and again, and again, it wont stop.

So, either I am stupid and it is downloading like a million updates all individually for some dumb reason, or something is broken.

Help???

THanks

---

### Post by sanderj on 2009-02-13
(It's "Vuze", not "Vuse".)

Yep, same here.

Reason is probably this: the installed vuze/azureus is older than newest version, so update is downloaded, but can't be installed because you need root-rights for that.

Real solution: Ubuntu should update Vuze in it's repositories.

Possible workaround: Maybe there's an option in Vuze to NOT check for an update? Go to Options, and search for 'update'.

My own workaround: With Firefox, I downloaded the newest Vuze, installed it in my ~/vuze, and now run that version.

HTH

---

### Post by quietbear on 2009-02-13
So, I have tried to unistall Vuze through the add/remove, and it says:

> Cannot remove 'azureus'

One or more applications depend on azureus. To remove azureus and the dependent applications, use the Synaptic package manager.

So, I open the synaptic package manager, but I dont know which files to uninstall to get rid of it.  All I want to do is uninstall it so I can install the one that works from the web.  If I try to install it now, it runs into the old version and wont uninstall it for some reason.

So what do I have to do to get rid of it like I never installed it in the first place???  (That was a mistake)

---

### Post by sanderj on 2009-02-13
Have followed my advice in my post? So:

Have you searched for an option in Vuze not to check for an update?

Have you downloaded & installed Vuze in a home dir subdirectory ~/vuze? If so, have you run that version of Vuze?

---

### Post by apoth on 2009-03-19
> **sanderj said:**
> Reason is probably this: the installed vuze/azureus is older than newest version, so update is downloaded, but can't be installed because you need root-rights for that.

Garden path I'm afraid. Doesn't work as root either.

---

### Post by kdreimiller on 2009-03-19
ahhhh i remember having that same problem and could never get around it, so i dropped Vuze and went to deluge.  completely fits my needs without a lot of bells and whistles.

---

### Post by mkvnmtr on 2009-03-19
On another os I found vuze demanding that I update by torrent. I found no way to stop this. I also found it to be one of the the torrent clients that uses a lot of resources. I came to Ubuntu because I want to decide how I use my computer. Vuze didn{t want to give me that choice. It didn't take long for me to find another client on Ubuntu. I like Deluge but there are several good ones. No reason to give up my control to a app that wants to sell me stuff.

---

### Post by zaarin on 2009-03-25
I had this problem myself.

Vuze automatically downloaded an upgrade to itself, then told me it was going to have to restart to install the upgrade.  It restarted every 3 minutes but never installed the upgrade.

I deleted the .torrent file and the data for the update and the problem went away.

My torrents in Vuze move unbearably slow though (avg less than 30k/s) so I think I'll experiment with other programs.

---

### Post by spike_naples on 2009-03-27
I hate Vuze for Ubuntu.

I would recommend KTorrent or Deluge.

Vuze doesnt even uninstall correctly. To uninstall go to SPM and search for Azureus then choose to completely uninstall all packages to get rid of the remnants of Vuze.

---

### Post by teague johnson on 2009-04-09
I know this is an old thread but if any one is still reading I had the same issue as mentioned above. I got the 4.2v of vuze from the vuze site and extracted it to my desktop. I can open the extracted folder to find two execute files for 4.2v and when opened they run fine, but I have to leave the folder on my desktop as it is right now. Then I "completely removed" the old 3.1.1.0v using synaptic package manager but this version of vuze is still in my Applications>Accessories menu and when selected will fully open (after some setup prompts) the 3.1.1.0v with a different GUI than the original 3.1.1.0v I had gotten from running the application synaptic package manager.

I would like to know how to totally remove version 3.1.1.0 of vuze from my laptop (old dell inspiron 600m) and move/install this new package information from my desktop into its place.

If anyone has advice it would be awesome to here it.

thanks!


(ubuntu 8.10)

---

### Post by MeTylerDurden on 2009-05-13
Heyo, Vuze is giving plenty of upgrade headbangers, does 9.04 version have azureus and vuze or just azureus in synaptic package manager. If there was a way to take vuze out of the ibex package would be nice - not to patronize vuze, but just to say azureus worked just fine and with transmission there is no way to adjust upload speed without digging into the preferences.. i LIKE AZUREUS because you can adjust speeds easily and get alot of other brilliant stuff in options

---

### Post by MeTylerDurden on 2009-05-15
[http://wiki.vuze.com/index.php/Azureus_2_/_3_and_Vuze#Use_the_UI_Switcher](http://wiki.vuze.com/index.php/Azureus_2_/_3_and_Vuze#Use_the_UI_Switcher)




this may help in finding the look you want, change sometimes comes at price and you have to take some time to remedy things.. my hat is still off to Vuze

---

