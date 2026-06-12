---
title: "XML Parsing Error when Downgrading from Firefox 4.0"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by ninjasinloaf on 2011-05-12
Hi.  I'm having all sorts of trouble getting rid of Firefox 4.  I did an update earlier and I deliberately de-selected all the Mozilla-related updates, but Firefox 4 still got installed (I'm definitely unclear on how that happened).  I have tried to uninstall/reinstall; I have tried to 'force version' through Synaptic and then ppa-purge the mozillateam ppa (says package is not found); I do not want to install the old version from the Mozilla website to my home directory.

I've done all kinds of purging and I've followed just about all the instructions I can google.  Here's what's happening:

*) Firefox 4 works fine when I reinstall it.
*) When I downgrade to 3.6 and then try to start Firefox, I get the following message on a yellow background:

XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 31, Column 1:<window id="main-window"

I am using Lucid.  I really don't want to switch browsers because I really like Firefox (3.6, that is) and this has been such an unseemly hassle.

Thank you for your help.

---

### Post by Joe of loath on 2011-05-12
What's the problem with Firefox 4 exactly? You can make the two look alike, all the addons are compatible, and FF4 is faster and lighter.

---

### Post by lovinglinux on 2011-05-12
> **Joe of loath said:**
> What's the problem with Firefox 4 exactly? You can make the two look alike, all the addons are compatible, and FF4 is faster and lighter.

+1

Please post the reasons why you don't like Firefox 4 and maybe we can help with that.

Also please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt

