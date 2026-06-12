---
title: "change theme from command line"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by carrarin on 2010-09-02
is there a way to change theme from the command line. Currently my theme is Ambiance, and I would like to change it to clearlooks. I want to do this from the command line, becuase thats just badass!!

Also, is there a way to figure out what my current theme is from the command line?

THanks

---

### Post by limestone on 2010-09-02
GTK theme:
gconftool-2 --type=string -s /desktop/gnome/interface/gtk_theme Clearlooks

Metacity:    
gconftool-2 --type=string -s /apps/metacity/general/theme Clearlooks

Icons:         
gconftool-2 --type=string -s /desktop/gnome/interface/icon_theme gnome

Wallpaper: 
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/gnome.png"

---

### Post by carrarin on 2010-09-02
thanks :)

---

### Post by Dreamer Fithp Apprentice on 2011-09-11
I put the first 3 commands in a script and they work fine. Strangely, they do NOT change my custom pointer, but that's cool, I like my pointer. How can I generalize this? In other words how can I inspect a theme (eg. High Contrast Inverse) and determine what commands would duplicate the effect of System, Preferences, Appearance, theme tab, High Contrast Inverse (or whatever). Failing a general solution, how about a specific one for High Contrast Inverse or my customised High Contrast Inverse,LP (which is just HCI with the pointer made bigger)?  I intend to point launchers to two scripts to toggle between these if I can figure it out. Or better yet, is there an environment variable or something I could use to tell the script which theme is in effect and toggle to the other one so I could use one launcher instead of two?

---

### Post by Dreamer Fithp Apprentice on 2011-09-11
OK, I figured it out. Anybody else that wants to do something like this, here's how:
Look at Limestone's commands as a template and a guide to where to look in gconf-editor.
Set a theme you like and then type gconf-editor on a command line to open that program (or maybe you can add it to your menus if you use it much) Then use Limestones commands to follow down the hierarchy/tree doodad (ok, that'll make sense if you are looking at it) until you come to the value for the last argument of the command and substitute that value in the command.

I still don't know if there is an elegant way for a script to enquire what theme is in use or what these values are. Maybe they are environment variables. If nothing else, maybe I can set a variable in the same script and use some sort of conditional statement to run one or the other set of commands depending on the environment variable. But that wouldn't survive rebooting. So maybe I should have it create a file somewhere to act the same way.

---

### Post by Dreamer Fithp Apprentice on 2011-09-13
Found a lot with method above but haven't found how to change the location of the window control buttons from left to right upper corner and change them to the trad __,Square,X symbols. I'd like to modify the default theme minimally, changing only the window controls symbols and locations to make them like clearlooks. Any suggestions?

---

### Post by Dreamer Fithp Apprentice on 2012-02-20
None of this seems to work any more with the new post-Maverick interface. As far as I can tell that is because the Gnome people didn't make any effort to continue to support legacy commands in Gnome 3. Please correct me if I'm wrong. 

Am I missing something here? Is there some simple way to to change the environment, without sticking to the soon-to-be-forever-frozen-so-that-no-security-flaws-will-ever-be-fixed gnome 2, or going to Mate, the further development of which seems open to question, so that my old scripts continue to work?

Can anyone point me to a reference to equivalent command syntax that works in the current gnome panel/oneric gnome classic (no effects) environment and how to extrapolate it to different themes and theme elements?

Is there another distro that is more committed to maintaining backwards compatibility so that users don't waste time working out useful scripts that break when it is updated?

---

### Post by Dreamer Fithp Apprentice on 2012-02-26
Update: It works fine in Mate if you make some simple substitutions of program and directory names, mostly replacing "g" or "gnome" with "mate".

---

