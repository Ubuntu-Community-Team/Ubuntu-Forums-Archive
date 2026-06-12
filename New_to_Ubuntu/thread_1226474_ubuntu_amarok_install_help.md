---
title: "ubuntu amarok install help"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by darrude on 2009-07-29
Hi,

i have been looking on Google and this forum but i'm getting confused.  I've followed a really good howto to get my ipod connected but stuck at the line 

"[COLOR=RoyalBlue]sudo apt-get install amarok libgpod3 gtkpod-aac[/COLOR]"

I do this and get the error

"[COLOR=RoyalBlue]The following packages have unmet dependencies:
  amarok: Depends: amarok-xine but it is not going to be installed or
                   amarok-engine
          Depends: kdelibs4c2a (>= 4:3.5.8-1) but it is not going to be installed
          Recommends: kdebase-kio-plugins but it is not going to be installed
          Recommends: kdemultimedia-kio-plugins but it is not going to be installed
E: Broken packages[/COLOR]"

Any advice would be appreciated.  

Do i need to change to a KDE desktop.

Sorry if these are silly question, but spent the last 2 hours on this and I've got nowhere.

I hope someone can help.

Many Thanks,

Darren.

---

### Post by metalf8801 on 2009-07-29
have you tried installing Amarok using Add/remove or Synaptic package manager? 
oh and you don't need KDE to use Amarok or at least I didn't

---

### Post by t0p on 2009-07-29
I suggest you try to install the packages that apt-get complained about not having; ie amarok-xine, amarok-engine, kdelibs4c2a and the rest.

Also, the command

```
sudo apt-get install -f
```

is used to fix broken packages.  So maybe try that.

---

### Post by achase79 on 2009-07-29
If you havn't done it recently then run ```
sudo apt-get update
```
Then try to install amarok

---

### Post by mc4man on 2009-07-29
Why don't you post what version of ubuntu your using, what version of amarok you're trying to install and maybe a link to your very good how to.

(( all those packages mentioned that aren't going to be installed are hardy versions

---

### Post by darrude on 2009-07-30
Nightmare.

I've gone down the lists installing everything it has said it needs a dependency for, and everythings gone wrong :(  re-installing as i type!](*,))

hopefully will go better this time!

Darren

---

### Post by egalvan on 2009-07-30
I used Synaptic to install amaroK on Hardy and Jaunty...

No problems at all, all dependencies were met.

No that I like amaroK all that much, but that's personal.

I miss MusicMatch v9.x on MS-Windows. The DJ function was what I need.

---

