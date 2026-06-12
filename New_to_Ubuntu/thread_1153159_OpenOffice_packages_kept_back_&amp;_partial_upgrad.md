---
title: "OpenOffice packages kept back &amp; partial upgrade error"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by nachos99 on 2009-05-08
I'm running 8.04, and the following OpenOffice packages appear to be causing problems with updating.  

```
desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-style-human openoffice.org-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

``` 

And I'm get a partial update message on the update manager.

"Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
-A previous upgrade which didn't complete
-Problems with some of the installed software
-Unofficial software packages not provided by Ubuntu
-Normal changes of pre-lease version of Ubuntu"

when I run the partial update, it will say

"Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

This can be caused by:
*Upgrading to a pre-release version of Ubuntu
*Running the current pre-release version of Ubuntu
*Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later."

How should I go about having the OpenOffice packages not kept back in the apt-get upgrade?

Thanks in advance for any suggestions.

---

### Post by rburkartjo on 2009-05-08
nacho try this 

has this happened to you you open the update manager and all the updates dont  install if so open a terminal and type or paste this

sudo aptitude full-upgrade



then hit enter

---

### Post by nachos99 on 2009-05-08
thank you for the reply.

i basically chickened out and only did 
```
# aptitude safe-upgrade
```

of course, my problem is not yet solved.  
as for running
```
# aptitude full-upgrade
``` 
im afraid if i force the openoffice upgrade, that it might break.

is this something i dont need to worry about?

---

### Post by chezzo on 2009-05-10
hi, i'm having exactly the same problem - any progress?

---

### Post by delboy1 on 2009-05-10
I am also getting this error but I am on 8.10

---

### Post by Didius Falco on 2009-05-10
I'm wondering if you have installed Open Office 3.1...If so, that's what is causing it - it can't "update" packages that are newer than the ones it wants to apply.

If that is the case, open **Synaptic** and look for the Open Office packages that say version 3.1, select them, go to the **Package** menu and tick the **Lock Version** box.

Then quit out of **Synaptic** and run the **Update Manager** again - it will ignore those packages and you should be able to update normally.

Regards,

Didius

On Edit: that is my understanding at any rate, and I think that is correct. If not, someone will soon correct me on it. <G>

---

### Post by nachos99 on 2009-05-10
Didius Falco, thank you for your suggestion.
i seem to have 3.0.1 installed and the latest version synaptic shows is the 3.1 rc2.
does this mean i should still try marking lock version under the package menu? or am i having problems because it's trying to get the 3.1rc2?
thanks again for your help.

[IMG]http://img224.imageshack.us/img224/2333/screenshotsynapticpacka.png[/IMG]

---

### Post by Didius Falco on 2009-05-10
Have you added the Open Office server? You can download the upgrades to OO, then lock them after you have them if you still get the error.

Regards,

Didius

---

### Post by ubun_two on 2009-05-10
I had this issue with Partial Upgrade on my 9.04 machine.  Here is what I ended up doing.

1, I temporary disabled the ppa openoffice repository and refreshed.
2, I used Synaptic to remove OpenOffice 3.0.
3, I re-enabled the ppa repository and refreshed.
4, I installed OpenOffice 3.1 through Synaptic.

Maybe there are easier, cleaner way to do this, but i couldn'tfigure it out.

---

### Post by freeman2000 on 2009-05-10
I had the same problem as Nachos, and thought it was because I was running Karmic, but since Nachos isn't, then that can't be the problem.  Here's what worked for me.  

From Update Manager I got the message about Partial Upgrades, but couldn't download anything.  So I also went to Terminal and typed in "sudo apt-get upgrade".  It got me all the updates except for the new OO v3.1, so I then went to Synaptics, to "openoffice" and noticed that my installed items had green blocks, but also had stars within those green blocks, which meant that there was an upgrade.  So I clicked the one for "openoffice", and then clicked on "Mark for Upgrade".  Lo and behold, it marked all the dependencies and installed everything.  I now have OO v3.1 and all is running well.  

