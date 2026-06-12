---
title: "Ubuntu software center, cant install DeVeDe"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by sunwatt on 2010-05-01
Just installed 10.04LTS, and all was pretty smooth. 

I've used Ubuntu Software center to install k3b, and openshot, went fine.

But when I tried to install DeVeDE I got these error messages.

How can I get DeVeDe installed?

One worry I have is I did Medibuntu in Terminal at a wifi hot spot with 40% signal, there was a couple errors, but Im not sure. Should I do medibuntu again?

This:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

My mp3's play and I did the flashplayer, nonfree thing, and youtube works.

Thanks

Jim
Mini 9 16GB SSD

---

### Post by zvacet on 2010-05-02
It look as you add Medibuntu repo to your source list.You can check that if you go to the places>file system>etc>apt>sources-list.d.Go to the system>admin>software sources>check all under ubuntu software and first two under updates tab.Reload and try again to install desired package.

---

### Post by coffeecat on 2010-05-02
> **sunwatt said:**
> One worry I have is I did Medibuntu in Terminal at a wifi hot spot with 40% signal, there was a couple errors, but Im not sure. Should I do medibuntu again?

The Medibuntu package server was down for some of yesterday and today, so one of those errors would have been to tell you that it couldn't download the Medibuntu keyring. And that's the reason you are getting the untrusted messages - no keyring authentication.

Go into System > Administration > Synaptic and do a Reload. Then look for the package 'medibuntu-keyring' and mark it for installation. Click on 'Apply' and it will be downloaded and installed. Now you should be able to install devede (with the Medibuntu dependencies) without the untrusted messages. (Close Synaptic before you try to use Software Centre.)

---

### Post by sunwatt on 2010-05-03
Thanks for the reply. While I was waiting for a reply, I tried installing with synaptic.

The install went fine, but didnt see devede listed as installed under applications.

I might have just been crosseyed, or missed seeing it, but I dont think so.

What I did next was futz with kpackage, typed devede in the search window, hit find, and it found DeVeDE.

I saw an Apply button, and hit it.

Checked Applications again, and found DeVEDe... okkkkkk

Thanks for the tip on Medibuntu keyring !

Jim

---

