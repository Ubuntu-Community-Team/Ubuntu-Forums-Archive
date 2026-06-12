---
title: "how to upgrade firefox"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by DarinB on 2010-04-21
how to upgrade firefox in hardy heron..using 3.0.17

---

### Post by cuberts on 2010-04-21
> **DarinB said:**
> how to upgrade firefox in hardy heron..using 3.0.17go to this link and install it.
It might say that this type of install might hurt your computer, but it wont. Click [here]("http://www.mozilla.com/en-US/firefox/firefox.html?utm_source=google&utm_medium=ppc&utm_campaign=firefox36&gclid=CJ6m-7zrmKECFQENDQodzEq_bA") for the link

---

### Post by wojox on 2010-04-21
Look here as well [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by ddecator on 2010-04-22
Best way is to use the Ubuntu Mozilla Team stable PPA: [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

This is supported by the Ubuntu Mozilla Team, so if you have any trouble with it, you can submit bugs on Launchpad. This will also allow you to get updates automatically with your system instead of installing separate.

Hope this helps!

---

### Post by egalvan on 2010-04-22
> **DarinB said:**
> how to upgrade firefox in hardy heron..using 3.0.17

The latest FF on hardy is 3.0.19.


> **ddecator said:**
> Best way use the **Ubuntu Mozilla Team stable PPA**:
 [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

This is supported by Ubuntu Mozilla Team,, you can submit bugs on Launchpad.
 This will also allow you to get updates automatically with your system instead of installing separate.

Absolutely +1 on this PPA.

Alternatively, you could wait two or three weeks for Lucid 10.04 LTS...
one week for it to go gold, and one or two weeks to weed out the show-stopper bugs...
 of which there should be none left.

That is what I will be doing on my non-work (aka "play") machines...

on my two work machines, I will be waiting for the point release six months down the pike
10.04.1
Can't be TOO stable when it comes to work... :)

---

### Post by nhasian on 2010-04-22
> **DarinB said:**
> how to upgrade firefox in hardy heron..using 3.0.17

Since no one mentioned it yet, you can upgrade directly from ubuntu hardy heron 8.04 to 10.04 lucid lynx next week when its released.  doing so will upgrade all your software including firefox :)

---

### Post by oldsoundguy on 2010-04-22
I have used the Ubuntuzilla site for upgrades for several years.

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

newest version now has an active "check for updates" button .. no more running the python script and no more work in terminal.

---

### Post by ddecator on 2010-04-22
> **oldsoundguy said:**
> I have used the Ubuntuzilla site for upgrades for several years.

Ubuntuzilla is not officially supported, so if you have any issues with it you will have a harder time getting help. The Ubuntu Mozilla Team PPAs are generally the better option.

---

### Post by aysiu on 2010-04-22
> **ddecator said:**
> Ubuntuzilla is not officially supported, so if you have any issues with it you will have a harder time getting help. The Ubuntu Mozilla Team PPAs are generally the better option. I have to disagree. nanotube, who maintains UbuntuZilla is very quick about answering any posts in the UbuntuZilla subforum here:
[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by nanotube on 2010-04-22
> **ddecator said:**
> Ubuntuzilla is not officially supported, so if you have any issues with it you will have a harder time getting help. The Ubuntu Mozilla Team PPAs are generally the better option.

also note that ubuntuzilla installs the official mozilla build - so if there are any problems, you could get support directly on the mozilla forums, as well, in addition to here.

that said, there's nothing wrong with firefox-stable either. ...

basically, down to your personal preference. :)

---

### Post by lovinglinux on 2010-04-22
> **ddecator said:**
> Ubuntuzilla is not officially supported, so if you have any issues with it you will have a harder time getting help. The Ubuntu Mozilla Team PPAs are generally the better option.

I disagree. I used to recommend  the Mozilla Team PPAs, but there are a few things you need to consider. For instance, last week or so, **ubuntu-mozilla-daily** pushed a broken implementation of Firefox 3.6.4pre [Lorentz], causing several browsers to crash when viewing flash content. On the other hand, **mozillateam/firefox-stable** was kept without any updates between January 24th and April 7th, thus missing critical security patches provided by Firefox [v.3.6.2](http://www.mozilla.com/en-US/firefox/3.6.2/releasenotes/).
[LIST]
[*]v.3.6, released January 21st, 2010
[*]v.3.6.2, released March 22nd, 2010
[*]v.3.6.3, released April 1st, 2010
[/LIST]

I'm not saying that those PPAs are bad. Mozilla Team actually does an awesome job providing those repositories and I use them myself. I just don't think they should be recommended for beginners, specially the **ubuntu-mozilla-daily.**

About the support, I agree with aysiu. Whenever can't help an Ubuntuzilla user to fix an issue, usually caused by the user himself, nanotube provides superb support.

So basically I believe that if the user has a 32bit system, the best option to keep Firefox updated with latest stable releases is indeed Ubuntuzilla. If the user has a 64bit system, the best option would be to download the latest release from Mozilla nightlies as soon as they are released or use the **mozillateam/firefox-stable** if the user don't mind waiting a little bit longer to get updates.

---

### Post by aysiu on 2010-04-22
Just to clarify, I'm not saying UbuntuZilla is *better* as a method than the Mozilla Team PPA. I'm saying that it's misleading to imply that UbuntuZilla has worse support. nanotube is all over those UbuntuZilla support threads, seriously.

---

### Post by nanotube on 2010-04-22
thanks you guys. :D </warmfuzzies> :)

---

### Post by Phan76 on 2010-04-22
Hey all just wanted to say thanks for posting these guides,very helpful

---

