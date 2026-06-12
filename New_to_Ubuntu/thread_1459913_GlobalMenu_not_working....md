---
title: "GlobalMenu not working..."
date: 2010-04-22
forum: New to Ubuntu
---

### Post by camn on 2010-04-22
I'm trying to get Ubuntu to look like Mac OSX and I have everything except for the GlobalMenu... I've tried everything Google told me to do... Can you guys post suggestions on what to do here? Thanks :D

---

### Post by wojox on 2010-04-22
You added and ran this:

```

sudo add-apt-repository ppa:globalmenu-team/ppa;
sudo apt-get update;
sudo apt-get install gnome-globalmenu

```

---

### Post by camn on 2010-04-23
[s]sudo apt-get update gave me this error... [/s]```
E: Some index files failed to download, they have been ignored, or old ones used instead
```[s]and sudo apt-get install gnome-globalmenu gave me this error... [/s]```
The following packages have unmet dependencies:
  gnome-applet-globalmenu: Depends: gnome-globalmenu-common but it is not going to be installed
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_globalmenu-team_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_globalmenu-team_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```Got it, I just searched for "gnome global menu" on and deleted everything that came up, then re-installed and it works fine :D

---

