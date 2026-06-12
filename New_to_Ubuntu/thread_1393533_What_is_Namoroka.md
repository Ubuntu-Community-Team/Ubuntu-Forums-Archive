---
title: "What is Namoroka?"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by bwsmith25 on 2010-01-29
Why does my version of Firefox now say "Namoroka?"

I've tried uninstalling it and reinstalling it, and it still comes up as "Namoroka Web Browser" - how do I get it back to Firefox?

Please be gentle, I am as "noob" as noob gets.

If it helps, I'm using Ubuntu 9.10

---

### Post by blur xc on 2010-01-29
> **bwsmith25 said:**
> Why does my version of Firefox now say "Namoroka?"

I've tried uninstalling it and reinstalling it, and it still comes up as "Namoroka Web Browser" - how do I get it back to Firefox?

Please be gentle, I am as "noob" as noob gets.

If it helps, I'm using Ubuntu 9.10

It's firefox 3.6, pre prealease version.  FF3.5 was known as Shiretoko.  It's just Mozilla code names...

Ignore it and pretend it says Firefox.  Maybe you can edit the menu/panel launchers, etc., to show the old ff logo and change the name to ff, never tried myself.

BM

---

### Post by Merk42 on 2010-01-29
> **blur xc said:**
> It's firefox 3.6, pre prealease version.  FF3.5 was known as Shiretoko.  It's just Mozilla code names...

Ignore it and pretend it says Firefox.  Maybe you can edit the menu/panel launchers, etc., to show the old ff logo and change the name to ff, never tried myself.

BM

Unfortunately some websites do browser sniffing and don't recognize Namoroka.  See [this bug](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211) for examples of during the 3.0 - 3.5 switch

bwsmith525, if you want Firefox 3.6 in Karmic I recommend the stable PPA.  So uninstall what you have then add this repo ppa:mozillateam/firefox-stable

You can do so by going into a terminal and typing:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
Then run the update manager as usual, or via terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by fromthehill on 2010-01-29
websites can see what browser you use by looking up your user-agent 
most websites don't use that. but you can temporarily change it with [this plugin]("http://chrispederick.com/work/user-agent-switcher/")

you'll need to add the firefox user agent yourself

I used this one

description: firefox 3.0
user agent:  Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9) Gecko/2008052906 Firefox/3.0
app code name: Mozilla
app name: Netscape
app version: 5.0 (X11; en-US)
platform: Linux i686

you can also use this plugin to access IE-only websites

---

### Post by amarendra on 2010-02-20
thanks Merk42: 
sudo add-apt-repository ppa:mozillateam/firefox-stable is fine but what about a repository that updates all or most of the packages to it's latest stable releases? On a slow connection it's very difficult for me to update all the repositries as they take a lot of time. However, that's better than just sitting with Ubuntu default versions which are horribly old. Just want to figure out all such repositories that will help me get the latest stable releases. May be vendor wise: like mozilla-stable instead of firefox-stable etc.

---

### Post by mcduck on 2010-02-20
> **amarendra said:**
> thanks Merk42: 
sudo add-apt-repository ppa:mozillateam/firefox-stable is fine but what about a repository that updates all or most of the packages to it's latest stable releases? On a slow connection it's very difficult for me to update all the repositries as they take a lot of time. However, that's better than just sitting with Ubuntu default versions which are horribly old. Just want to figure out all such repositories that will help me get the latest stable releases. May be vendor wise: like mozilla-stable instead of firefox-stable etc.
There is no such thing (or, put in other way, upgradign to latest Ubuntu release is close as youa re goung to ever get to that while running Ubuntu).

If you want to have latest versions of all your programs all the time you should be using some Linux distribution with rolling releases. Ubuntu is built with more focus on stability than latest program versions which is why the package versions in repositories are frozen to the ones that were available during the development of that release.

---

### Post by bug67 on 2010-02-20
If you want the *current* Firefox release from Mozilla, why not just enable the Ubuntuzilla repo?

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by amarendra on 2010-02-20
@mcduck: yeah. anyway, i will try to workaround this using PPAs for some packages where latest version does matter like firefox and pidgin. 
well, I am not sure if I am right but Ubuntu should at least have an option for rolling releases or users should have an option while installing becasue this lame in my opinion-not having the latest packages. 

@bug67: thnaks but once I tried ubuntuzilla and didn't find it very useful. maybe i had committed some mistakes while installing but it would rather go with firefox-stable ppa. 

just hoping Ubuntu changes it's stance or have a repository for this purpose or really backports the backports repositiry. i feel frustrated when i see my friends using firefox 3.6 on their PCs. I would have switched to some other rolling release distro but unfortunately I don't like any of them.

---

