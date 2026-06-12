---
title: "Could not download all repository indexes"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by clar3 on 2010-08-20
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct........Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead...plz need help i dont know whats going on with the updates ive tried update manager and i have ubuntu tweak and nothing seems to work it says its was last updated 8 days ago but shows packages and the above message appears any help would be appreciated.

---

### Post by natravis on 2010-08-20
It would appear that the PPA you were using for VLC has been reorganized (because the maintainer [c-korn] is still there on launchpad @ [https://launchpad.net/~c-korn/+archive/ppa](https://launchpad.net/~c-korn/+archive/ppa))

I don't see him as a maintainer of VLC on there, so perhaps that is why your link no longer works. You need to remove that PPA from your sources list and perhaps uninstall VLC then reinstall it from the standard repositories. Did you setup that PPA for a specific reason?

---

### Post by clar3 on 2010-08-20
everything is fine now i uninstalled vlc using ubuntu tweak and retried the update with both tweak and update manager and no new packages were available but it did finally say it was updated a couple seconds ago and the icon in my task bar is gone now so thanks):Pubuntu for life:D

---