```

---

### Post by ninjasinloaf on 2011-05-12
Thank you for your swift responses.  I appreciate you taking the time to help.

Frankly, I don't care for the look, the feel, or the behavior of Firefox 4 (which don't really do it for me -- it's a lot like Chrome and I am immensely uncomfortable using Chrome too).  For example, the right-click menu is all shuffled around when I click on a link; I'm unhhappy with the fewer buttons and their placement; I don't like where the tabs and such are; it's keeping all my history in the drop-down menu even though I told it not to in the 'options' menu. I'm unhappy with the lack of the status bar; my favorite sites bar is missing; I don't like the add-ons manager, the UI. And, it's actually running a lot slower (plus there's a super-annoying popup that shows up when it is waiting for a page to load or when I hover over a link; it used to have very cute little fishies that counted out and filled up when the page was loading); I don't like the animation that happens when I open a new tab (windows animations are one of the things I intensely dislike in Windows and on the Macs in my office).

I don't really think these things are 'neat' enough to give up my comfort and familiarity.  I understand that the software would like to move into the future, but I was happy with how it was and I would like to change it back. I suppose if I could get the look and functionality back to exactly how it was, or near enough that I knew no difference, I'd be fine, but mostly, I am frustrated that I can't 'uninstall' an update that I purposefully tried to avoid and didn't want in the first place. :)  Where did I go wrong?

I hope I don't sound combative, but what does 'faster and lighter' mean?

As a side note: why is there still Wine stuff in the sources list? I thought I uninstalled/deleted that those a long time ago.


Again, thank you for helping. Here are the contents of the firefox-report.txt:

Ubuntu Architecture

Linux MeowMixing 2.6.32-31-generic-pae #61-Ubuntu SMP Fri Apr 8 20:00:13 UTC 2011 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-globalmenu                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

aelmahmoudy-tl2009-karmic.list
aelmahmoudy-tl2009-karmic.list.distUpgrade
aelmahmoudy-tl2009-karmic.list.save
banshee-team-ppa-lucid.list
banshee-team-ppa-lucid.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
getdeb.list
getdeb.list.bck
glasen-intel-driver-lucid.list
glasen-intel-driver-lucid.list.save
gnuzilla-team-ppa-lucid.list
gnuzilla-team-ppa-lucid.list.save
google-chrome.list.save
google-talkplugin.list
google-talkplugin.list.save
jacob-evo230-lucid.list
jacob-evo230-lucid.list.save
jonoomph-openshot-edge-karmic.list
jonoomph-openshot-edge-karmic.list.distUpgrade
jonoomph-openshot-edge-karmic.list.save
mendeleydesktop.list
mendeleydesktop.list.save
opera.list.save
ricotz-ppa-lucid.list
ricotz-ppa-lucid.list.save
tomboy-packagers-stable-lucid.list
tomboy-packagers-stable-lucid.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.save
ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.save
winehq.list
winehq.list.distUpgrade
winehq.list.save

---

### Post by lovinglinux on 2011-05-12
> **ninjasinloaf said:**
> For example, the right-click menu is all shuffled around when I click on a link;

Use [Menu Editor]("https://addons.mozilla.org/en-US/firefox/addon/710/") to hide menu items and reorder them to your liking.

> **ninjasinloaf said:**
> I'm unhhappy with the fewer buttons and their placement;

Which buttons do you need? You can move almost any button anywhere. Just right-click on a toolbar, then select "Customize", then drag the buttons around.

> **ninjasinloaf said:**
> I don't like where the tabs and such are; 

You can change the tab position, by right-clicking the toolbar and toggling "Tabs on top". You can also have more tab position options with [Tree Style Tab]("https://addons.mozilla.org/en-US/firefox/addon/5890/").

> **ninjasinloaf said:**
> it's keeping all my history in the drop-down menu even though I told it not to in the 'options' menu.

Please post a screenshot of your Privacy options.

> **ninjasinloaf said:**
> I'm unhappy with the lack of the status bar; my favorite sites bar is missing;

There is an Add-on Bar now, which is much better, since you can move things like any other toolbar. Right-click on any toolbar, select "Add-on Bar" to display it. They have kept part of the status bar for compatibility reasons, so if you have extensions that add icons to the status bar, they will still show in the add-ons bar.

If you want to regain several old status bar functionalities, use [Status-4-Evar]("https://addons.mozilla.org/en-US/firefox/addon/235283/").

> **ninjasinloaf said:**
> I don't like the add-ons manager, the UI. And, it's actually running a lot slower

It is slower, but most likely these problems will be sorted out in future releases.

About the UI, you can use [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108/") to modify it. There are [several style sheets]("http://userstyles.org/styles/browse/all/Add-ons%20Manager") that change the add-ons manager layout.

> **ninjasinloaf said:**
> (plus there's a super-annoying popup that shows up when it is waiting for a page to load or when I hover over a link; it used to have very cute little fishies that counted out and filled up when the page was loading);

Use [Status-4-Evar]("https://addons.mozilla.org/en-US/firefox/addon/235283/") to hide that and display link targets and loading progress information in the add-ons bar.

> **ninjasinloaf said:**
> I don't like the animation that happens when I open a new tab (windows animations are one of the things I intensely dislike in Windows and on the Macs in my office).


Which animation? Are you referring to the tab groups?

> **ninjasinloaf said:**
> Again, thank you for helping. Here are the contents of the firefox-report.txt:

I don't see any Firefox ppa installed, but I don't know several repositories you are using. So do this:

```
sudo apt-get remove firefox
sudo apt-get update
sudo apt-get install firefox
```

If you still get Firefox 4 after that, then post the result of the following command:

```
apt-cache policy firefox
```

---

### Post by ninjasinloaf on 2011-05-12
Thank you for your suggestions.  I may have to spend time modifying because the remove/update/reinstall sequence did not work.  

Here's the output from apt-cache policy firefox:

```
firefox:
  Installed: 4.0.1+build1+nobinonly-0ubuntu0.10.04.0~ricotz1
  Candidate: 4.0.1+build1+nobinonly-0ubuntu0.10.04.0~ricotz1
  Version table:
 *** 4.0.1+build1+nobinonly-0ubuntu0.10.04.0~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/ppa/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     3.6.17+build3+nobinonly-0ubuntu0.10.04.1 0
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
     3.6.3+nobinonly-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
