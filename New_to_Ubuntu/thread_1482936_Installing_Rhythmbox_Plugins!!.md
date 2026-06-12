---
title: "Installing Rhythmbox Plugins!?!"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2010-05-14
hi...

recently i moved from Songbird to Rhythmbox...

i'm having trouble installing additional plugins for rhythmbox...

i cant find this directory, says it doesnt exist **~/.gnome2/rhythmbox/plugins**

instead i found **/tmp/context/usr/lib/rhythmbox/plugins** and copied the files in a tar file in that folder... but its not working... i dont see that plugin in Edit->Plugins...

what shall i do... i'm on lucid...

i was following this page [http://code.google.com/p/albumartsearch/](http://code.google.com/p/albumartsearch/)

---

### Post by randolf_ambrose on 2010-05-14
i found this directory **/usr/lib/rhythmbox/plugins** permission denied...

do i really have to log in as root to do this or is there any other simple way???

---

### Post by dearingj on 2010-05-14
> **randolf_ambrose said:**
> hi...
i cant find this directory, says it doesnt exist **~/.gnome2/rhythmbox/plugins**
[/url]

That is the directory you want; you'll have to create it yourself. Open up your home folder, enable "Show hidden files" on the view menu (the dot in .gnome2 makes it a hidden folder), navigate to .gnome2/rhythmbox (creating the rhythmbox folder if necessary), and create the plugins folder.

---

### Post by GSF1200S on 2010-05-14
Wow, cool plugin.. never even seen it before. Installed ;)

Heres what you do. Download the package to /home. Open with your archive manager and extract the folder to /home. Then open nautilus as root:
```
gksu nautilus /usr/lib/rhythmbox/plugins
```

Open another instance of Nautilus (or use split view) and copy the folder you extracted from the tarball. Then go to the root instance of nautilus and right click>paste. After done, close and reopen rhythmbox. For some reason, everytime I add a plugin, Rhythmbox never works the first time, so I have to close it and reopen again.

Plugin is working for me..

**EDIT** Make sure you go to Edit>Plugins and enable the "Album Art Search Panel" checkbox in order to use.

---

### Post by ajgreeny on 2010-05-14
You will have to make the /home/*username*/.gnome2/rhythmbox/plugins directory yourself if it is not already there and then it all should work OK.

---

### Post by randolf_ambrose on 2010-05-14
oh... lemme try making that directory then!!! brb!!

---

### Post by randolf_ambrose on 2010-05-14
> **GSF1200S said:**
> Wow, cool plugin.. never even seen it before. Installed ;)

Heres what you do. Download the package to /home. Open with your archive manager and extract the folder to /home. Then open nautilus as root:
```
gksu nautilus /usr/lib/rhythmbox/plugins
```

Open another instance of Nautilus (or use split view) and copy the folder you extracted from the tarball. Then go to the root instance of nautilus and right click>paste. After done, close and reopen rhythmbox. For some reason, everytime I add a plugin, Rhythmbox never works the first time, so I have to close it and reopen again.

Plugin is working for me..

**EDIT** Make sure you go to Edit>Plugins and enable the "Album Art Search Panel" checkbox in order to use.

worked!!! :)

like you said, i also had to restart rhthmbox... but thats fine...

now its working!!! thanks!!!

and take a look at this... [http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty)

---

### Post by randolf_ambrose on 2010-05-14
[B]@dearingj
@ajgreeny[/B]

i tried to find/make the .gnome2 directory... it wasnt there and couldnt make it(permissions)... before entering as root, i tried the other way and it worked!!!

thanks for the help... :)

---

### Post by ottabaub on 2010-06-01
I'm running Ubuntu 10.04. I had no trouble getting the *Repeat One Song* plugin to work for me. Here's what to do step-by-step:
[LIST=1]
[*]Click **Places-->Home Folder**. Opens *Home Folder* in *Nautilus*.
[*]**Ctrl-h** to view hidden stuff.
[*]Double-click the **.gnome2** folder to open it.
[*]Right-click in list pane.
[*]Select **Create Folder** from pop-up menu.
[*]Name folder *rhythmbox*.
[*]Open **rhythmbox**.
[*]Double-click on new folder and, similarly to previous steps, create folder *plugins*.
[*]Close *Nautilus*.
[*]Run **rhythmbox**. If it loads as a little icon in Panel, left-click the icon and select **Show Rhythmbox**.
[*]Click **Edit-->Plugins**.
[*]Scroll down the plugin list until you get to **Repeat One Song**.
[*]Click on the **Enabled** checkbox to select it.
[*]Click the **Close** button.
[/LIST]
That should do it for ya. :KS

---

### Post by randolf_ambrose on 2010-12-14
COOLEST RHYTHMBOS PLUGIN EVER!!!

FULLSCREENVIEW

[http://code.google.com/p/rhythmbox-fullscreen-plugin/](http://code.google.com/p/rhythmbox-fullscreen-plugin/)

---

