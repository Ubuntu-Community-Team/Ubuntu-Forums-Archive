---
title: "Upgrading Firefox"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by pkj on 2010-08-15
Hi,

I am running ubuntu 9.04
Due to slow internet connection i am not able to upgrade ubuntu..

I want to upgrade only Firefox as of now..
I have downloaded firefox-3.6.8.tar.bz2

Need to know as to how to upgrade my exiting firefox

Also, some sites are not opening in firefox...They are asking only for the IE..

Will i be able to open them with upgraded firefox...Or any other way out..

pkj:

---

### Post by lovinglinux on 2010-08-15
You can't upgrade Firefox by downloading from Mozilla. Software upgrades in Ubuntu are done through the package manager. Nevertheless, you can run that  version you have downloaded, side by side with your current version.

See method #1 of the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

About sites asking for IE, use [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/") extension to spoof the browser "identity".

---

### Post by xangua on 2010-08-15
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by sandyd on 2010-08-15
> **pkj said:**
> Hi,

I am running ubuntu 9.04
Due to slow internet connection i am not able to upgrade ubuntu..

I want to upgrade only Firefox as of now..
I have downloaded firefox-3.6.8.tar.bz2

Need to know as to how to upgrade my exiting firefox

Also, some sites are not opening in firefox...They are asking only for the IE..

Will i be able to open them with upgraded firefox...Or any other way out..

pkj:[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/)

---

### Post by snowpine on 2010-08-15
Try:

```
sudo apt-get update
sudo apt-get install firefox
```

This will upgrade your Firefox to the current version in the Ubuntu repositories (without updating your entire system, since you have a slow connection).

You can use the Firefox plugin called User Agent Switcher to fool sites into thinking you're using IE.

---

### Post by lovinglinux on 2010-08-15
> **snowpine said:**
> Try:

```
sudo apt-get update
sudo apt-get install firefox
```

This will upgrade your Firefox to the current version in the Ubuntu repositories (without updating your entire system, since you have a slow connection).

You can use the Firefox plugin called User Agent Switcher to fool sites into thinking you're using IE.

This probably won't work, since the browser is already installed.

Try this instead:

```
sudo apt-get update
sudo apt-get install --reinstall firefox
```

---

