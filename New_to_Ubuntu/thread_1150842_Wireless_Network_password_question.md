---
title: "Wireless Network password question"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by adventure man on 2009-05-06
Hello :KS Every time I start up my computer and log into Xubuntu 9, my wireless network connection asks me for the password to log into my house wifi internet connection.  Any way I can store the password somewhere so that I do not receive this prompt any more?

Thanks :)

---

### Post by adventure man on 2009-05-06
Here is a screenshot of my problem, it has something to do with nm-applet and default keyring lock :confused: :

[[IMG]http://i242.photobucket.com/albums/ff89/quasimodo69/th_Screenshot.png[/IMG]](http://i242.photobucket.com/albums/ff89/quasimodo69/Screenshot.png)

---

### Post by webwiller on 2009-05-06
I need this answer too! Itìs bothering to put in a password each and every boot! Pls help!
Ty! ;)

---

### Post by Dngrsone on 2009-05-06
Try going to Preferences/Network Security and entering your password in the appropriate block under the Wireless tab.

---

### Post by webwiller on 2009-05-06
Done. Dont know if it works yet as I cant reboot now cause I'm downloading staff. Will see... ty!

---

### Post by adventure man on 2009-05-06
> **Dngrsone said:**
> Try going to Preferences/Network Security and entering your password in the appropriate block under the Wireless tab.
Where is this located (Network Security)? :confused:

---

### Post by Dngrsone on 2009-05-06
I'm sorry; that should be Network Configuration.

---

### Post by Dr.Vista on 2009-05-06
I believe that the problem is not with Network Applet itself. It's the keyring application that prompts us for this instead. This only happens, well to me in Ubuntu, when you make Ubuntu automatically sign in.

---

### Post by webwiller on 2009-05-06
Yeeh...but what's the point? If I set ubuntu to start automatically it's obviously cause I dont bother with pwd...

Any workaround than?

;)

---

### Post by Dngrsone on 2009-05-06
> **webwiller said:**
> Yeeh...but what's the point? If I set ubuntu to start automatically it's obviously cause I dont bother with pwd...

Any workaround than?

;)

The point is security.

---

### Post by Nycticorax on 2009-05-06
Right, and so how do you tell ubuntu that you're happy with the lower level of security implied by wireless activation without a password on automatic login?

---

### Post by webwiller on 2009-05-06
Yep! It works!

System>Pref>Network Config>WIreless>Click on your connection>Edit>Network Security>Put in your pwd save and exit.

Reeboot, done ;)

---

### Post by Dngrsone on 2009-05-06
> **Nycticorax said:**
> Right, and so how do you tell ubuntu that you're happy with the lower level of security implied by wireless activation without a password on automatic login?



Well, a quick [search](http://www.google.com/search?q=ubuntu+autologin+auto+keyring&ie=UTF-8) turned up [this](http://ubuntuforums.org/showthread.php?t=814582) and [this](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14).

Here's where I would normally make a snarky, sarcastic comment about people willing to play russian roulette with all their passwords, data, et al, but frankly, my heart isn't in it today-- if you want to leave yourself open to exploitation, have at.  I did my civic duty, and I won't be affected by your carelessness in any way.

---

### Post by adventure man on 2009-05-06
> **webwiller said:**
> Yep! It works!

System>Pref>Network Config>WIreless>Click on your connection>Edit>Network Security>Put in your pwd save and exit.

Reeboot, done ;)


i can't find "Pref" in System :confused:

is this different in Xubuntu?

---

### Post by Dngrsone on 2009-05-06
> **adventure man said:**
> i can't find "Pref" in System :confused:

is this different in Xubuntu?

Pref is short for **Pref**erences.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/doh.gif[/IMG]

---

### Post by adventure man on 2009-05-06
> **Dngrsone said:**
> Pref is short for **Pref**erences.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/doh.gif[/IMG]
yeah i know.  Couldn't find preferences either.

I click Applications in upper right, go to System, yet under system I do not see Preferences?  I see "Network" and "Network Tools".  I guess Xubuntu is different in this aspect? any advice?

---

### Post by Dngrsone on 2009-05-06
I guess... you see anything under Network?

---

### Post by adventure man on 2009-05-06
> **Dngrsone said:**
> I guess... you see anything under Network?
nothing :(

---

### Post by adventure man on 2009-05-12
any ideas guys on how to get automatic login on a wireless connection with Xubuntu?:confused:
I can't find this in Applications > Network :confused:

---

### Post by zim2dive on 2009-05-16
> **Dngrsone said:**
> Well, a quick [search](http://www.google.com/search?q=ubuntu+autologin+auto+keyring&ie=UTF-8) turned up [this](http://ubuntuforums.org/showthread.php?t=814582) and [this](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14).

Here's where I would normally make a snarky, sarcastic comment about people willing to play russian roulette with all their passwords, data, et al, but frankly, my heart isn't in it today-- if you want to leave yourself open to exploitation, have at.  I did my civic duty, and I won't be affected by your carelessness in any way.

Many thanks... exactly the user-friendliness I wanted from the OS... boot and connect with no typing required... when I want a forcibly paranoid OS I'll switch to Windoze.

---

### Post by Dngrsone on 2009-05-16
> **zim2dive said:**
> Many thanks... exactly the user-friendliness I wanted from the OS... boot and connect with no typing required... when I want a forcibly paranoid OS I'll switch to Windoze.

I assume you are talking about Vista... the OS that thinks that it is far preferable to give the *illusion* of security by asking for permission to do **anything** than actually *being* secure.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/doh.gif[/IMG]

---

### Post by zim2dive on 2009-05-17
> **Dngrsone said:**
> I assume you are talking about Vista... the OS that thinks that it is far preferable to give the *illusion* of security by asking for permission to do **anything** than actually *being* secure.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/doh.gif[/IMG]

LOL, yes indeed. ;)

---

### Post by adventure man on 2009-05-26
> **Dngrsone said:**
> Well, a quick [search]("http://www.google.com/search?q=ubuntu+autologin+auto+keyring&ie=UTF-8") turned up [this]("http://ubuntuforums.org/showthread.php?t=814582") and [this]("http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14").

Here's where I would normally make a snarky, sarcastic comment about people willing to play russian roulette with all their passwords, data, et al, but frankly, my heart isn't in it today-- if you want to leave yourself open to exploitation, have at.  I did my civic duty, and I won't be affected by your carelessness in any way.


dngersone hit the nail on the head with his second link.  I don't know how i missed it :confused:

anyway, thanks so much man:D

link to the answer for googlers:

[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)

---

