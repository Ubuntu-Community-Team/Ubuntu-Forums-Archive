---
title: "ubuntu minimal with openbox"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-02-15
ubuntu minimal with openbox
installed ubuntu minimal install. after installing only the base system. I aptituded xorg, openbox, obconf, openbox-themes slim, firefox, xfe, synaptic, xfce4-terminal and pypanel.

The trouble I have been having so far is I need to know how to edit my openbox menu and how to autostart pypanel. It also doesn't save my session so when I try to shutdown openbox, it takes me back to command line and when I restart anything I saved in say firefox is gone.

(I don't mean to double post, this is in desktop as well, but I am sort of a beginner as well. At least I think like one. I can be Clumsy)

---

### Post by Dr Small on 2009-02-15
Do you have any login manager, such as GDM, XDM or KDM, or are you just manually starting X?

---

### Post by kansasnoob on 2009-02-15
I know this won't help much, but I tried Openbox once and decided to use IceWM.

I used this guide:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Openbox just made me crazy! Hmmmmmm, maybe I should say "crazier"!

---

### Post by llamakc on 2009-02-15
Slim is a graphical login manager.

---

### Post by LunaticHiatus on 2009-02-15
what that guy said. Slim is my log in manager. Its a graphical login manager for X. Works just like kdm or gdm. just lighter.

---

### Post by LunaticHiatus on 2009-02-15
shameless bump

---

### Post by kk0sse54 on 2009-02-15
For your openbox menu I suggest installing obmenu and obconf is another great tool for general openbox configuration.

As for Slim you need to change your config file so that the command for executing openbox is "exec openbox-session". Forgive me if I do not know the specific Ubuntu config files but for me the config file is usually /etc/slim.conf.

---

### Post by Dr Small on 2009-02-15
> **LunaticHiatus said:**
> shameless bump
Bumping every 48 hours is shameless, and permitted. Bumping every 20 minutes is not.

I edit my .xinitrc file and specify what WM I wish to load, but before that, I am executing another script which loads all of my desktop settings. Maybe you do something similar with Slim.

---

### Post by supersonicdarky on 2009-02-15
copy all defaults to your home folder (create the destination folder if needed)
```
cp /etc/xdg/openbox/* ~/.config/openbox/
```

autostart.sh: like sessions in gnome.
what mine looks like:
```
# Run the system-wide support stuff
. $GLOBALAUTOSTART
# Programs to launch at startup
ogg123 /opt/timotei.ogg &
fbsetbg `grep "^file" /home/kernel/.config/nitrogen/bg-saved.cfg | sed 's/^file=//'` &
xcompmgr -CcFf -o 0.3 &
sh /home/kernel/scripts/mv_torrents &

# SCIM support (for typing non-english characters)
export LC_CTYPE=ja_JP.utf8
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=scim
export QT_IM_MODULE=scim
scim -d &

# Programs that will run after Openbox has started
(sleep 3 && conky) &
(sleep 3 && conky -c ~/.conkyrc_mpd) &
(sleep 5 && tilda) &
(sleep 2 && scmpc) &
```
Notice the & at the end of each line, it backgrounds the task.

Menu.xml: thats where the menu is stored.
what mine looks like:
```
<?xml version="1.0" encoding="UTF-8"?>

<openbox_menu xmlns="http://openbox.org/"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://openbox.org/
                file:///usr/share/openbox/menu.xsd">

<menu id="root-menu" label="Openbox 3">
  <item label="Sw3">
    <action name="Execute"><execute>swiftweasel3</execute></action>
  </item>
  <item label="FM">
    <action name="Execute"><execute>pcmanfm</execute></action>
  </item>
  <separator />
  <menu id="internet" label="Net">
  <item label="Opera">
      <action name="Execute"><execute>opera</execute></action>
  </item>
  <item label="Epiphany">
      <action name="Execute"><execute>epiphany</execute></action>
  </item>
  <item label="Transmission">
      <action name="Execute"><execute>transmission</execute></action>
  </item>
  </menu>
  <menu id="system" label="Misc">
  <item label="Run...">
    <action name="Execute"><execute>gmrun</execute></action>
  </item>
  <item label="Steam">
    <action name="Execute"><execute>sh /home/kernel/scripts/run_steam</execute></action>
  </item>
  <item label="KjP">
    <action name="Execute"><execute>kanjipad</execute></action>
  </item>
  <item label="Nautilus">
      <action name="Execute"><execute>nautilus --no-desktop</execute></action>
  </item>
  <item label="Gnome Control Center">
      <action name="Execute"><execute>gnome-control-center</execute></action>
  </item>
  <item label="gParted">
      <action name="Execute"><execute>gparted</execute></action>
  </item>
  <item label="Baobab">
      <action name="Execute"><execute>baobab</execute></action>
  </item>
  <item label="VBox">
      <action name="Execute"><execute>VirtualBox</execute></action>
  </item>
  </menu>
  <menu id="multimedia" label="Media">
  <item label="Gnome-MPlayer">
      <action name="Execute"><execute>gnome-mplayer</execute></action>
  </item>
  <item label="Sonata">
      <action name="Execute"><execute>sonata</execute></action>
  </item>
  <item label="Vocaloid">
      <action name="Execute"><execute>wine /home/kernel/.wine/drive_c/Program\ Files/VOCALOID2/VOCALOID2.exe</execute></action>
  </item>
  </menu>
  <menu id="graphics" label="Vis">
    <item label="Nitrogen">
      <action name="Execute"><execute>nitrogen --sort=aplha /home/kernel/Walls</execute></action>
    </item>
    <item label="Photoshop">
        <action name="Execute"><execute>wine /home/kernel/ps/Photoshop.exe</execute></action>
    </item>
    <item label="Gimp">
        <action name="Execute"><execute>gimp</execute></action>
    </item>
    <item label="gThumb">
        <action name="Execute"><execute>gthumb</execute></action>
    </item>
    <item label="Picasa">
        <action name="Execute"><execute>picasa</execute></action>
    </item>
  </menu>
  <separator />
  <menu id="openbox-conf-menu" label="Conf">
    <menu id="client-list-menu" />
    <separator />
    <item label="ObConf">
      <action name="Execute"><execute>obconf</execute></action>
    </item>
    <item label="Edit autostart.sh">
      <action name="Execute"><execute>gedit /home/kernel/.config/openbox/autostart.sh</execute></action>
    </item>
    <item label="Edit menu.xml">
      <action name="Execute"><execute>gedit /home/kernel/.config/openbox/menu.xml</execute></action>
    </item>
    <item label="Edit rc.xml">
      <action name="Execute"><execute>gedit /home/kernel/.config/openbox/rc.xml</execute></action>
    </item>
    <item label="gtk">
      <action name="Execute"><execute>gtk-theme-switch2</execute></action>
    </item>
    <item label="Screenlets">
      <action name="Execute"><execute>screenlets-manager</execute></action>
    </item>
    <item label="Restart">
      <action name="Restart" />
    </item>
    <item label="Reconfigure">
      <action name="Reconfigure" />
    </item>
  </menu>
</menu>

</openbox_menu>

```

rc.xml: all other options are stored here. Too long to post what mine looks like.

More info: [http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page)

---

### Post by LunaticHiatus on 2009-02-15
thank ya much, that should be helpful

---

### Post by LunaticHiatus on 2009-02-15
I forgot to bring this up, but I'm using a wireless adepter to connect to the internet. What should I apt-get to handle that? I tried wcid but it didn't automatically recognize my wireless drivers. Which is one of the things I like about ubuntu.

---

### Post by llamakc on 2009-02-15
> **LunaticHiatus said:**
> I forgot to bring this up, but I'm using a wireless adepter to connect to the internet. What should I apt-get to handle that? I tried wcid but it didn't automatically recognize my wireless drivers. Which is one of the things I like about ubuntu.

You should use the forum's search feature to look for folks with similar hardware (network adapter) to what you have. See what solutions they have. At bare minimum you must include the type of hardware that you are using. As your post is above, all folks can do is guess.

---

