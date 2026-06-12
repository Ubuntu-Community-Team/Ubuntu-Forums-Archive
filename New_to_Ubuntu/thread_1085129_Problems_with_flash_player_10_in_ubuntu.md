---
title: "Problems with flash player 10 in ubuntu"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Blackdog909 on 2009-03-02
I am having trouble getting flash player 10 to work in ubuntu 8.04.
I have the latest version but it does not work. Suggestions anyone?

---

### Post by Kareeser on 2009-03-02
Error?

---

### Post by charliehorse55 on 2009-03-02
Are you using a 64 bit build of ubuntu?

---

### Post by fong on 2009-03-02
Hi,

I'm also having some problems with the flash player. When I load up videos on firefox, it, most of the time crashes.

Am on 8.10 64 bit.

---

### Post by Blackdog909 on 2009-03-03
no, No 64 bit computer here

---

### Post by gandaran on 2009-03-03
> **Blackdog909 said:**
> no, No 64 bit computer here
where did you get the flash 10/how did you install it? do you have your ubuntu fully updated (and update channels enabled), did you remove any other flash package you mite have installed first?
see [this ]("http://gandaran.com.sapo.pt/ubuntu.html")for installing flash

---

### Post by gandaran on 2009-03-03
> **fong said:**
> Hi,

I'm also having some problems with the flash player. When I load up videos on firefox, it, most of the time crashes.

Am on 8.10 64 bit.
try installing the 64-bits adobe flash, maybe it will fix your problem.
remove the flashplugin-nonfree (32-bits flash) installed first, now get the 64-bits package [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz"), to install extract the package and move the libflasplayer.so file to /home/'user'/.mozilla/plugins (create the plugins folder) or if you have more than one user account place it in /usr/lib/mozilla/plugins, thats all!

---

### Post by charliehorse55 on 2009-03-03
> **fong said:**
> Hi,

I'm also having some problems with the flash player. When I load up videos on firefox, it, most of the time crashes.

Am on 8.10 64 bit.
Read here:
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

Scroll down to where it says Flash 10. Execute the lines of code reboot your browser and voilia!

Worked for me, I'm using 8.10 64 bit as well.

---

### Post by philinux on 2009-03-03
No need to run any scripts. You only need this file as has been said.
libflasplayer.so

Copied to 
~/.mozilla/plugins

What could be easier.

---

### Post by Blackdog909 on 2009-03-05
I reinstalled ubuntu and it now works fine. Thanks for the help.

---

### Post by RichardCain on 2009-03-07
I tried downloading install_flash_player_10_linux.deb - it downloads no problem but when it goes to install, I get: 

Error: Dependency is not satisfiable: libpango1.0-0

Any thoughts??

---

### Post by Ripose on 2009-03-07
*libpango* is available from the Main Ubuntu Repository.
Use Synaptic Package Manager, to see if it is installed.

---

### Post by gandaran on 2009-03-07
> **RichardCain said:**
> I tried downloading install_flash_player_10_linux.deb - it downloads no problem but when it goes to install, I get: 

Error: Dependency is not satisfiable: libpango1.0-0

Any thoughts??
the adobe flash .deb package is only for ubuntu 8.04 and above, what version are you running? 
for earlier ubuntu versions download the .tar.gz package

---

### Post by RichardCain on 2009-03-17
Thanks guys.  Flash Player is now working.  Unfortunately I've been so busy sorting all kinds of sh*% out over the last week, I can't exactly remember how I fixed it.  It's working anyway, that's the main thing.

---

### Post by Bios Element on 2009-03-17
> **RichardCain said:**
> Thanks guys.  Flash Player is now working.  Unfortunately I've been so busy sorting all kinds of sh*% out over the last week, I can't exactly remember how I fixed it.  It's working anyway, that's the main thing.

Meh, I know how that is. I've fixed most every problem but for the life of me I can't remember WTF I did to fix them. Glad it's working for ya man.

---

### Post by stchman on 2009-03-17
> **Blackdog909 said:**
> I am having trouble getting flash player 10 to work in ubuntu 8.04.
I have the latest version but it does not work. Suggestions anyone?

If you are running 32 bit you can get the Flash 10 installer in .deb format from Adobe website.

---

### Post by nikislash on 2009-03-24
Im running 32 bit 8.04 and I couldnt get flash player 10 to work either. When I tried to install the .deb i got an error about a libpango1.0-0 dependancy 

In the end I just downloaded flash player version 9 and that works perfectly

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2)

---

### Post by patocardo on 2009-04-04
Sorry about my ignorance, but how can I copy that file to ~/.mozilla/plugins; I have the file in my dir, but I cannot find mozilla dir

---

