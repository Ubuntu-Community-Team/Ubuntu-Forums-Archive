---
title: "Problem installing firefox/konquerer updates"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Scorch40 on 2010-05-16
Hey guys!

I just installed Ubuntu on my laptop using the installer that runs from windows. I selected a blank partition as the location to install it, chose the Kubuntu style/GUI and it all works. Everything works fine, except for a couple of things. I went to install Firefox, and the installer opens, and runs, at which point I get a message saying "Requested packages already installed".

Also, all websites work basically fine in Konquerer except for facebook. Whenever I attempt to go to facebook, it attempts to open/save a file rather than display the page. I figured this was because the relevant flash updates or what not were not installed. I got a notification saying that there were available updates for Konquerer, and one of them was a flash update, yet when I attempted to install them I got the same error message as I got when I attempted to run firefox.

Sorry if I sound too detailed/not detailed enough, but any help would be great on this problem.

Thanks! :)

---

### Post by ashwinhgtx on 2010-05-16
You are running Kubuntu, the KDE version of Ubuntu.


Open up Konsole and type in
```
sudo apt-get update
```

Enter your password after this(you won't be able to see it), and hit enter.


After this is done type
```
sudo apt-get install firfox firefox-branding
```

---

### Post by lovinglinux on 2010-05-16
> **ashwinhgtx said:**
> You are running Kubuntu, the KDE version of Ubuntu.


Open up Konsole and type in
```
sudo apt-get update
```

Enter your password after this(you won't be able to see it), and hit enter.

After this is done type
```
sudo apt-get install firfox firefox-branding
```

The package **firefox-branding** is installed automatically when you install **firefox** package, so no need to include it in the command. BTW, your command has a typo in firefox.

The correct command would be:

```
sudo apt-get install firefox
```

---