```

---

### Post by ninjasinloaf on 2011-05-12
Oh, and by 'animations' I meant when I open a new tab or close a tab they fly and whizz around.

---

### Post by lovinglinux on 2011-05-12
> **ninjasinloaf said:**
> Thank you for your suggestions.  I may have to spend time modifying because the remove/update/reinstall sequence did not work.  

Here's the output from apt-cache policy firefox:

```
firefox:
  Installed: 4.0.1+build1+nobinonly-0ubuntu0.10.04.0~ricotz1
  Candidate: 4.0.1+build1+nobinonly-0ubuntu0.10.04.0~ricotz1
  Version table:
 *** 4.0.1+build1+nobinonly-0ubuntu0.10.04.0~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/ppa/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     3.6.17+build3+nobinonly-0ubuntu0.10.04.1 0
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
     3.6.3+nobinonly-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
```

The "problem" is the ricotz ppa, which is updating Firefox to 4.0.1. I guess you probably need it for other software, so instead of disabling it, open Synaptic Package Manager, search for firefox, select the firefox package then click "Package >> Force version" and select version 3.6.x.

If you don't need the ricotz ppa for other software, then disable it, update, remove Firefox and install again.

---

### Post by lovinglinux on 2011-05-12
> **ninjasinloaf said:**
> Oh, and by 'animations' I meant when I open a new tab or close a tab they fly and whizz around.

That's not a Firefox feature. That's an Ubuntu animation I guess, more precisely Compiz or perhaps you have an add-on that do that. Anyway, that doesn't happen here.

Take a look at the video:

[IMG]http://www5.picturepush.com/photo/a/5643608/img/5643608.gif[/IMG]

---

### Post by ninjasinloaf on 2011-05-12
I fixed the animations by changing browser.tabs.animate to False in the about:config page.


I can't imagine that PPA repository was important -- when I googled it it was just fore firefox and inkscape and some other things I've never heard of.  So it was certainly the culprit!

I got 3.6 going again (thankyouthankyouthankyou!) but now I can't seem to put all my preferences back in. It doesn't like when I just copy/paste the folder.  And when I try to open the profile manager (in usr/lib/firefox) as another set of instructions showed me, I get nothing.

So much heartache! If I do decide to go back and modify Firefox 4 at some point, will I be able to change all the download manager stuff too? I don't care for any of the popups.

Thank you gain for your help.  I appreciate your time today.

---

### Post by lovinglinux on 2011-05-12
> **ninjasinloaf said:**
> I fixed the animations by changing browser.tabs.animate to False in the about:config page.

Indeed that turns off the animation, but it is so discrete that I can barely see the difference. Do yours animate more than the video above?

> **ninjasinloaf said:**
> 
I can't imagine that PPA repository was important -- when I googled it it was just fore firefox and inkscape and some other things I've never heard of.  So it was certainly the culprit!

I got 3.6 going again (thankyouthankyouthankyou!) but now I can't seem to put all my preferences back in. It doesn't like when I just copy/paste the folder.  And when I try to open the profile manager (in usr/lib/firefox) as another set of instructions showed me, I get nothing.

So much heartache! If I do decide to go back and modify Firefox 4 at some point, will I be able to change all the download manager stuff too? I don't care for any of the popups.

Thank you gain for your help.  I appreciate your time today.

To open the profile manager, CLOSE Firefox and run the following in a  terminal:

```
firefox -P
```

Which folder are you trying to copy?

What do you mean by "all download manager stuff"?

---

### Post by ninjasinloaf on 2011-05-12
Yes, I noticed those animations.  Even the ones in your video were quite dramatic to me. :)

When downloading in Firefox 4, a small popup would appear in the lower right hand corner of the screen to tell me what was being downloaded.  Also, at another point when it was asking me confirmation to allow or disallow permission (I forget what for, I've clicked a lot of things today) a rather unsightly popup came in the top center of the window with a drop-down box for options of allow or don't allow.  I did not fancy that at all.

I found the backup copy of my bookmarks and imported that through the bookmarks folder.  Then I found prefs.js and typed them all into about:config one-by-one to get all my settings back, but the firefox -P is good to know.  I was following some instructions that were sending me to usr/lib/firefox and there wasn't anything there. 

I can't figure out how to insert an image in here without it being a URL, but for the Firefox 4 privacy settings, I had gone to Edit->Preferences->Privacy and set the first dropdown box to "Never remember history" and the second to "When using the location bar, suggest: Nothing" and then did "clear all current history".  It still retained recently visited links in the History menu. Was there something else I should've set?

---

### Post by lovinglinux on 2011-05-12
> **ninjasinloaf said:**
> I found the backup copy of my bookmarks and imported that through the bookmarks folder.  Then I found prefs.js and typed them all into about:config one-by-one to get all my settings back, but the firefox -P is good to know.  I was following some instructions that were sending me to usr/lib/firefox and there wasn't anything there.

You don't need to type all prefs manually, just copy prefs.js to the new profile.

**> **ninjasinloaf said:**
> I can't figure out how to insert an image in here without it being a URL, but for the Firefox 4 privacy settings, I had gone to Edit->Preferences->Privacy and set the first dropdown box to "Never remember history" and the second to "When using the location bar, suggest: Nothing" and then did "clear all current history".  It still retained recently visited links in the History menu. Was there something else I should've set?**

You are doing it right. It shouldn't be saving any bookmarks in History. 

Try to delete the file permissions.sqlite from your profile and check if that solves the problem. You need to close Firefox before deleting profile files.

---

### Post by ninjasinloaf on 2011-05-12
If I could mark this thread as double-solved I would.  Thank you for your help today.

---

### Post by lovinglinux on 2011-05-13
> **ninjasinloaf said:**
> If I could mark this thread as double-solved I would.  Thank you for your help today.

You are welcome.

---

### Post by romulusnr on 2011-05-27
A thousand Internets. I downgraded from 4 back to 3.6 via removing the MZ repo and then using Synaptic "force version" back to the Canonical stable. But I still had this problem. Apparently I needed to remove it first -- which I was afraid to do because I didn't want to risk losing my profile data. But all was well. Thanks for the solution!

I just have one bone to pick with something that was said:

> **Joe of loath said:**
> What's the problem with Firefox 4 exactly? You can make the two look alike, all the addons are compatible, and FF4 is faster and lighter.

All the addons are compatible? Huh? What? Pretty much all my addons were disabled after FF4 upgrade, and no updated versions available. Since I use these addons in my work, I depend on them heavily. That's why I needed to downgrade. So I don't know where you got that from but it's not my experience.

---

### Post by Joe of loath on 2011-05-27
The only addon I've found that isn't compatible is the Ubuntu modifications pack in 10.04 and 10.10. If anything isn't compatible, it usually means the author has abandoned it, so you'll need to find a replacement at some point.

---

### Post by romulusnr on 2011-05-31
> **Joe of loath said:**
> If anything isn't compatible, it usually means the author has abandoned it, so you'll need to find a replacement at some point.

That's not at all true.

You know when the latest version of Putty was made? 2007. Yet it's still the standard for Windows SSH clients.

FF4 was released in March. It's not even June.

I'm tired of the forced obsolescence provided by new FF major versions completely nuking my browser work environment. Every single time...

It'd be like installing a new version of Ubuntu and having it completely nuke your desktop and panel configuration.

(Oh, wait...! That **did** happen! :P)

---

### Post by Joe of loath on 2011-05-31
It's not exactly forced, if you change the way the browser works, you can't expect everything to carry on working properly.

---

