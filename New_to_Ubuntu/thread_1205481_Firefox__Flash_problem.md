---
title: "Firefox / Flash problem"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by jonathanfrost on 2009-07-06
I need some serious help. Most websites i go to like Myspace or Youtube show this grey box with a play button in it but when i hit the play button nothing happens and i have the latest flash player i think. Can some one please help? id appreciate a message on my messengers or a reply here. Thanks

---

### Post by Crafty Kisses on 2009-07-06
The first question is, are you running 32-bit or 64-bit Ubuntu? I'm just going to guess you're running 32-bit. If you're not sure if you have Flash installed, you can always go into Firefox and type the following in the navigation bar:
```
about:plugins
```
That will tell you if you have Flash installed. If it says Flash is not installed, try running the following command:
```
sudo apt-get install ubuntu-restricted-extras
```
You may also need to refresh the page a couple of times, I've found that I have this issues sometimes, I just refresh like 3 times, and it works perfectly.

---

### Post by sadaruwan12 on 2009-07-06
Yes 'cos Flash is not a free plugin like most of them out there the ubuntu extras are some times needed but if this doesn't work out got System -> Administration -> Software Sources then from the third party tab select all of the repositories there except for the CD rom and try doing it again.

---

### Post by jonathanfrost on 2009-07-06
I need some serious help. Most websites i go to like Myspace or Youtube show this grey box with a play button in it but when i hit the play button nothing happens and i have the latest flash player i think. Can some one please help? id appreciate a message on my messengers or a reply here. Thanks

---

### Post by zeroseven0183 on 2009-07-06
I would assume, as you said, that you already installed the [latest Adobe Flash player]("http://get.adobe.com/flashplayer/otherversions/"). Have you restarted the broswer or your machine already?

---

### Post by jman6495 on 2009-07-06
you are using a different player to try and play flash
go to tools > Addons >Plugins and disable all other media plugins

---

### Post by jonathanfrost on 2009-07-06
i get video on youtube but the picture is really choppy. one moment its standing still then when i scroll a bit it skips ahead to the middle of the song and no music any idea on how to fix?

---

### Post by s.fox on 2009-07-06
Hi,

Clicking anywhere on the video "time line" will make it skip to the point where you clicked.  I sometimes have the problem where the video seems to stop loading.  I tend to solve this by refreshing the page.  

-Silver Fox

---

### Post by lovinglinux on 2009-07-06
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

> **lovinglinux said:**
> 

**Symptoms:**

[B][list][*] Can't play streaming videos
[*] Flash videos display only a symbol and won't start[/list][/B]
**Solution:**

Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



---

### Post by DeanoCYM on 2009-07-06
I had a similar problem because I had more than one flash pluign installed. This solved it for me:

```

sudo apt-get update
sudo apt-get autoremove gnash adobe-flashplugin
sudo apt-get install flashplugin-nonfree

```

---

