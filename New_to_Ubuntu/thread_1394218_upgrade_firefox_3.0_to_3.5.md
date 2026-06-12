---
title: "upgrade firefox 3.0 to 3.5"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by 16sinker on 2010-01-30
I recently did a clean install of Ubuntu 9.04, which comes with Firefox 3.0. I wanted to upgrade to Firefox 3.5, so I used synaptic package manager to install 3.5 and apparently it was installed, but my computer is still using 3.0. Both versions, 3.0 and 3.5 are installed in Synaptic, so my question is, how do I switch to 3.5. I've tried removing 3.0 in Synaptic, but am left with no browser. Can someone help?

---

### Post by pastalavista on 2010-01-30
> **16sinker said:**
> I recently did a clean install of Ubuntu 9.04, which comes with Firefox 3.0. I wanted to upgrade to Firefox 3.5, so I used synaptic package manager to install 3.5 and apparently it was installed, but my computer is still using 3.0. Both versions, 3.0 and 3.5 are installed in Synaptic, so my question is, how do I switch to 3.5. I've tried removing 3.0 in Synaptic, but am left with no browser. Can someone help?when you uninstalled 3.0, you still had 3.5 but it is called by its build name, Shiretoko. To update Your 3.0 browser, the only way I know is [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page").

---

### Post by lovinglinux on 2010-01-30
You need to create a launcher or update the existing one with the command below:

```
firefox-3.5
```

The current launcher uses...

```
firefox %u
```

...which points to the default version.

I recommend that you read [this](http://lovinglinux.megabyet.net/?page_id=220#Method-#4-1-Details-3). It explains what the installation method you have chosen.

---

### Post by 16sinker on 2010-01-30
> **lovinglinux said:**
> You need to create a launcher or update the existing one with the command below:

```
firefox-3.5
```

The current launcher uses...

```
firefox %u
```

...which points to the default version.

I recommend that you read [this](http://lovinglinux.megabyet.net/?page_id=220#Method-#4-1-Details-3). It explains what the installation method you have chosen.

Thanks, I'll call this solved. I had forgotten about the additional launcher for Shiretoko in applications>internet. Now I can use both 3.0 and 3.5. Do you know if 3.6 is available for Jaunty, and if so would it replace 3.0 or 3.5?

---

### Post by skymera on 2010-01-30
I suggest using this:
[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

### Post by lovinglinux on 2010-01-30
> **16sinker said:**
> Thanks, I'll call this solved. I had forgotten about the additional launcher for Shiretoko in applications>internet. Now I can use both 3.0 and 3.5. Do you know if 3.6 is available for Jaunty, and if so would it replace 3.0 or 3.5?

If you add the ubuntu-mozilla-daily PPA, it should update your firefox-3.5 package to 3.6.

---

### Post by skymera on 2010-01-30
> **lovinglinux said:**
> If you add the ubuntu-mozilla-daily PPA, it should update your firefox-3.5 package to 3.6.

The Mozilla Daily PPA will upgrade him to 3.6.x prerelease.

The Mozilla Stable Channel PPA will upgrade him to 3.6 stable and so on.

---

### Post by Norm24 on 2010-01-30
Also you can upgrade to 3.6 thru Ubuntzilla.

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

---

### Post by lovinglinux on 2010-01-30
> **Norm24 said:**
> Also you can upgrade to 3.6 thru Ubuntzilla.

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

Ubuntuzilla is not upgrade, is a side-by-side installation of a separate version.

---

### Post by 16sinker on 2010-01-30
> **lovinglinux said:**
> If you add the ubuntu-mozilla-daily PPA, it should update your firefox-3.5 package to 3.6.

Please. Some help with commands for adding the ubuntu-mozilla-daily PPA would be greatly appreciated.

---

### Post by tom.swartz07 on 2010-01-30
> **16sinker said:**
> Please. Some help with commands for adding the ubuntu-mozilla-daily PPA would be greatly appreciated.

Sure!

If youre using karmic, just open a terminal and type
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

If youre in jaunty, its a bit more involved:

Step 1: Copy the first line from the apt sources.list entries section of the PPA overview page. For example:

```
deb http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
```

Step 2: On your Ubuntu computer, open System > Administration > Software Sources.

Step 3: Click the Third Party Software tab.


Step 4: Click the Add button.

Step 5: Paste the line you copied in step 1 and click the Add Source button.

Step 6: Now copy the second line from the apt sources.list entries section of the PPA overview page and paste it in just as you did in steps 4 and 5.

When prompted, reload the software sources information. Don't worry if you see a warning about unverified software sources; we're going to fix that next.

Telling Ubuntu how to authenticate the PPA

Now Ubuntu knows about the PPA. It also needs to know how to check the software hasn't been tampered with since Launchpad built it.

Note: This is not an endorsement of any of the software in PPAs. You must make sure you trust the PPA owner before installing their software.

Step 1: On the PPA's overview page you'll see the PPA's OpenPGP key id. It'll look something like this: 1024/12345678. Copy it, or make a note of, the portion after the slash, e.g: 12345678.

Step 2: Open your terminal and enter:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
```

Step 3: Finally, tell Ubuntu to re-load the details of each software archive it knows about:

sudo apt-get update

You're now ready to install software from the PPA! Note that I already filled in the stuff you needed to look up! :D

---

### Post by Norm24 on 2010-01-30
> **lovinglinux said:**
> Ubuntuzilla is not upgrade, is a side-by-side installation of a separate version.

Never said Ubuntzilla was an upgrade in itself.But one can upgrade to 3.6 by installing Ubuntzilla and then installing the latest version of FF.After that any new updates for FF are done by opening a terminal and:
```
gksudo firefox
```
Once FF opens click on Help>Check for Updates.

---

### Post by 16sinker on 2010-01-30
> **tom.swartz07 said:**
> Sure!

If youre using karmic, just open a terminal and type
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

If youre in jaunty, its a bit more involved:

Step 1: Copy the first line from the apt sources.list entries section of the PPA overview page. For example:

```
deb http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
```

Step 2: On your Ubuntu computer, open System > Administration > Software Sources.

Step 3: Click the Third Party Software tab.


Step 4: Click the Add button.

Step 5: Paste the line you copied in step 1 and click the Add Source button.

Step 6: Now copy the second line from the apt sources.list entries section of the PPA overview page and paste it in just as you did in steps 4 and 5.

When prompted, reload the software sources information. Don't worry if you see a warning about unverified software sources; we're going to fix that next.

Telling Ubuntu how to authenticate the PPA

Now Ubuntu knows about the PPA. It also needs to know how to check the software hasn't been tampered with since Launchpad built it.

Note: This is not an endorsement of any of the software in PPAs. You must make sure you trust the PPA owner before installing their software.

Step 1: On the PPA's overview page you'll see the PPA's OpenPGP key id. It'll look something like this: 1024/12345678. Copy it, or make a note of, the portion after the slash, e.g: 12345678.

Step 2: Open your terminal and enter:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
```

Step 3: Finally, tell Ubuntu to re-load the details of each software archive it knows about:

sudo apt-get update

You're now ready to install software from the PPA! Note that I already filled in the stuff you needed to look up! :D

Thanks so much. Even with Jaunty the howto that you provided worked for me.:D

---

### Post by tom.swartz07 on 2010-01-30
> **16sinker said:**
> Thanks so much. Even with Jaunty the howto that you provided worked for me.:D

Sweet deal! Glad to help!

If you dont have any more questions, please mark the thread as [solved] in the thread tools!

---

### Post by nanotube on 2010-01-30
> **lovinglinux]> 
Also you can upgrade to 3.6 thru Ubuntzilla.

Ubuntuzilla is not upgrade, is a side-by-side installation of a separate version.
[/quote]

well, as far as it appears to the user, it looks like an 'upgrade', so i wouldn't quibble about it. :)

[QUOTE=lovinglinux said:**
> 
I recommend that you read [this](http://lovinglinux.megabyet.net/?page_id=220#Method-#4-1-Details-3). It explains what the installation method you have chosen.

hey, nice, i see you made a cool webpage of your nice firefox howto, with internal anchors and all - good stuff! :)

while i was looking, want to give you some comments for it:

in your 'manual' method, you make a symlink from /opt/firefox/plugins to /usr/lib/mozilla/plugins. starting with ff3.5, however, firefox looks in /usr/lib/mozilla/plugins by default, anyway, so there's no need to do this at all. (for reference, see this link: [https://developer.mozilla.org/en/firefox_3.5_for_developers](https://developer.mozilla.org/en/firefox_3.5_for_developers)  and search for '/usr/lib' ). 

so that means you can shorten your manual instructions by a whole 2 commands! :)

and further, speaking of plugins, note that there's a bug in the sun-java6-plugin package on karmic, (it doesn't place a symlink in /usr/lib/mozilla/plugins), a fix for which (and a link to the launchpad bug report) is here:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

additionally, i think the section for method #3, installation from ppa repositories, could use some links to the actual ppas on launchpad. 

hope that helps - keep up the good work on that howto!

---

### Post by lovinglinux on 2010-01-31
> **nanotube said:**
> well, as far as it appears to the user, it looks like an 'upgrade', so i wouldn't quibble about it. :)

I'm just exercising my OCPD :)

> **nanotube said:**
> hey, nice, i see you made a cool webpage of your nice firefox howto, with internal anchors and all - good stuff! :)

