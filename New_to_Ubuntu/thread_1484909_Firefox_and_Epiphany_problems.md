---
title: "Firefox and Epiphany problems"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by lolzwut on 2010-05-16
These are kind of un related but I figured why not just ask them in the same thread.


So first problem is that my firefox continues to close for no reason. I'll just be doing something and them BAM! it closes, I can restore my data when I restart but it's pretty annoying. I can't seem to pin point anything that's triggering that to happen. Does anyone know how I might be able to fix it?


Second problem is: after all this was happening I decided to switch to Epiphany just so I could at least use a browser comfortably until I resolved the firefox issue. So I did:

```

sudo apt-get install epiphany-browser
```
everything was fine, it didn't give me any errors. So I opened it and it has no address bar, no back button, no forward button, stop button, refersh button etc. Anyone know what that could be? Thanks.

---

### Post by lolzwut on 2010-05-16
Anyone have any ideas?

---

### Post by warfacegod on 2010-05-16
This may help for Firefox: [http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by lolzwut on 2010-05-16
Never mind I got it. You just gotta rename the .mozilla folder so it'll create a new profile.

---

### Post by lovinglinux on 2010-05-16
> **lolzwut said:**
> Never mind I got it. You just gotta rename the .mozilla folder so it'll create a new profile. Just in case anyone else who didn't get any useful replies the whole day was wondering.

If you had followed warfacegod useful suggestion, you would find this in my tutorial, along with troubleshooting steps to avoid deleting/renaming your entire profile.

Basically, I don't recommend renaming/deleting the .mozilla folder because not everyone is willing to lose all passwords, extensions, bookmarks, settings and other Firefox profile contents.

---

### Post by lolzwut on 2010-05-16
> **lovinglinux said:**
> If you had followed warfacegod useful suggestion, you would find this in my tutorial, along with troubleshooting steps to avoid deleting/renaming your entire profile.

Basically, I don't recommend renaming/deleting the .mozilla folder because not everyone is willing to lose all passwords, extensions, bookmarks, settings and other Firefox profile contents.



Yeah I read about that before I attempted it so I saved all my tabs I had open, bookmarks, add ons etc. in a text file so I could remember all the stuff I had and get it back later. My saved passwords got lost though but thankfully I remember all of them for every site I'm registered on. It seemed to fix the problem with it crashing. Thanks though!

---

### Post by lovinglinux on 2010-05-16
> **lolzwut said:**
> Yeah I read about that before I attempted it so I saved all my tabs I had open, bookmarks, add ons etc. in a text file so I could remember all the stuff I had and get it back later.

To avoid such a hassle in the future, read the [Backup](http://firefox-tutorials.blogspot.com/2010/05/backups.html) section of my tutorial.

> **lolzwut said:**
> My saved passwords got lost though but thankfully I remember all of them for every site I'm registered on. It seemed to fix the problem with it crashing. Thanks though!

If you can remember all the passwords, then you are probably using weak passwords. I would recommend using a password generator like [Password Generator](https://addons.mozilla.org/en-US/firefox/addon/12441), then use a single strong semi-readable master password for Firefox that you can remember. You might also want to export your passwords with [Password Exporter](https://addons.mozilla.org/en-US/firefox/addon/2848), although it doesn't encrypt the output file. So it is not recommended for long term storage, unless you encrypt the file yourself.

---