### Post by mcduck on 2010-02-20
> **amarendra said:**
> @mcduck: yeah. anyway, i will try to workaround this using PPAs for some packages where latest version does matter like firefox and pidgin. 
well, I am not sure if I am right but Ubuntu should at least have an option for rolling releases or users should have an option while installing becasue this lame in my opinion-not having the latest packages. 

@bug67: thnaks but once I tried ubuntuzilla and didn't find it very useful. maybe i had committed some mistakes while installing but it would rather go with firefox-stable ppa. 

just hoping Ubuntu changes it's stance or have a repository for this purpose or really backports the backports repositiry. i feel frustrated when i see my friends using firefox 3.6 on their PCs. I would have switched to some other rolling release distro but unfortunately I don't like any of them.

You shouldn't hold your breath waiting for Ubuntu to change such integral part of the distro's philoshophy. That's quite unlikely to ever happen on the actual Ubuntu releases. There is no way how one distribution could serve every purpose, and there are already quite many distributions that provide rolling releases. Ubuntu targets for ease of use and stability which is almost impossible to acchieve with rolling releases (unless there's enormous testing team availavble to test the new packages all the time).

Like I said, if rolling releases is what you want you need to use a distro that uses rolling releases. Even offering such thing as user-selectable option would require lot more resources for package maintenance (versus actual distribution development), and make providing any level of support considerably harder.

