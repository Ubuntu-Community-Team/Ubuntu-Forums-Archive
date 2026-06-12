---
title: "Firefox 3.6"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by augie2051 on 2010-01-30
Can someone help me with installing 3.6 in Koala? I found a tutorial but at the end stage received the following output:
"Package firefox-3.6 is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another sourceE: Package firefox-3.6 has no installation candidate"

Any ideas on what went wrong better yet how to fix?

---

### Post by skymera on 2010-01-30
Use this:

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

Instructions are on page :)

---

### Post by Norm24 on 2010-01-30
Ubuntzilla.

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

---

### Post by skymera on 2010-01-30
Please note Ubuntuzilla has only 32bit Firefox.

---

### Post by augie2051 on 2010-01-30
I found the fix and a super easy install!

[http://techdrivein.blogspot.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html](http://techdrivein.blogspot.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html)

---

### Post by lovinglinux on 2010-01-30
[Installation Methods](http://lovinglinux.megabyet.net/?page_id=220#Installation-Methods-2)

---

### Post by Silvertones on 2010-01-30
I'd love to have 3.6 as I was using it in Windows however isn't getting programs outside of the synaptic repositories sort of risky and contrary to the whole idea of Linux?

---

### Post by samh785 on 2010-01-30
> **Silvertones said:**
> I'd love to have 3.6 as I was using it in Windows however isn't getting programs outside of the synaptic repositories sort of risky and contrary to the whole idea of Linux?
It's only risky if you're really really new. :P

---

### Post by Silvertones on 2010-01-30
> **samh785 said:**
> It's only risky if you're really really new. :P

That's not a very satisfactory answer!

---

### Post by augie2051 on 2010-01-30
ubuntuzilla is a trusted and respected means.  If you want 3.6 you can get it there or the link to loving linux.

---

### Post by lovinglinux on 2010-01-30
> **Silvertones said:**
> I'd love to have 3.6 as I was using it in Windows however isn't getting programs outside of the synaptic repositories sort of risky and contrary to the whole idea of Linux?

Short answer is yes. Long answer,  Ubuntuzilla project exists since 2007 and the people behind it are trustworthy. The PPA mentioned on other posts is from the [guys behind the Ubuntu version of Firefox](https://wiki.ubuntu.com/MozillaTeam).

---

### Post by nanotube on 2010-01-30
> **augie2051 said:**
> I found the fix and a super easy install!

[http://techdrivein.blogspot.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html](http://techdrivein.blogspot.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html)

note that these instructions are now outdated - ubuntuzilla now hosts a ppa repository with the latest mozilla releases, which is a much smoother user experience that dealing with an installer script. 

(though the old installer script still works, if you choose to use it).

latest info is always on the ubuntuzilla website:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by nanotube on 2010-01-30
> **lovinglinux said:**
> Short answer is yes. Long answer,  Ubuntuzilla project exists since 2007 and the people behind it are trustworthy. 

i very much appreciate your positive comment :), and i'd like to add the following:

the trustworthiness of ubuntuzilla verifiable: the binaries packaged in the ubuntuzilla ppa are unmodified binaries as released by mozilla, so anyone could extract the .debs and compare the checksums of the contents with those of a tar.bz2 downloaded directly from mozilla.com.

---

### Post by lovinglinux on 2010-01-30
> **nanotube said:**
> i very much appreciate your positive comment :), and i'd like to add the following:

the trustworthiness of ubuntuzilla verifiable: the binaries packaged in the ubuntuzilla ppa are unmodified binaries as released by mozilla, so anyone could extract the .debs and compare the checksums of the contents with those of a tar.bz2 downloaded directly from mozilla.com.

I forgot about that :)

---

### Post by Easy Limits on 2010-01-30
I didn't have any luck with the instructions on Ubuntuzilla.  But I did follow the instructions in this thread and it worked like a champ.  Thanks guys!

---

### Post by nanotube on 2010-01-30
> **Easy Limits said:**
> I didn't have any luck with the instructions on Ubuntuzilla.  But I did follow the instructions in this thread and it worked like a champ.  Thanks guys!

as long as you got something working, it's all good :) - but would you mind telling me, if you remember, what exactly didn't work for you on the ubuntuzilla instructions? if there are any problems with the repository, i'd like to fix them.

---

### Post by Silvertones on 2010-01-31
Nanotube,
OK so I followed the install instructions and everything went fine EXCEPT I lost NOSCRIPT. I tried a reinstall through Synaptic but no dice. I really want this feature.

---

### Post by Silvertones on 2010-01-31
Now this surprised me. I did a search for addons specifcally noscript. I just told it to add it to firefox and it did.

---

### Post by lovinglinux on 2010-01-31
> **Silvertones said:**
> Now this surprised me. I did a search for addons specifcally noscript. I just told it to add it to firefox and it did.

Yes, you can download noscript form [Mozilla Add-ons](https://addons.mozilla.org/en-US/firefox/addon/722) site, since it is an extension for Firefox, although it is also available through Synaptic. It wasn't showing up probably because the Synaptic version install it for all users, on the default Firefox installation folder. Since Ubuntuzilla is a different package, you need to install the extensions through Firefox interface.

---

### Post by Silvertones on 2010-01-31
It's odd that my other extensions did. AHHH I think I know why. When I first started with Ubuntu I imported the Win Firefox profile. It had 3 extensions. I DL noscript through Synaptic.

---

### Post by lovinglinux on 2010-01-31
> **Silvertones said:**
> It's odd that my other extensions did. AHHH I think I know why. When I first started with Ubuntu I imported the Win Firefox profile. It had 3 extensions. I DL noscript through Synaptic.

Because when you install from Firefox they are stored in the profile folder of the user. So even if you install several different versions of Firefox, they will show on all versions, as long as you use the same FF profile.

---

### Post by nanotube on 2010-01-31
silvertones:
ok, that explains it. it's as lovinglinux said, about where the files go when you install through synaptic, vs when you install manually through the addons functionality.

---

### Post by Silvertones on 2010-01-31
OK so I'm good with Firefox. Thunderbird was another story. I followed the same procedure however it did not use the profiles from version2.0.

---

### Post by Easy Limits on 2010-01-31
> **nanotube said:**
> as long as you got something working, it's all good :) - but would you mind telling me, if you remember, what exactly didn't work for you on the ubuntuzilla instructions? if there are any problems with the repository, i'd like to fix them.

When I downloaded the installer .deb package and double clicked on it the little installer window said "Error: wrong architecture i386"

This kind of surprised me since I am using 9.10 32-bit.

---

### Post by Silvertones on 2010-01-31
I reverted back to the official synaptic versions. I'm just too green with Ubuntu to be messing around with something I don't understand.

---

### Post by nanotube on 2010-01-31
> **Easy Limits said:**
> When I downloaded the installer .deb package and double clicked on it the little installer window said "Error: wrong architecture i386"

This kind of surprised me since I am using 9.10 32-bit.

which 'installer .deb package' did you download? why not just use the repository as it's meant to be used?

instructions are at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by old fert on 2010-01-31
This seemed to work without a hitch.

Thanks,

---

### Post by Easy Limits on 2010-01-31
This one:

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

---

### Post by lovinglinux on 2010-01-31
> **Silvertones said:**
> OK so I'm good with Firefox. Thunderbird was another story. I followed the same procedure however it did not use the profiles from version2.0.

The problem is that Mozilla has changed it's update policy and Canonical is adapting to follow it. So until Jaunty, when you installed a alternative version like Firefox 3.5, it was installed side-by-side with the default version and your profiles were copied from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5.

Now, it doesn't install side-by-side and uses the same profiles used by the default version. The same behavior should apply to Thunderbird. But it doesn't. Currently, when you install Thunderbird 3.0, it creates a new profile folder, which is  ~/.thunderbird-3.0. So close Thunderbird and copy the contents from ~/.thunderbird to ~/.thunderbird-3.0 or delete the last one and create a symlink pointing to ~/.thunderbird. Make backups first to avoid loosing data.

---

### Post by nanotube on 2010-01-31
> **Easy Limits said:**
> This one:

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

well, read the description right above the green download button, which says "do not manually download files". 

instead, just go to the website and read the instructions for using the repository.

i don't yet know how to get rid of the green download button on sourceforge...

---

### Post by nanotube on 2010-01-31
> **lovinglinux said:**
> 
[quote=Silvertones]
OK so I'm good with Firefox. Thunderbird was another story. I followed the same procedure however it did not use the profiles from version2.0.

The problem is that Mozilla has changed it's update policy and Canonical is adapting to follow it. So until Jaunty, when you installed a alternative version like Firefox 3.5, it was installed side-by-side with the default version and your profiles were copied from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5.

Now, it doesn't install side-by-side and uses the same profiles used by the default version. The same behavior should apply to Thunderbird. But it doesn't. Currently, when you install Thunderbird 3.0, it creates a new profile folder, which is  ~/.thunderbird-3.0. So close Thunderbird and copy the contents from ~/.thunderbird to ~/.thunderbird-3.0 or delete the last one and create a symlink pointing to ~/.thunderbird. Make backups first to avoid loosing data.[/QUOTE]

if you're using ubuntuzilla, then you won't see a ~/.thunderbird-3.0.

iirc, the ubuntu-repos version uses ~/.mozilla-thunderbird, while the mozilla official build using ~/.thunderbird.

so for ubuntuzilla, symlink .thunderbird to .mozilla-thunderbird, or just rename .mozilla-thunderbird to .thunderbird.

(and of course, back up your stuff before messing around with it.)

---

### Post by lovinglinux on 2010-02-01
> **nanotube said:**
> if you're using ubuntuzilla, then you won't see a ~/.thunderbird-3.0.

iirc, the ubuntu-repos version uses ~/.mozilla-thunderbird, while the mozilla official build using ~/.thunderbird.

so for ubuntuzilla, symlink .thunderbird to .mozilla-thunderbird, or just rename .mozilla-thunderbird to .thunderbird.

(and of course, back up your stuff before messing around with it.)

I forgot to mention I'm using the daily PPA for Thunderbird.

Bottom line, whenever you install Thunderbird or Firefox from alternative sources, you need to check if you profile has been cloned to another folder and symlink to your original.

---

### Post by Silvertones on 2010-02-02
Well I'm back to the latest versions. Firefox is fine as it uses the existing profile.

In TB I use two profiles so I did some thinking. Here's what I did:
 ```
 thunderbird -ProfileManager
```Then using the Profile Manager I created the two new profiles in .thunderbird. It's simply assigning a name. When done I went into .mozilla-thunderbird and copied everything in the John profile folder and pasted it into the .thunderbird John profile folder. I repeated that for each profile.
I did it this way so that I could copy the profile from 3.0   to 2.0. That way if 3.0 messes up I can uninstall it and revert to 2.0 without any loss.

---

### Post by jmelton on 2010-02-02
I've followed the instructions for Ubuntuzilla and it says it has successfully installed Firefox 3.6, but I cannot start the browser.  It just shows "Firefox" on the bottom menu and does nothing when I click on either the icon on the launcher panel or the one in the Applications menu.  I tried just typing firefox on the command line as well & same thing, although I suppose it's possible that the command for launching firefox from the command line is something other than that.  The command that is entered in the Launcher is firefox %u.  What do I need to do to get this going again?

---

### Post by jmelton on 2010-02-02
> **jmelton said:**
> I've followed the instructions for Ubuntuzilla and it says it has successfully installed Firefox 3.6, but I cannot start the browser.  It just shows "Firefox" on the bottom menu and does nothing when I click on either the icon on the launcher panel or the one in the Applications menu.  I tried just typing firefox on the command line as well & same thing, although I suppose it's possible that the command for launching firefox from the command line is something other than that.  The command that is entered in the Launcher is firefox %u.  What do I need to do to get this going again?

The problem has suddenly fixed itself.  Although I'm glad it's now working, I wish I knew what was going wrong before.

---

### Post by nanotube on 2010-02-02
> **jmelton said:**
> The problem has suddenly fixed itself.  Although I'm glad it's now working, I wish I knew what was going wrong before.

my guess is: the problem was because you haven't completely exited the previous version.

---

