---
title: "Synaptic woes - Unresolved dependencies"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by snowbalance on 2009-01-20
I'm sorry that my first post is asking for help, and I need someone to be pretty basic with me, as I only first began using Linux/Ubuntu yesterday.  I've browsed around but no luck so far.  I want to genuinely understand what it is that's going wrong.  Anyhoo.

I'm trying to install VLC via Synaptic, but this is what's happening:

1) I mark the item for installation
2) "Mark additional required changes?" comes up - "to be installed" and a few items.
3) THEN...

Could not mark all packages for installation or upgrade.  The following packages have unresolved dependencies.  Make sure that all required repositories are added and enabled in the preferences.

```
vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libtar  but it is not installable
 Depends: libvcdinfo0 (>0.7.23) but it is not installable
 Depends: libvlc0 but it is not going to be installed
 Depends: libwxbase2.6-0 (>=2.6.3.2.1.5ubuntu6) but it is not installable
 Depends: libwxgtk2.6-0 (>=2.6.3.2.1.5ubuntu6) but it is not installable
 Depends: libxosd2 (>=2.2.13) but it is not installable
```

I'm using 7.04 Feisty Fawn.  Here's what I've tried:
-System>Admin>Software Sources, all are ticked except for 'source code'

Tried sudo apt-get upgrade.  Here's what I got for that:
```
jillian@LILITH4:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I read about shutting down package processes (am I calling it the right thing?) before attempting to install from Synaptic, but I'm not sure what those processes are.  Here is a screen shot of my running processes: [http://i41.tinypic.com/2vnju4k.png](http://i41.tinypic.com/2vnju4k.png)

Thanks so much in advance (and dumb it down for me ;))

---

### Post by diablo75 on 2009-01-20
Hmmm... Try typeing this into a terminal window:

```
sudo apt-get install vlc
```

And copy the output into a reply in this thread.  Also, make sure Synaptic is closed before doing this or it won't work.

---

### Post by snowbalance on 2009-01-20
```
jillian@LILITH4:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6.release-0ubuntu4.2) but it is not going to be installed
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6.release) but it is not going to be installed
       Depends: libwxbase2.6-0 (>= 2.6.3.2.1.5ubuntu6) but it is not installable
       Depends: libwxgtk2.6-0 (>= 2.6.3.2.1.5ubuntu6) but it is not installable
       Depends: libxosd2 (>= 2.2.13) but it is not installable
E: Broken packages
```

:-?

---

### Post by jrusso2 on 2009-01-20
Feisty is out of support.  The repository is gone.  Try something newer would be my suggestion.

Either Hardy LTS, or Intrepid 8.10

---

### Post by snowbalance on 2009-01-20
> **jrusso2 said:**
> Feisty is out of support.  The repository is gone.  Try something newer would be my suggestion.

Either Hardy LTS, or Intrepid 8.10
I have 8.10 downloaded and onto a disc.  I'm sorry if this is a stupid question, but how would I upgrade without starting over with a fresh install?

---

### Post by jrusso2 on 2009-01-20
Well you have to upgrade in steps so you would probably need the Gutsy CD, Then Hardy CD then Intrepid.

Easier to start clean.  Hope you have your own /home

---

### Post by diablo75 on 2009-01-20
The easiest way to update to the next version up is to open a terminal and type:

```
sudo update-manager -d
```

But it will take a long time.  Fair warning.  It literally would be faster to backup your important data and start fresh with 8.10, because you'd have to use the above command 3 times to get up to speed, and there's a chance you'll hit a snag along the way.

---

### Post by dmizer on 2009-01-20
Just slap the disk in, and it will ask you if you want to upgrade. Say yes, and the rest of the process will be automatic.

---

### Post by jrusso2 on 2009-01-20
> **diablo75 said:**
> The easiest way to update to the next version up is to open a terminal and type:

```
sudo update-manager -d
```

But it will take a long time.  Fair warning.  It literally would be faster to backup your important data and start fresh with 8.10, because you'd have to use the above command 3 times to get up to speed, and there's a chance you'll hit a snag along the way.

Since the Feisty repository is gone people seem to not be able to do this method.  That's why I did not suggest it.

---

### Post by diablo75 on 2009-01-20
This will only work if it's the Alternate CD, and again you'd have to upgrade from 7.04 directly to 7.10 directly to 8.04 directly to 8.10.  I wouldn't do it if I were you.

---

### Post by snowbalance on 2009-01-20
> **jrusso2 said:**
> Well you have to upgrade in steps so you would probably need the Gutsy CD, Then Hardy CD then Intrepid.

Easier to start clean.  Hope you have your own /home
I don't know what you mean by /home (forgive me!), but I only switched from Windows yesterday, so I don't have much to lose.  If it's easier to do a fresh install, I'll do that.  Thanks for being patient with me :)

---

### Post by dmizer on 2009-01-20
> **jrusso2 said:**
> Well you have to upgrade in steps so you would probably need the Gutsy CD, Then Hardy CD then Intrepid.

Easier to start clean.  Hope you have your own /home

If you do not have a /home partition, you can create one: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jrusso2 on 2009-01-20
> **snowbalance said:**
> I don't know what you mean by /home (forgive me!), but I only switched from Windows yesterday, so I don't have much to lose.  If it's easier to do a fresh install, I'll do that.  Thanks for being patient with me :)

/home is a partition that houses all your application settings saving a lot of time and other configurations.

But I would just install clean since you don't have anything to lose it appears go with 8.04 or 8.10

---

### Post by dmizer on 2009-01-20
> **snowbalance said:**
> I don't know what you mean by /home (forgive me!), but I only switched from Windows yesterday, so I don't have much to lose.  If it's easier to do a fresh install, I'll do that.  Thanks for being patient with me :)

If you can easily backup, then your best bet will be to start from scratch with 8.10

---

### Post by snowbalance on 2009-01-20
Cheers everyone.  Glad to see it's something as simple as an upgrade (this time!).  I'll just do this then... and probably be back with more questions (: Thanks again.

---

### Post by zvacet on 2009-01-20
First of all delete current Ubuntu install and do ffresh install of Hardy (because it is** L**ong **T**erm **S**upport) or Itrepid if you want latest.Back to your question.To install VLC you have to go in system>admin software sourses>Under Ubuntu check all except sources and under third party check first two.Refresh and you will be able to install VLC and more other things.

---

### Post by eclark on 2009-01-23
> **jrusso2 said:**
> Feisty is out of support.  The repository is gone.  Try something newer would be my suggestion.

Either Hardy LTS, or Intrepid 8.10

Glad to know what the problem was. I just installed Xubuntu 7.04 on my Thinkpad 600E and will try to update as indicated on their website. 

release schedule: ([http://ubuntuforums.org/showthread.php?t=808376](http://ubuntuforums.org/showthread.php?t=808376))
> A new Ubuntu version is released every 6 months. Each new version is supported for 18 months on the desktop (I can't remember how long for the server). However, every 4th release is a LTS (long-term support) release. The LTS release is supported for 3 years on the desktop.

Hardy (8.04) is LTS and supported until April 2011
Gutsy (7.10) is supported until April 2009
Feisty (7.04) is supported until October 2008
Edgy (6.10) was supported until April 2008
Dapper (6.06) is LTS and supported until June 2009

Intrepid (8.10) will be released in October 2008 and supported until April 2010

---