The idea of having a rolling-release, permanently unstable, development version of Ubuntu is somehting that has been around for quite awhile, but there has never been enough resources or need for such thing to actually make it happen. See Gumpy Groundhog in Launchpad: [https://blueprints.launchpad.net/launchpad-foundations/+spec/grumpy-groundhog]("https://blueprints.launchpad.net/launchpad-foundations/+spec/grumpy-groundhog")

---

### Post by RedRat on 2010-02-20
Speaking of Firefox 3.6, my 8.04 just downloaded and update my old FF 3.0 to 3.6. Very nice. But here is my question: in my toolbar atop my Desktop, the FF icon changed to some strange looking terminal icon. I right-clicked on the icon and chose Properties and it had a "chose icon" button. When I clicked on that it took me to a \usr\share\pixmaps but there was no typical FF icon and they were all png files.  Where is that typical FF icon stored????

The only icon options are png files when I am presented with options to select an icon form \usr\share\icons\pixmaps.

How about all the others in \usr\share\icons?

---

### Post by JackRock on 2010-02-20
> **RedRat said:**
> Speaking of Firefox 3.6, my 8.04 just downloaded and update my old FF 3.0 to 3.6. Very nice. But here is my question: in my toolbar atop my Desktop, the FF icon changed to some strange looking terminal icon. I right-clicked on the icon and chose Properties and it had a "chose icon" button. When I clicked on that it took me to a \usr\share\pixmaps but there was no typical FF icon and they were all png files.?


It's the same reason the name changed.  As it's not an OFFICIAL release, they cannot use the standard Firefox icon for Shiretoko/Namoroka.  So they use the blue globe instead.

---

### Post by RedRat on 2010-02-20
> **JackRock said:**
> It's the same reason the name changed.  As it's not an OFFICIAL release, they cannot use the standard Firefox icon for Shiretoko/Namoroka.  So they use the blue globe instead.
Well this update came through Synaptic and not directly from Firefox, so I must assume that is an official release. I think it would be odd if the version in Synaptic were not an official release since it tends to take quite a long time for them to download. FF 3.5 never appeared in the Hardy repos. 

still where are the icons??? Why only png?

---

### Post by mcduck on 2010-02-20
> **RedRat said:**
> Well this update came through Synaptic and not directly from Firefox, so I must assume that is an official release. I think it would be odd if the version in Synaptic were not an official release since it tends to take quite a long time for them to download. FF 3.5 never appeared in the Hardy repos. 

still where are the icons??? Why only png?

You *must* have added some extra repository for it, as only the current development release of Ubuntu (Lucid) has Firefox 3.6 in it's repositories. Every other release has older versions, and it's not going to be updated.

Karmic has FF3.5, and Jaunty, Intrepid & Hardy still have FF3.0
[http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=all&section=all]("http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=all&section=all")

The reason why the Firefox package you have installed (where ever you got it from) is not branded and uses the code name instead of "Firefox" is that such packages don't usually *replace* the official Firefox version that came with your Ubuntu release, they are installed *alongside* it. And having two browsers with same name would be a bit problematic, so the unofficial version is left unbranded.

---

### Post by JackRock on 2010-02-20
Agreed.  There are ways to add "unstable" PPAs to the your computer's system, allowing updates to non-official releases.  I have 3.6 Namoroka on my system.  And I, like you, received it from the Synaptic.

---

### Post by RedRat on 2010-02-20
> **mcduck said:**
> You *must* have added some extra repository for it, as only the current development release of Ubuntu (Lucid) has Firefox 3.6 in it's repositories. Every other release has older versions, and it's not going to be updated.

Karmic has FF3.5, and Jaunty, Intrepid & Hardy still have FF3.0
[http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=all&section=all)

The reason why the Firefox package you have installed (where ever you got it from) is not branded and uses the code name instead of "Firefox" is that such packages don't usually *replace* the official Firefox version that came with your Ubuntu release, they are installed *alongside* it. And having two browsers with same name would be a bit problematic, so the unofficial version is left unbranded.

I have not added any repos! In point of fact I have been looking for FF 3.5 to appear in the repos! It has not shown up. This update appeared yesterday for the first time. It was merely listed as a FF update, I did not even know it was for 3.6. Here is the "About Firefox" display.

There is no other FF installed only this one. It appears to be in the Firefox directory.

---

### Post by mcduck on 2010-02-20
> **RedRat said:**
> I have not added any repos! In point of fact I have been looking for FF 3.5 to appear in the repos! It has not shown up. This update appeared yesterday for the first time. It was merely listed as a FF update, I did not even know it was for 3.6. Here is the "About Firefox" display.

There is no other FF installed only this one. It appears to be in the Firefox directory.

The problem with that is that it simply can't be coming from the official repositories, since there is no such package in the official repositories.

Not to mention the Ubutnu policy of packagw versions not updating after the version freeze which happens during the developmnet, before release. You must have some additional repository or something, there is no way the default Firefox version would be updated to 3.6 on any Ubuntu version other than Lucid.

Could you run "sudo apt-get update" and "apt-cache show firefox" and post the outputs here?

(Other than where your Firefox is coming from, thes ame answer still applies that the package is unbranded to avoid it mixing with the version that your Ubuntu release is supposed to have.)

---

### Post by Georgia boy on 2010-02-20
How did you get the update? I'm running Hardy 8.04 and my version of FF is 3.0.18. I didn't get an automatic update to the 3.5 or 3.6 FF.

Just curious.


Tom

---

### Post by RedRat on 2010-02-20
> **mcduck said:**
> The problem with that is that it simply can't be coming from the official repositories, since there is no such package in the official repositories.

Not to mention the Ubutnu policy of packagw versions not updating after the version freeze which happens during the developmnet, before release. You must have some additional repository or something, there is no way the default Firefox version would be updated to 3.6 on any Ubuntu version other than Lucid.

Could you run "sudo apt-get update" and "apt-cache show firefox" and post the outputs here?

(Other than where your Firefox is coming from, thes ame answer still applies that the package is unbranded to avoid it mixing with the version that your Ubuntu release is supposed to have.)

Here they are as text file attachments.

---

### Post by Tholley on 2010-02-20
> **RedRat said:**
> Speaking of Firefox 3.6, my 8.04 just downloaded and update my old FF 3.0 to 3.6. Very nice. But here is my question: in my toolbar atop my Desktop, the FF icon changed to some strange looking terminal icon. I right-clicked on the icon and chose Properties and it had a "chose icon" button. When I clicked on that it took me to a \usr\share\pixmaps but there was no typical FF icon and they were all png files.  Where is that typical FF icon stored????

The only icon options are png files when I am presented with options to select an icon form \usr\share\icons\pixmaps.

How about all the others in \usr\share\icons?

I'm not sure if you have figured it out yet, but the FFox seems to be gone with 3.6, but if you goto your applications/internet you will see it now has a blue globe that says Namoroka Web Browser. I just grabbed it and put it up in the toolbar.

---

### Post by JackRock on 2010-02-20
> **Tholley said:**
> I'm not sure if you have figured it out yet, but the FFox seems to be gone with 3.6,

It's not gone.  Just renamed and re-iconed until the next stable version is released.

---

### Post by mcduck on 2010-02-21
If I remeber right some older Ubuntu releases hd a separate, unbranded Firefox 3.5 packages, I suppose you must have installed that one. But I'm absolutely sure that the normal default Firefox version has not updated in any Ubtunu release, and definitely hasn't changed to unbranded version.

Also you *do* have several additional repositories there so you might want to check what repositories you have added yourself..

---

### Post by ikt on 2010-02-21
[QUOTE=McDuck]You shouldn't hold your breath waiting for Ubuntu to change such integral part of the distro's philoshophy.[/QUOTE]

interesting...

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

> Mozilla moved to a monthly security update cycle early in 2009; next step planned is to stop doing stable release branches for any distro-relevant amount of time. For instance, they consider to release firefox 3.6 as a minor update to firefox 3.5 and want to a 3-4 month cycle for such minor-major version upgrades. Also it happens more frequently now that they bump reqtuirements on system libs like cairo and sqlite3 in minor version upgrades.

This is in line with what is planned by chromium and it's unfeasible to try to do our own stable release branch maintenance as this would require far more resources than we can get at any point in the future.

Instead we should prepare for what is coming and ensure that we can follow major-minor version upgrades in a timely fashion.

---

