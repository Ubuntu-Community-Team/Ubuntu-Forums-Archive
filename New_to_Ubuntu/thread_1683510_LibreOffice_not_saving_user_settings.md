---
title: "LibreOffice not saving user settings"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Proshka on 2011-02-07
Hi there,

I changed (and saved) some user settings (documents path, fonts, writing aids options, etc.) but every time I start LibreOffice those modifications are replaced by default options so I have to change them over and over again. I am using Maverick. Any suggestions?

Proshka

---

### Post by roffik on 2011-02-11
I had the same problem, but I think I managed to get rid of it by renaming the folder [FONT="Courier New"].openoffice.org[/FONT] (which sits in your home folder) - you can as well delete the folder. Later I found that LibreOffice uses its own folder [FONT="Courier New"].libreoffice[/FONT]. I dont't know how it is connected, but it seems it helped.

---

### Post by Proshka on 2011-02-11
I deleted it too but the problem persists. I found a reference in another forum regarding a file (.libreoffice/3/user/registrymodifications.xcu) where the user settings are stored. The file continues to point out to OpenOffice in the same paths I would expect LibreOffice even though OO has been completely removed from the system before installing LO.

---

### Post by Proshka on 2011-02-11
By deleting the file mentioned above I managed to get rid of the problem.

---

### Post by Proshka on 2011-02-13
My last post was too optimistic. I had to turn off and reboot the system before properly exiting LibreOffice and when I opened Writer I had the same problem again. However I noticed that if I delete the file .libreoffice/3/user/registrymodifications.xcu before making changes in user settings those changes persist when I open Writer again but dissapear when there is a LO crash or system failure.

---

### Post by Guilden_NL on 2011-02-13
Thanks for the well defined issues and steps you've taken.

I'll play around with permissions and see if I can crash LO and if the settings stick.

Great stuff!  Thanks!

---

### Post by ZaphodFJ on 2011-02-15
Does the above problem include spellcheck settings?  My dictionary keeps going AWOL and I'm hoping someone has a solution already posted.

---

### Post by ZaphodFJ on 2011-02-18
One solution, based on advice from: [http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/](http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/) is this:

Do a full uninstall.

        - Install LibO

Then install
* hunspell-dictionary-*/myspell-dictionary-*: Hunspell/Myspell dictionaries for use with LibreOffice
* libreoffice-l10n-*: UI interface translation
* libreoffice-help-*: User help
* libreoffice-thesaurus-*: Thesauri for the use with LibreOffice
* libreoffice-hyphenation-*: Hyphenation patterns for LibreOffice
* libreoffice-gtk: Gtk UI Plugin, GNOME File Picker support,

Problem has gone away.  It also helps to go to tools/preferences and make sure you are telling LibO to use your locale.  My problem was a US installation, in the UK - and it couldn't find the UK dictionary.

---

### Post by colferma on 2011-02-21
> **ZaphodFJ said:**
> One solution, based on advice from: [http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/](http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/) is this:

Do a full uninstall.

        

I'm having the same trouble with LibreOffice; it doesn't remember the changes I make to the templates. I originally installed it directly over OpenOffice, and when this problem came up I tried a few steps: removing the .openoffice directory, removing the mxu (or some such) configuration file, purging openoffice. All to no avail.

Would you mind explaining how to go about a full uninstallation of libreoffice before the reinstall?

Thanks,

M

---

### Post by larusalka on 2011-03-06
I was having the same problem, but finally got rid of it by removing OpenOffice residual configurations via Synaptic Package Manager. To do that, you just have to select 'Not installed (residual config)' on the left panel, search for openoffice, then select all the resulting packages, mark for complete removal and finally apply.
Worked for me.

---

### Post by Guilden_NL on 2011-03-07
> **larusalka said:**
> I was having the same problem, but finally got rid of it by removing OpenOffice residual configurations via Synaptic Package Manager. To do that, you just have to select 'Not installed (residual config)' on the left panel, search for openoffice, then select all the resulting packages, mark for complete removal and finally apply.
Worked for me.

I haven't had a chance to go back to this until now.  Your post made me slap my forehead and question why I didn't think of this myself.

Ubuntu forums are valuable regardless of how long you you've been running Linux.

Great point and I just confirmed that it corrected the problem. I haven't crashed Libre, but hopefully that won't happen anyway!

Thanks again!

---

### Post by Morgen on 2011-03-07
> **larusalka said:**
> I was having the same problem, but finally got rid of it by removing OpenOffice residual configurations via Synaptic Package Manager. To do that, you just have to select 'Not installed (residual config)' on the left panel, search for openoffice, then select all the resulting packages, mark for complete removal and finally apply.
Worked for me.

I tried this but unfortunately it did not resolve the issue for me. Settings are gone after a reboot. Wish I could roll back to LO 3.3.0. Wasn't a problem before.

---

### Post by larusalka on 2011-03-07
Well, in my case settings do stick after a reboot, but unfortunately they were gone after I manged to crash LibreOffice (freaking DOC files ](*,)).
So, is it definitively a bug? :confused:

---

### Post by Morgen on 2011-03-07
This is definitely a bug. It is a known issue that was supposed to be fixed with LO 3.3.1, but instead was made worse. Seems to affect more people now than before. See the following post:

[https://bugs.freedesktop.org/show_bug.cgi?id=33915](https://bugs.freedesktop.org/show_bug.cgi?id=33915)

---

### Post by Morgen on 2011-03-08
As a temporary fix until this gets resolved I have made a backup copy of the entire ~/.libreoffice folder and every time that I reboot my computer I replace the .libreoffice folder with my back up. There is probably another solution with more finesse but this works for now. At least I don't have to do the changes manually.

---

