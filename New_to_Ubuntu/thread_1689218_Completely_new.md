---
title: "Completely new"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by chatterb0x on 2011-02-16
Ok every, so my windows 7 just crashed on me and I'm running off Ubuntu from the CD, not yet fully installing it, trying to get 9.10 older version. But in the meantime, I'm trying to get adobe flash player to work for youtube videos but I have NO idea how to work this OS... when I try installing adobe flash it just brings up this tar.gz thing.

I'm also trying to configure my platonics headset (usb plug) so I can talk to my peeps on skype.

---

### Post by andymorton on 2011-02-16
> **chatterb0x said:**
> Ok every, so my windows 7 just crashed on me and I'm running off Ubuntu from the CD, not yet fully installing it, trying to get 9.10 older version. But in the meantime, I'm trying to get adobe flash player to work for youtube videos but I have NO idea how to work this OS... when I try installing adobe flash it just brings up this tar.gz thing.

I'm also trying to configure my platonics headset (usb plug) so I can talk to my peeps on skype.

Go to the following page and in the drop down list choose .deb for Ubuntu 8.04+. Right click on the file when it's downloaded and choose install with gdebi installer. [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect)


If it's not there you can get from add/remove programmes. 
Alternatively you could install the Ubuntu Restricted Extras package which includes Flash, MP3 support, Java, Microsoft fonts etc. 
I can't help with the headset. Sorry
andy :)

---

### Post by Keiran230 on 2011-02-18
As for flash, Java, mp3, wmv, and other formats that aren't open source, but commonly wanted, this can all be installed in one convenient command. (type it into the terminal, in Applications > Accessories > Terminal)

*sudo apt-get -y install ubuntu-restricted-extras*

**HEADS UP**: It downloads a LOT of software. If it's a live disk, it probably isn't worth the wait though, since it's a pretty large download. If you decide to fully install Ubuntu later, this command will be awesome for you.

You can also do this through Applications > Ubuntu Software Center, but I just memorized the command, which I find simpler. As for the file you find, the reason you get a .tar.gz file from Adobe is because that's a generic Linux archive format that would work on ANY distribution, not just Ubuntu.

---

