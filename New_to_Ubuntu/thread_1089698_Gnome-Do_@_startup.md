---
title: "Gnome-Do @ startup"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by LiviooT on 2009-03-07
I installed Gnome-Do and checked the "run at startup" box in the preferences window. Everything works just fine but everytime I boot into Ubuntu a security box pops up telling me:

> 
The application 'Do' (/usr/bin/mono) wants access to the default keyring, but it is locked


I have to enter my password so Docky can come out... and it's really annoying. Is there anything I can do so that Gnome-Do can start directly?

Thanks

Keep in mind I'm a complete novice so... :) simple solutions, please! :D

---

### Post by jpeddicord on 2009-03-07
That's a little strange, are you using any plugins for Do that require passwords?

---

### Post by LiviooT on 2009-03-07
I use a lot of plugins... some of them require passwords: gmail contacts indexer, flickr account etc... but none of them require my root password as far as I know.

What exactly should I be looking for?

---

### Post by Twitch6000 on 2009-03-07
> **LiviooT said:**
> I use a lot of plugins... some of them require passwords: gmail contacts indexer, flickr account etc... but none of them require my root password as far as I know.

What exactly should I be looking for?

I suggest doing a simple check list type thing.

Turn a plugin off restart(or log off and back in) and see if it asks for your password.

After you find the problem you can just leave that plugin off :).

---

### Post by LiviooT on 2009-03-07
that would mean restarting my computer a couple of dozen times :(

but if that is the only solution... I'll try it :) thank you :)

---

### Post by jyaan on 2009-04-13
Instead of restarting your computer, just restart X with Ctrl Alt Backspace

---

### Post by jpeddicord on 2009-04-13
> **jyaan said:**
> Instead of restarting your computer, just restart X with Ctrl Alt Backspace

Not always the best solution; this ends your session rather abruptly. Logging out and back in again is probably the better way to go about things. Ctrl-alt-bksp has been disabled in 9.04, to boot.

---

### Post by jyaan on 2009-04-13
My god, they disabled it? I'm not going to like that...

But yes, you should always close anything that might cause problems if stopped abruptly, so logging out is better overall. Sometimes I forget that not everyone has been using *nix for 5 years :P

---

### Post by directhex on 2009-04-14
Is your system configured to log on automatically?

---

### Post by d580744 on 2009-04-25
I think this is a security measure that can't be fixed easily.  But lets try.

I installed Gnome-Do and checked the "run at startup" box in the preferences window.
Then I confirmed/check boxed that it was set to autostart in my session:
 
/usr/bin/gnome-do can be added if needed to:

```
gnome-session-properties
```
or
```
xfce4-autostart-editor
```


Still on login I get /usr/bin/mono wants access to the default keyring but it is locked.


Lets get back to the problem.  I think this is really annoying too.  


This results in the entry here

```
cat /etc/xdg/autostart/gnome-do.desktop

```
```
ls ~/.config/autostart/
```

I am running xubuntu so didn't want to have to  
```
sudo aptitude install gnome-desktop
```just to fix this one annoyance.

On my straight ubuntu 9.04 laptop, this problem also exists.

  However, a similar problem existed in 8.04 for the network-manager applet.

The network-manager problem was fixed in 9.04 because despite using autologin (which never asks for my password) a pop-up for the network-manager SSID aked to allow access to the default keyring for this user session forever on the first use. I had to choose remember authorization always or something.


I am using autologin. and gnome-do /usr/bin/mono is the only autostart program I need a password for.

Once started it does remember my passwords for twitter, etc

So maybe if we can figure out how network-manager-applet fixed things we can figure out how to fix gnome-do

---

### Post by carleton on 2009-04-26
I'd also like to see a solution to this problem any takers?

---

### Post by KhaaL on 2009-05-08
i know that the microblogging plugin requires the user to type in the password. I'm still looking into if it's possible to disable the request...

---

### Post by sledhead45 on 2009-05-10
Same story for me. Running intrepid ibex and gnome-do 0.8.1.
Also, when using the docky theme I can't seem to reorder tabs in firefox. I can start reordering tabs again the moment I close docky. Though reordering firefox tabs with docky running works when you press F11 in firefox for fullscreen. This should perhaps gets its own ticket.

---

### Post by imp0steur on 2009-05-24
This solved my nm-applet problem ..
[http://ubuntuforums.org/showthread.php?t=1138099](http://ubuntuforums.org/showthread.php?t=1138099)

In case of Gnome-Do turned out it was the microblogging plugin that was causing the problem ..

I am better off without it .. anyways I use 3rd party clients like thwirl/tweetdeck .. so unless I find any fix for this I m not using it anymore.

---

### Post by ad_267 on 2009-05-24
Applications that needs to store a password will often encrypt this using your default keyring. When you log in with your password this is unlocked, but if you have autologin enabled it isn't. That's why the application asks for your password to the keyring. You can fix this by turning off autologin or setting your default keyring password to be empty.

That's the way I understand it anyways, might not be 100% technically correct.

---

