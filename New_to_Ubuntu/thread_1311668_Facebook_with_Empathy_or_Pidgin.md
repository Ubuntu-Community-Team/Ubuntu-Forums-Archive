---
title: "Facebook with Empathy or Pidgin?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by sngehl01 on 2009-11-02
How can I get my facebook chat to work with one of these programs? I'm running Ubuntu 9.10, and I have them both installed, I just can't connect to my facebook with either of them.

thanks

---

### Post by danastasio on 2009-11-02
as it stands, it is not possible to use facebook chat through empathy or pidgin nativly, but you should check this out

[http://lifehacker.com/396473/facebook-chat-plug+in-integrates-facebook-with-pidgin](http://lifehacker.com/396473/facebook-chat-plug+in-integrates-facebook-with-pidgin)

google *is* your friend

---

### Post by marshmallow1304 on 2009-11-02
```
sudo apt-get install pidgin-facebookchat
```

---

### Post by sngehl01 on 2009-11-02
> **marshmallow1304 said:**
> ```
sudo apt-get install pidgin-facebookchat
```

thanks, I was sure I could get it since I had pidgin on Vista and got facebook to work on it

i went to pidgins site and i saw the plugin, but link was broken

---

### Post by Xomm on 2009-11-02
As stated above by marshmellow1304,

You need that extra Plugin to chat with facebook.

(Beware, if you have lots of friends, it's a headache to go through all of them in that tiny Pidgin window. ;))

---> My browser lagged until after you posted. Sorry. <---

---

### Post by sngehl01 on 2009-11-02
ok now how in the world do i get it to stop alerting me when someone logs on? is there a way to turn it off, i don't want a fricken alerty everytime someone comes online, this is annoying.

---

### Post by sngehl01 on 2009-11-02
it does it when a buddy logs on with AIM or Facebook or anything, and quite frankly it's past the stage of annoying and is really ticking me off

---

### Post by sngehl01 on 2009-11-02
c'mon someone please, lol, this is driving me nuts!!!!!

---

### Post by Xomm on 2009-11-02
Heh. I've looked everywhere. I don't see it.

All I see is Mute Sound, but I'm assuming it's the messages that are annoying you.

Looking around in the notif bar now.

Will post when done.

Edit: Try removing the system tray icon. (If you don't have it anyways or it doesn't work, then never mind.)

---

### Post by Xomm on 2009-11-02
I see nothing.

I've got to go now, so, if you're going to keep looking, look in system > administration/preferences. That's the only other place I can think of.

---

### Post by sngehl01 on 2009-11-02
> **Xomm said:**
> I see nothing.

I've got to go now, so, if you're going to keep looking, look in system > administration/preferences. That's the only other place I can think of.

ok. i've been looking too. i have nothing. yeah, those pop up messages are very terribly annoying

thanks for helping, hopefully we'll be able to figure something out

---

### Post by sngehl01 on 2009-11-02
i accidently deleted the button on the top, it was like an envelope that let me quickly get to pidgin, empathy, and my email. i deleted the button from the panel. how do I get it back? I couldn't find it when i clicked "add to panel"

help

---

### Post by Xomm on 2009-11-02
I believe it's indicator applet.

---

### Post by sngehl01 on 2009-11-02
that got it. thanks!

---

### Post by marshmallow1304 on 2009-11-03
You mean the notifications in the top right?

In Pidgin, go to Tools -> Plugins and look for the "Libnotify Popups" plugin.  Either disable it or configure it to not display every time someone logs in.

---

### Post by Roinator on 2009-11-03
...nvm

---

### Post by Dapilot1 on 2009-11-05
Edit > Preferences > Sounds
Then scroll down and deselect contact goes offline/online
Thats for empathy at least

---

### Post by Dapilot1 on 2009-11-05
Edit > Preferences > Sounds
Then scroll down and deselect contact goes offline/online
At least in Empathy anyway

---

### Post by baltadt on 2009-11-05
I downloaded the pidgin facebook plugin but I don't see it as a im account. How do I set it up?

---

### Post by baltadt on 2009-11-05
nevermind I'm an idiot.

---

### Post by Odin Overland on 2009-11-06
Anyone having any trouble actually connecting to the network now?  I was prompted for confirmation exercise on Adium the other day and had a bad time connecting.  A few logins over the web took care of that for Adium, but Pidgin is still a no-go for me.  Did facebook do something to block out some chat clients - or do I just need another work-around?

---

### Post by crowdedelevator on 2009-11-06
> **Xomm said:**
> As stated above by marshmellow1304,

You need that extra Plugin to chat with facebook.

(Beware, if you have lots of friends, it's a headache to go through all of them in that tiny Pidgin window. ;))

---> My browser lagged until after you posted. Sorry. <---

please tell me how to get that plug in. i saw this and was hooked. i hate having to stay on that site to do it. and i only have 3 friends that are on at once it seems. its kind of nice

---

### Post by Odin Overland on 2009-11-06
> **crowdedelevator said:**
> please tell me how to get that plug in. i saw this and was hooked. i hate having to stay on that site to do it. and i only have 3 friends that are on at once it seems. its kind of nice

Typing this in the terminal was the absolute easiest way of all the ways I have done it in the past few days on different systems.

> **marshmallow1304 said:**
> ```
sudo apt-get install pidgin-facebookchat
```

---

### Post by Xomm on 2009-11-08
It's also under Preferences > Plugins, I believe. 

There's also a bunch more useful plugins under there, but, before telling me that some of them make no sense, they don't make sense to people who don't need them. ;)

---

### Post by rob.arntfield on 2009-11-11
Something has changed with facebook. 

The only way (for me anyways) to enable facebook chat was to remove 
the *pidgin-facebookchat 1.6.0* and head over to the google website. 

[http://code.google.com/p/pidgin-facebookchat/]("http://code.google.com/p/pidgin-facebookchat/")

Download the .deb and install it. It will warn you that you should use the older version in the repositories, ignore it and install anyways. 

Restart Empathy, problem solved.

---

