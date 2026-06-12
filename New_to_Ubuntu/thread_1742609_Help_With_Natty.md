---
title: "Help With Natty"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-04-29
Ok so i just installed Natty and it worked great. I was messing around with compiz and I hit restore to defualt settings. Now my ubuntu just shows the desktop background with no toolbars or unity. I tried to hit alt f2 and that didnt bring anything up.  How can I go about fixing this, or will I have to reinstall Natty?  Thanks

---

### Post by cariboo on 2011-04-29
Make sure you have Unity enabled in compizconfig-settings-manager.

---

### Post by hunter99507 on 2011-04-29
Right now all I have is a desktop with no toolbars. I can't get to compiz because all I have is a blank background. Any suggestions?

---

### Post by sikander3786 on 2011-04-29
> **hunter99507 said:**
> Right now all I have is a desktop with no toolbars. I can't get to compiz because all I have is a blank background. Any suggestions?
Right click your desktop and 'Create Launcher'. Name it whatever and the command will be

```
/usr/bin/ccsm
```

Close the window and double click the new launcher. Then search for 'Unity plugin' and enable it.

---

### Post by nomekop on 2011-05-06
[COLOR=#000][FONT=times new roman]the same thing happened to me and i think i have your solution 
(or at least this is what work for me)

boot up in **Ubuntu classic** and go to **system** -** administration** - **synaptic package manager**
remove anything that has to do with **compiz** (or anything that has compiz in the name)

now restart your computer and boot up in** Ubuntu **and press **ctrl alt t** and your terminal should come up type in this line **sudo apt-get install compiz** then press enter after that type in this line **sudo apt-get install unity** press enter then **sudo apt-get upgrade unity**

after its done restart your computer and boot in to **ubuntu** and bam everything is back[/FONT][/COLOR]

---