Thanks. I was thinking about adding tutorials to my site for some time and I finally decided to switch from Joomla to something lighter. I didn't imagine Wordpress would make it so easy. I'm completely in love with it. :)

> **nanotube said:**
> while i was looking, want to give you some comments for it:

in your 'manual' method, you make a symlink from /opt/firefox/plugins to /usr/lib/mozilla/plugins. starting with ff3.5, however, firefox looks in /usr/lib/mozilla/plugins by default, anyway, so there's no need to do this at all. (for reference, see this link: [https://developer.mozilla.org/en/firefox_3.5_for_developers](https://developer.mozilla.org/en/firefox_3.5_for_developers)  and search for '/usr/lib' ). 

so that means you can shorten your manual instructions by a whole 2 commands! :)

and further, speaking of plugins, note that there's a bug in the sun-java6-plugin package on karmic, (it doesn't place a symlink in /usr/lib/mozilla/plugins), a fix for which (and a link to the launchpad bug report) is here:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

additionally, i think the section for method #3, installation from ppa repositories, could use some links to the actual ppas on launchpad. 

hope that helps - keep up the good work on that howto!

Thanks a lot. I will update it right now.

---

### Post by nanotube on 2010-01-31
> **lovinglinux said:**
> 
Thanks. I was thinking about adding tutorials to my site for some time and I finally decided to switch from Joomla to something lighter. I didn't imagine Wordpress would make it so easy. I'm completely in love with it. :)

hrm... maybe i'll give it a try too. :)

> 
Thanks a lot. I will update it right now.

looks good! :)

---

