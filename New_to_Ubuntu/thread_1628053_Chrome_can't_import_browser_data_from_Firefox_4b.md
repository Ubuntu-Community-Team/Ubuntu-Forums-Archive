---
title: "Chrome can't import browser data from Firefox 4b?"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by sallam on 2010-11-22
Greetings

I've just downloaded and installed Google Chrome. It did not import anything from FF during the installation process. (their help page says it should)
Now I'm trying to import browser data from FF, using Chrome Preferences > Personal Stuff > Browsing data "Import data from another browser..."
But it says:> No supported browser found
I did some search, and it seems that Chrome fails to import data from browsers in development versions. I'm using FF 4b7. Could that be the reason why it didn't recognize it during installation and even now through Chrome preferences?

I tried to get back to FF3.6, the default version that came with ubuntu 10.10, but I don't know where it is located, and I don't know which file to double click to start FF3.6. I want to make it the default browser, then try re-installing Chrome to catch the data from FF..

Many thanks for any tips or suggestions.

---

### Post by NosferatuPT on 2010-11-22
I think the default version (3.6) has been updated to 4b7, that's why you can't find it.

You should go to Ubuntu Software Center and remove firefox, then try to install it again. This new installation should be a stable version, not a beta. You can do this in the Ubuntu Software Center or firefox website.

---

### Post by sallam on 2010-11-22
NosferatuPT,
Thanks for your help. I don't think that ubuntu switched to FF4 yet. btw, FF doesn't auto upgrade, it only updates. Upgrades, eg. from 3 to 4, has be done manually.

I found it!
For anyone who has the same issue:
I just typed firefox in the terminal, and FF3.6.11 started. Then, I made it the default browser from preferences > advanced. Then closed FF, opened Chrome, and went to: Preferences > Personal Stuff > Browsing data "Import data from another browser..." and there it was, firefox showing up at last!. It took Chrome only a second to get all data from FF.

Chrome 7 is awesome!

---

