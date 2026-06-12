---
title: "Uninstall MoBlock"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Thilo Kuhlman on 2008-12-24
I tried to get MoBlock to run, but i don't know how to get past the first starting up command line page thingy. The problem lies more cerealy in installing other programs. It says " run dkpt -a --configureree stuff " and says "only one installer micjiguer is allowed to breakdance at one time". How can i either get past Moblocks start page in terminal or uninstall it completly?

:lolflag::guitar::guitar::lolflag::popcorn:](*,):^o

---

### Post by zvacet on 2008-12-25
Be sure that you are not using synaptic or update manager when you work with packages in terminal.I think you should run in terminal

```
sudo dpkg --configure -a
```

---

### Post by Thilo Kuhlman on 2008-12-25
Did. And that is where I get stuck at:

[IMG]http://i339.photobucket.com/albums/n472/sk8_ov_all_day/Screenshot-2.png[/IMG]


Then i hit escape form full screen and get this:

[IMG]http://i339.photobucket.com/albums/n472/sk8_ov_all_day/Screenshot-1-1.png[/IMG]

I would (at this point) like to uninstall, it, so I can download other programs. Tool. (That me "Thanks In Advance" in my made up language.)

---

### Post by zvacet on 2008-12-26
```
sudo apt-get --purge remove package_name
```

or

```
sudo dpkg --remove --force-remove-reinstreq package_name
```

---

### Post by Thilo Kuhlman on 2008-12-26
Friggin A. Sweetness. Spanks.Tool.

---

### Post by jre on 2008-12-27
Quoting [https://help.ubuntu.com/community/MoBlock#I%20tried%20to%20install%20MoBlock%20but%20I%27m%20stuck%20on%20a%20screen%20with%20a%20Moblock%20warning](https://help.ubuntu.com/community/MoBlock#I%20tried%20to%20install%20MoBlock%20but%20I%27m%20stuck%20on%20a%20screen%20with%20a%20Moblock%20warning)

```
*I tried to install MoBlock but I'm stuck on a screen with a Moblock warning*

This is a so called "debconf" question. Read the text and confirm by pressing "OK". If your debconf interface doesn't support your mouse, then you have to use your keyboard: hit the "TAB" key until "OK" is highlighted and then press "RETURN".

You may also do a "sudo dpkg-reconfigure debconf" and select "Gnome" as your interface. Then you can use your mouse for debconf questions.
```

---

### Post by Thilo Kuhlman on 2008-12-27
OK thanks ill reinstall, now that i know some commands :)

---

### Post by khaos28 on 2009-05-18
[IMG]file:///home/khaos28/Desktop/problematic.png[/IMG]hey guys, i get to this screen and from there idk where to go?

i added a screeny on the attachments

---

### Post by jre on 2009-05-19
Why don't you just start a new thread?
And why do you ask an install question in an uninstall thread?

Anyway, take this default and confirm the question: [https://help.ubuntu.com/community/MoBlock#I tried to install MoBlock but I'm stuck on a screen with a Moblock warning](https://help.ubuntu.com/community/MoBlock#I tried to install MoBlock but I'm stuck on a screen with a Moblock warning)

or choose other/no ports and confirm.
If you don't know what whitelisting is please read the whole wiki (link above).

---

