---
title: "Edit Thunderbird Profiles.ini to access Samba share on freenas"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by johniathome on 2010-07-29
I am migrating from Windows to Ubuntu.

I have been using Thunderbird on Windows for some time. All Tbird files are stored on my freenas server on a different box. I need to modify the Tbird profiles.ini in Ubuntu to point to this.

Profiles.ini currently says:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=out5d9no.default

When I navigate to the share on my freenas box using Nautilus in Ubuntu, the location column shows:

	smb://freenas.loacl/n-data-new/~~~N-DELTA/~PERSONAL

Just to check I could see this before modifying Profiles.ini, I opened a terminal and typed in:

	cd smb://freenas.loacl/n-data-new/~~~N-DELTA/~PERSONAL

...but is says there's no such directory.

So, my question is: the Path line in Profiles.ini needs to be modified - but to what?

---

