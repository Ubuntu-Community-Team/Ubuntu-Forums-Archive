---
title: "Unable to Upgrade to Firefox 6"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by Merisi on 2011-08-30
I've just downloaded Firefox 6 but I'm unable to use it.  I saw somewhere about using some sudo apt code but I've no how to use this.  I would gladly appreciate any help.

---

### Post by bodhi.zazen on 2011-08-30
Many use the ppa :

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

### Post by Merisi on 2011-08-30
> **bodhi.zazen said:**
> Many use the ppa :

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

 Forgive me but I've no idea what the ppa is.  I've literally just installed Ubuntu and it's alien to me.

---

### Post by Enigmapond on 2011-08-30
No need to apologize..:) Open your terminal and copy/paste this:

```
sudo apt-add-repository ppa:mozillateam/firefox-stable
```

then

```
sudo apt-get update && sudo apt-get upgrade
```

This should upgrade you to the new firefox.

Cheers!

---

### Post by Merisi on 2011-08-30
> **Enigmapond said:**
> No need to apologize..:) Open your terminal and copy/paste this:

```
sudo apt-add-repository ppa:mozillateam/firefox-stable
```then

```
sudo apt-get update && sudo apt-get upgrade
```This should upgrade you to the new firefox.

Cheers!

 I copied the code and then I pressed alt-F2 and then pasted the code with control-v I then pressed enter and nothing seemed to happen.  Thank you for your patience with me.

---

### Post by Enigmapond on 2011-08-30
I'm terribly sorry...the first code should read:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

after you enter your pass it will import the key. Then run the second command from my previous..

OOPS..:))

---

### Post by oldsoundguy on 2011-08-30
just remember that CLI or terminal in Linux is akin to CMD in Windows.  With the exception that in Linux when you write or paste a command, you will have to follow that command with your password.  That is to keep from installing by accident .... something that Windows does far too often.

---

### Post by Merisi on 2011-08-30
> **Enigmapond said:**
> I'm terribly sorry...the first code should read:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```after you enter your pass it will import the key. Then run the second command from my previous..

OOPS..:))

 Thank you so much I managed to upgrade after finally finding the terminal.  Will Firefox now automatically update?

---

### Post by bodhi.zazen on 2011-08-30
> **Merisi said:**
> Forgive me but I've no idea what the ppa is.  I've literally just installed Ubuntu and it's alien to me.

A ppa is a "Personal Package Archive"

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

Many people or teams package various things into a ppa so if a ppa is available it is an alternate source for packages not in the standard ubuntu repositories, in your case firefox 6

---

### Post by Enigmapond on 2011-08-30
> **Merisi said:**
> Thank you so much I managed to upgrade after finally finding the terminal.  Will Firefox now automatically update?

Yes. When FF7 is released it will automatically update. Please mark this thread as "Solved" in the Thread Tools above and good luck!

---

### Post by Merisi on 2011-08-30
I would just like to thank everyone that offered help in this thread.  It's a pleasure being part of the Ubuntu community :)

---

