---
title: "Problems Accessing the Internet on 10.04.4 LTS"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by Boosh007 on 2013-09-30
Recently downloaded a copy of my Ubuntu 10.04.4 LTS on my sister's Dell Inspiron Mini 10 computer. a virus in her computer rendered it useless in Windows XP, and I use 10.04 so fixing future errors and troubles will be easier for me down the road. Everything works okay, but I can't access the internet, getting an error message, everytime  I try to log in. If I plug it in using an ethernet cable, it works fine and I have no problems. Just a few minutes ago, I downloaded a massive update, 243 files in a wired network, with a few included to fix Firefox, but it still doesn't work. The message I get consists of;

[COLOR=#ff0000]Server Not Found
Firefox can't find the server at start.ubuntu.com[/COLOR] (with three options as to what might be the cause for it. Tried two, but the third I'm not familiar with-firewalls?)

I know the wireless is working. If I place the cursor over the desktop icon for it it reads; [COLOR=#ff0000]Wireless network connection 'fisherman_EXT'
                                                                                                                          active: fisherman_EXT (100%)[/COLOR]

I bet it's something simple, but I'm at a loss as to what I can do. Any ideas?
William

---

### Post by sanderj on 2013-10-01
10.04 Desktop? You know it's not supported anymore? See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

---

### Post by bcschmerker on 2013-10-01
Be advised that desktop support for Ubuntu® 10.04.7-LTS Lucid Lynx&#8482; ended earlier this year, and server support ends in 2015.  Notwithstanding the settings problem briefed this Thread, some potential contributing factors have already been fixed in 12.04.3-LTS Precise Pangolin&#8482;, available for download at ubuntu.com.

---

### Post by Boosh007 on 2013-10-01
Had 12.04 for two-weeks. Hated it so bad that I crashed my computer on purpose, erased the hard drive, and re-downloaded 10.04. Don't care if it's not going to be supported, it works perfectly for what I do and the alteranative is too grizzly to even think about. Now, is there anyone with an answer to my question or should I just wing it?...

---

### Post by Bucky Ball on 2013-10-01
How about this for grizzly: If you have this computer online it is vulnerable and a security risk. It has not had security updates for six months and the longer you run it, the more vulnerable it will become.

If you don't like 12.04 because you don't like Unity try another desktop enviroment on it, or try another flavour. Xubuntu or Lubuntu are closer to the Gnome experience.

Have fun, but if you stay with 10.04 you do so at your own risk (and your chances of getting support for it here are not great - it's dead).

---

### Post by BluegrassHero on 2013-10-01
I was amazed how much I hated Unity but loved Ubuntu when I tried mate-desktop.  Give mate a try.

[http://mate-desktop.org/install/](http://mate-desktop.org/install/)

EDIT:  As a professional Red Hat Sys Engineer and recovering Fedora addict, this is a tough cup of coffee to drink, but I am committed to embracing Ubuntu and eventually finding myself as a total evangelist.  I have loved the simplicity of Gnome and mate is a well done implementation of it.  Unlike Windows, you have many options.  Before you give up on Unity, try (in this order, in my opinion):

Mate-desktop (a fork from Gnome 2)
LXDE or XFCE (both are similar enough that you'll initially love them both the same)
KDE (still very resource-heavy on older commodity (free) hardware that I use.

Lastly... give Unity a chance.  It has some pretty cool stuff to it, but I say this as a last resort because that's how I see it at the moment.  I am told I'll eventually embrace the feel and the shortcuts, but it's a lot to re-learn if you're a Gnome-2 head like myself.

I hope this is helpful thought.

---

### Post by sanderj on 2013-10-01
> **Boosh007 said:**
> Now, is there anyone with an answer to my question or should I just wing it?...

Well ... do this:

```
ifconfig
mtr -nrc2 8.8.8.8
nslookup www.google.com

```

Post the output here

---

### Post by sanderj on 2013-10-02
@Boosh007 ... did you read my post with advice? You asked for help, I gave it, so I would like to see your followup.

---

### Post by Bucky Ball on 2013-10-02
> **sanderj said:**
> @Boosh007 ... did you read my post with advice? You asked for help, I gave it, so I would like to see your followup.

@Boosh007: Please share with the community how you solved this or whether you chose to install a supported release. Cheers. ;)

---

### Post by Boosh007 on 2013-10-03
I chose to download a supported release; Poseidon Linux 4 which is an exact mirror of 10.04LTS for the scientific community... I will be downloading a copy for myself as soon as I can log all the info I can't take with me on a flash drive.

---

### Post by sanderj on 2013-10-04
> **Boosh007 said:**
> I chose to download a supported release; Poseidon Linux 4 which is an exact mirror of 10.04LTS for the scientific community... I will be downloading a copy for myself as soon as I can log all the info I can't take with me on a flash drive.

Out of curiosity I downloaded Poseidon Linux 4 and installed it in a VM. Results:

- big download (3 - 4 GB)
- needs quite a lot of disk space (8GB was too little, so I assigned 16GB disk space)
- it installs and it works. Flash works. Nice.
- kernel is 2.6.32-52
- lsb_release -a says 10.04.2, not 10.04.4. Pity.
- sudo apt-get update / upgrade gives errors on quite a list of sources. That worries me a bit

---

### Post by Bucky Ball on 2013-10-05
> **sanderj said:**
> 
- sudo apt-get update / upgrade gives errors on quite a list of sources. That worries me a bit

If it's using the Ubuntu 10.04 repos that's not surprising. Maybe you could have a dig (available backports maybe?) and tweak source.list. You might also try installing a newer kernel (you should then be able to choose from the old or new at boot). Otherwise, looks good if you've got the specs to handle it. ;)

---

