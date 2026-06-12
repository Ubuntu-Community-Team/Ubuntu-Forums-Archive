---
title: "Installing Xfce and regular GNOME and returning back to UNR GNOME"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by HappyD on 2009-07-06
):P

I've installed UNR on my AA1 and it's really great, i'm really happy with it :D
But i was wondering what's Xfce like. So i wanna try it, but i have a question first.
If i like GNOME better, how can i return to the "no-desktop" GNOME (you know, the GNOME that has elements specific to UNR, like the fact that it has Desktop only as a folder)?
Will sudo apt-get remove xfce4 do it, or do i have to do something more?
Can i install regular GNOME instead of the modified one that comes with UNR?

Thanks in advance for the help! :D

---

### Post by ugm6hr on 2009-07-06
I understand that there is an XFCE-based netbook interface too.

No harm in trying; you will have the option to choose which "session" you want to use at the login screen (assuming you haven't selected auto-login).

Full gnome can be used without installing anything; just use "Switch Desktop Mode" - if you want to have the true full Ubuntu experience, install the package **ubuntu-desktop** (and remove netbook-remix if you want).

---

### Post by HappyD on 2009-07-06
Thank you for the quick reply, can you please tell me how can i get that Xfce-based netbook interface? Is there a KDE-based netbook interface?

---

### Post by ugm6hr on 2009-07-06
Never tried it myself, but this is where I heard of it:
[http://mydellmini.com/forum/ubuntu-netbook-remix/7632-xfce-its-faster.html](http://mydellmini.com/forum/ubuntu-netbook-remix/7632-xfce-its-faster.html)

---

### Post by HappyD on 2009-07-06
Thx, can you just tell me where can i find the option "Switch Desktop Mode"?

---

### Post by pizza-is-good on 2009-07-06
Use this link for when you want to remove
 
[[COLOR=#444444]http://www.psychocats.net/ubuntu/puregnome[/COLOR]]("http://www.psychocats.net/ubuntu/puregnome")
 
Xfce is nice, looks a lot like gnome, but no effects. KDE.... well, I wouldn't reccomend it.

---

### Post by pizza-is-good on 2009-07-06
> **HappyD said:**
> Thx, can you just tell me where can i find the option "Switch Desktop Mode"?
Its one of the options when you log in. I don't remember which, try them all, and find something like 'Select session'

---

### Post by ugm6hr on 2009-07-06
> **HappyD said:**
> Thx, can you just tell me where can i find the option "Switch Desktop Mode"?

In the main menu:
System -> Prefs -> Switch Desktop Mode

---

### Post by HappyD on 2009-07-06
Thanks.
Btw, i have a question and i don't want to open up a whole new topic, so i'm just gonna ask here. How can i add the Education tools menu?

---

### Post by ugm6hr on 2009-07-06
> **HappyD said:**
> Thanks.
Btw, i have a question and i don't want to open up a whole new topic, so i'm just gonna ask here. How can i add the Education tools menu?

The Main Menu auto-updates in Gnome (and XFCE).

If you install a program that has its default menu entry in Education, it will appear automatically.

You can manually add entries (if you know what you are doing) by going to System -> Prefs -> Main Menu

---

### Post by HappyD on 2009-07-06
When i installed KDE, the Education menu appeared, but when i removed KDE, the menu disappeared, as well as the programs inside it. But when i checked for, let's say, Kalzium, it was installed. How can i add the programs to the list quickly? Or can you just tell me where can i find the list of the Education programs so i can reinstall them?

---

### Post by ugm6hr on 2009-07-06
> **HappyD said:**
> When i installed KDE, the Education menu appeared, but when i removed KDE, the menu disappeared, as well as the programs inside it. But when i checked for, let's say, Kalzium, it was installed. How can i add the programs to the list quickly? Or can you just tell me where can i find the list of the Education programs so i can reinstall them?

Presumably, you removed the applications at the same time when removing KDE.

If you want them back, just install the applications separately.

Add/remove... will probably be the easiest way to search for educational programs, or if you remember them by name, use Synaptic.

If Kalzium is defintiely installed, you should be able to find it in the Main Menu editor (as previous), but it may require you to "tick" the entry.

---

### Post by HappyD on 2009-07-06
Kalzium is installed (when i typed sudo apt-get install kalzium it said that it was already installed) but it is nowhere to be found. I'll try Add/Remove. THX!

---

### Post by HappyD on 2009-07-07
Hello guys.
I finally managed to run the shiny, new Xfce interface. I wasn't happy with it so i ran Gnome. There wasn't anything except the completely empty Desktop. I ran failsafe Gnome and it worked. Well, mostly. The upper bar was missing. I erased Xfce via terminal and the rest via Synaptic. Reboot into regular Gnome and it was the same. Later, i somehow found out that i somehow wiped the FREAKING GNOME WINDOW MANAGER. WTF?!
Can anyone PLEASE help me, what should i enter to install it back? PLEASE!! :(

---

### Post by ugm6hr on 2009-07-07
```
sudo apt-get install ubuntu-netbook-remix
```

---

### Post by pizza-is-good on 2009-07-07
The same happend to me recently.
 
I don't know how I erased the manager, but I got it fixed...
 
This is the link of the thread on how I solved it.
 
[http://ubuntuforums.org/showthread.php?t=1201112](http://ubuntuforums.org/showthread.php?t=1201112)
 
Hope that helps....

---

### Post by HappyD on 2009-07-07
Thx for the link, i'm sorry, but i have no idea what to do... :/
I can't even find the .gnome folder anywhere to rename the session file.
BTW Being the n00b as i am, i typed sudo apt-get install gnome and it didn't do anything except installing all the progs and stuff i don't need (this is UNR and it came with different files than the regular Ubuntu or Gnome). So can you also tell me how can i install the UNR Gnome back? Pretty please with a watermellon on top? :)

Damn... F**k this, i think i'm gonna reinstall...

---

### Post by pizza-is-good on 2009-07-08
> **HappyD said:**
> 
i think i'm gonna reinstall...
 
I think that might be your best choice....
 
Don't worry, we all have gotten stuck at some point in time...

---

### Post by HappyD on 2009-07-09
Yeah, well, it was easy and quick. It's a relief that it isn't as Windows, there isn't that bunch of drivers, programs and anti-viruses you have to download and install, so it doesn't take you all day... It took me about half an hour :D

---

### Post by pizza-is-good on 2009-07-09
> **HappyD said:**
> Yeah, well, it was easy and quick. It's a relief that it isn't as Windows, there isn't that bunch of drivers, programs and anti-viruses you have to download and install, so it doesn't take you all day... It took me about half an hour :D
 
That's why I love Ubuntu. Its so easy to deal with. Once installed, you do have to go through all the updaes, but you can leave that to do during the night, because it requires no attention.

---

