---
title: "certain video sites not working in FF"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by tyler.mcg on 2009-07-25
still can't stream videos in firefox on certain sites?!?! I have gotten the restriced-media app.

---

### Post by pro003 on 2009-07-25
would you mind mentioning 'those sites'? maybe we can then help you.

---

### Post by tyler.mcg on 2009-07-25
[http://www.bobparsons.me/index.php](http://www.bobparsons.me/index.php)

and also redtube I noticed didn't work.

---

### Post by NESFreak on 2009-07-25
what you need is is the official adobe flash player. Not some opensource clone. Since those don't work (yet).

install flashplugin-nonfree from apt-get or synaptic, "adobe flash plugin 10" from synaptic or download it here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

also if you've got any other multimedia related problems have a look here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by QIII on 2009-07-25
And when you are done installing Flash, make sure that you REMOVE swfdec and gnash, as they will likely cause conflicts.

---

### Post by kansasnoob on 2009-07-25
Well, that's a "flash" site.

First of all is this Ubuntu Jaunty 9.04? You can be certain by going to terminal and running:

```
cat /etc/issue
```

Then also, in Firefox, type as a  URL in the address window:

```
about:plugins
```

It would then help if you clicked "select all" and then "copy-n-paste" the results here as a quote. That way we can see exactly what's installed.

We should also know what version of Firefox you're using. You can see just by clicking Help > About Mozilla Firefox.

---

### Post by tyler.mcg on 2009-07-25
ok I uninstalled gnash and swfdec but when I load FF 3.0.12 it has the same video window, I click about it says swfdec 0.8.2. I just got finished uninstalling it by going to add/remove applications. but it remains in firefox? how can I remove it?

UPDATE:
ok I checked and it says in add/remove that swfdec is still isntalled so I'm going to try removing gstreamer.

---

### Post by kansasnoob on 2009-07-25
You must restart Firefox each time you install or remove any plugin or add-on.

---

### Post by lovinglinux on 2009-07-25
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by kansasnoob on 2009-07-25
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

+1! That's well written. Kudos to you.

---

### Post by tyler.mcg on 2009-07-25
Hey lovinglinux,

thanks for your help with that. can I more quickly type sudo apt-get part everytime i go in the terminal I use that.

---

### Post by lovinglinux on 2009-07-26
> **kansasnoob said:**
> +1! That's well written. Kudos to you.

Thank you.

> **tyler.mcg said:**
> Hey lovinglinux,

thanks for your help with that. can I more quickly type sudo apt-get part everytime i go in the terminal I use that.

You are welcome.

---

