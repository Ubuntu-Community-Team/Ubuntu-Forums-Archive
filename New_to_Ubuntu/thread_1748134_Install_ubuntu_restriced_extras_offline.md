---
title: "Install ubuntu restriced extras offline"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by xxnishantxx on 2011-05-03
hello,
Where I live, Internet connection is very slow. everytime i install ubuntu, i have to download the ubuntu-restricted-extras package. 
I tried to save the deb file from the apt cache and tried installing it after a reinstall of ubuntu. In the software certre, it shows it as installed, but none of the codecs or flash seem to work.
Can anybody suggest a reason why this is not working as it should be...
Thanks in advance!

---

### Post by ManiDhillon on 2011-05-03
Did you reload your software list before installing them?
Flash and Fonts require a live internet connection to install eac time because they load files from internet, so the reason flash is not working is obvious. As for codecs I don't know what is wrong, I have a fast connection but I don't like to download ! gig each time I re-install my OS so I do the same thing but this never happened with me.
If you could please write the steps you followed, I can try to figure the problem.
And for next time try to use AptOnCD package, it is in ubuntu repo and it can do all the offline installation and backing up work of your apt cache for you. It is easy to use.

---

### Post by xxnishantxx on 2011-05-03
thanks for the quick reply. I'm using 11.04 Natty by the way.
this is what I did:
-go to /var/cache/apt/archives and copy the ubuntu-restricted-extras_42_i386.deb and ubuntu-restricted-addons_4_i386.deb files to a different partition.
-Reinstalled ubuntu later
-I opened ubuntu-restricted-addons_4_i386.deb in Software Centre and clicked on the Install button. the package installed
-opened the ubuntu-restricted-extras_42_i386.deb file in Software Centre and that installed as well without any error messages.

I thought this meant that its installed, so I opened firefox and tried to watch videos but t said I was missing Flash. Then I opened Totem to watch a video and it asked me whether I want to search for missing plugins. Therefore, I concluded that although it says that its installed in the Saftware Centre, the actual contents of the package are missing...
still in the dark here about how to get it to install everything.
About the fonts and Flash, you mentioned that it loads files from the Internet. This may sound stupid, but shouldn't those files be included in the deb file that I backed up? maybe i'm missing something essential about how this stuff works. anyway, thanks for your help. will check out AptonCD

---

### Post by ManiDhillon on 2011-05-03
Oh mate you did wrong. They are just pointer/dummy packages. In real they when you select them in Synaptic they install so many other packages like gstreamer and other packages. Go to synaptic and remove these packages. The install from internet again. Next time copy all the contents of /var/cache/apt/archives. After you install your OS, copy them back to same location and install from Synaptic Package Manager not by clicking on them.

---

### Post by xxnishantxx on 2011-05-03
thanks a lot man! yeah that makes sense now...stupid me. shouldve thought of that. thanks loads again mate - gonna save me a lot of trouble and time

---

### Post by ManiDhillon on 2011-05-03
Anytime man. No need of thanks.

---

### Post by gandaran on 2011-05-03
> **xxnishantxx said:**
> thanks for the quick reply. I'm using 11.04 Natty by the way.
this is what I did:
-go to /var/cache/apt/archives and copy the ubuntu-restricted-extras_42_i386.deb and ubuntu-restricted-addons_4_i386.deb files to a different partition.
-Reinstalled ubuntu later
-I opened ubuntu-restricted-addons_4_i386.deb in Software Centre and clicked on the Install button. the package installed
-opened the ubuntu-restricted-extras_42_i386.deb file in Software Centre and that installed as well without any error messages.

I thought this meant that its installed, so I opened firefox and tried to watch videos but t said I was missing Flash. Then I opened Totem to watch a video and it asked me whether I want to search for missing plugins. Therefore, I concluded that although it says that its installed in the Saftware Centre, the actual contents of the package are missing...
still in the dark here about how to get it to install everything.
About the fonts and Flash, you mentioned that it loads files from the Internet. This may sound stupid, but shouldn't those files be included in the deb file that I backed up? maybe i'm missing something essential about how this stuff works. anyway, thanks for your help. will check out AptonCD
you must have a internet connection for flash and the fonts as they are directly download from the internet, the flash and fonts files aren't included in the .deb packages.

---