Hope that helps you.  Good luck.

---

### Post by chezzo on 2009-05-11
> **freeman2000 said:**
> I then went to Synaptics, to "openoffice" and noticed that my installed items had green blocks, but also had stars within those green blocks, which meant that there was an upgrade.  So I clicked the one for "openoffice", and then clicked on "Mark for Upgrade".  Lo and behold, it marked all the dependencies and installed everything.

Worked for me! Thanks so much :D

P.S. Thought it hadn't for a moment because the logo on the loading popup still said 3.0 but under Help/About it says 3.1.0 (although the logo there also says 3.0!). I assume the logo is like that because it's still in RC?

---

### Post by robc02 on 2009-05-11
This also worked for me - thanks.

Some packages were uninstalled- one was the english british language help package. When I try to reinstall it, Synaptic wants to uninstall most of Open Office (writer, calc etc)! 
When I click on "Help - Open Office.org help" I get a message telling me to install the English-US help package or the Locale equivalent. Well, I checked and the English - US package is installed. I tried uninstallling and reinstalling it. I presume that it is not being recognised because it is an older version - can anyone confim this.
I would quite like a working help package, does anyone know how I can get one?

---

### Post by nachos99 on 2009-05-11
did the upgrade to 3.1 and having similar (same?) problem.

when i open up language support under systems/admin, it will say
"The language support is not installed completely

Some translations or writing aids available for your chosen laguages are not installed yet.  Do you want to install them now?"   (my chosen language is english)

if I clikc install, it will install that but uninstall the openoffice. 

when i go to add/remove to install openoffice suite, it will not let me saying there's a conflict with something and to fix it in software manager.  

after putting in 
```
sudo apt-get remove language-support-en language-support-translations-en openoffice.org-help-en-gb openoffice.org-l10n-en-gb openoffice.org-l10n-en-za thunderbird-locale-en-gb
```
it will allow me to reinstall openoffice again.  got that from [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

any suggestions?

---

### Post by pigphish on 2009-05-12
> **freeman2000 said:**
> I had the same problem as Nachos, and thought it was because I was running Karmic, but since Nachos isn't, then that can't be the problem.  Here's what worked for me.  

From Update Manager I got the message about Partial Upgrades, but couldn't download anything.  So I also went to Terminal and typed in "sudo apt-get upgrade".  It got me all the updates except for the new OO v3.1, so I then went to Synaptics, to "openoffice" and noticed that my installed items had green blocks, but also had stars within those green blocks, which meant that there was an upgrade.  So I clicked the one for "openoffice", and then clicked on "Mark for Upgrade".  Lo and behold, it marked all the dependencies and installed everything.  I now have OO v3.1 and all is running well.  

Hope that helps you.  Good luck.

This worked for me. Also I should note I installed a pre-release kernel for the intel gfx problem which i assume why it was complaining.

---

### Post by robc02 on 2009-05-12
I have just followed the instructions on the softpedia link given by nachos99. It didn't install the help packages so I did this using Synaptic.
It made no difference at all! I still have no help package.

---

### Post by jamesobooth on 2009-05-13
> **freeman2000 said:**
> I had the same problem as Nachos, and thought it was because I was running Karmic, but since Nachos isn't, then that can't be the problem.  Here's what worked for me.  

From Update Manager I got the message about Partial Upgrades, but couldn't download anything.  So I also went to Terminal and typed in "sudo apt-get upgrade".  It got me all the updates except for the new OO v3.1, so I then went to Synaptics, to "openoffice" and noticed that my installed items had green blocks, but also had stars within those green blocks, which meant that there was an upgrade.  So I clicked the one for "openoffice", and then clicked on "Mark for Upgrade".  Lo and behold, it marked all the dependencies and installed everything.  I now have OO v3.1 and all is running well.  

Hope that helps you.  Good luck.


This worked for me!

---

