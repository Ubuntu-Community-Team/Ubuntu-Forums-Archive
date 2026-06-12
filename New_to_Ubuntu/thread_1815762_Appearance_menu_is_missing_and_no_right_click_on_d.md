---
title: "Appearance menu is missing and no right click on desktop"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by BishweshJ on 2011-07-31
I can't find the appearance menu anywhere and I can't right click on the desktop. I had updated my ubuntu and this started once I restarted my Ubuntu after the updates. I have the syslog if you want me to post it.

---

### Post by glennric on 2011-07-31
Can you start a terminal?  If so run "ps aux | grep nautilus".  If a job shows up (other than the grep job) then nautilus is running.  If only the grep job appears then you need to start nautilus.  You can do this from the terminal by typing "nautilus".  Then the right click menu should work.

If nautilus is running and there is still no right click there is another problem.

---

### Post by BishweshJ on 2011-07-31
Tried to load nautilus and it says failed to load module (null).

---

### Post by glennric on 2011-07-31
Maybe try reinstalling nautilus.  From a terminal type "sudo apt-get install --reinstall nautilus"

---

### Post by BishweshJ on 2011-07-31
I reinstalled it and it still says the same thing.

---

### Post by glennric on 2011-08-01
What is the precise error that you are getting when you try to run nautilus from the terminal?

---

### Post by BishweshJ on 2011-08-01
Initializing nautilus-gdu extension```

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:2139): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:2150): Gtk-WARNING **: Failed to load type module: (null)
null)
```

This is what I'm getting.

---

### Post by glennric on 2011-08-01
Have you installed any gnome 3 components?  Or have you changed your desktop settings in any way recently?  Or installed any new packages that might be related to this issue?

---

### Post by BishweshJ on 2011-08-01
This all started when I was installing updates. Now when I try to run the updates it says that I have to run a partial update and when I try to do it nothing happens. 
Other than the updates I had installed some new themes and that's about it.

---

### Post by amjjawad on 2011-08-01
> **BishweshJ said:**
> This all started when I was installing updates. Now when I try to run the updates it says that I have to run a partial update and when I try to do it nothing happens. 
Other than the updates I had installed some new themes and that's about it.

And what release of Ubuntu are you using? that should be the first info in the first post ;)

Did you upgrade from 10.10 to 11.04?
Is this normal or Wubi Installation?

---

### Post by BishweshJ on 2011-08-01
Its a Wubi installation and my Ubuntu is 11.04 with Gnome 3.0.2.

---

### Post by amjjawad on 2011-08-01
> **BishweshJ said:**
> Its a Wubi installation and my Ubuntu is 11.04 with Gnome 3.0.2.

Wubi, ha? I'm really sorry, I have no experience with Wubi at all, that's why the 3rd link exists in my signature :)

My guess would be GNOME3 has caused something wrong but that's only a guess. I have never used GNOME3, just saw it on Fedora 15 LiveCD and that's all.

---

### Post by BishweshJ on 2011-08-03
Anyone got any idea what can I do to solve this problem?

---

### Post by josephmills on 2011-08-03
open terminal and type in ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```   anything ?

---

### Post by BishweshJ on 2011-08-03
says gnome-panel no processes found.
Also I can't choose anything in the log in screen other than my account. No other options to go classic or anything and I can't also find log in menu in the applications.

---

### Post by josephmills on 2011-08-03
> **BishweshJ said:**
> says gnome-panel no processes found.
Also I can't choose anything in the log in screen other than my account. No other options to go classic or anything and I can't also find log in menu in the applications.

wow that is not good try to reinstall gnome or kde or what ever to get you back to square 1. sounds like to might have deleted some core things some how with that update did you do a clean or auto remove or any thing like that well dosent matter how it happened just matters that it did I would reinstall gnome 3 or kde or something.

---

### Post by BishweshJ on 2011-08-03
I'm not sure how to re-install gnome 3 but I tried this:
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update

sudo apt-get upgrade
sudo apt-get install gnome-shell

And well it didn't make a difference once I restarted my computer. Also I should mention that when I try to reset Unity I get errors as well, although it successfully removes the compiz but nothing else with the themes/background.

---

### Post by amjjawad on 2011-08-03
The whole idea behind Wubi is that a user can try Ubuntu for a short time and then "install" Ubuntu if he/she likes it. Wubi not meant to be used for a long time.

If I were you, I would un-install Wubi and Install Ubuntu to the Hard Drive or even External/USB Drive.

Just a suggestion, not a solution for your current issue.

---

### Post by BishweshJ on 2011-08-03
I've used it for less than a week so I want a solution to this problem and get used to ubuntu.

---

### Post by obie17 on 2011-08-03
if you cannot open the terminal before you login, login as "ubuntu (safe mode)" then try alt+F2 then type this command** unity --reset. **

---

### Post by FluffWind on 2011-11-15
I know I'm a tad late, but I had a similar problem. 

I found this solution, and it worked just fine for me.

Using lxterminal or choosing "Run" from the menu, use:

"pcmanfm --desktop-pref" 

then click on the "Advanced" tab and uncheck "show menus provided by window managers when desktop is clicked".


I hope it helps!

---

### Post by amjjawad on 2011-11-16
> **FluffWind said:**
> I know I'm a tad late, but I had a similar problem. 

I found this solution, and it worked just fine for me.

Using lxterminal or choosing "Run" from the menu, use:

"pcmanfm --desktop-pref" 

then click on the "Advanced" tab and uncheck "show menus provided by window managers when desktop is clicked".


I hope it helps!

Hi :)

I think you are talking about Lubuntu while the OP has Ubuntu :)

---

### Post by lolpenguin on 2011-11-16
Since a "partial upgrade" was mentioned, and the last job performed was an update, run this in a terminal
```
sudo dpkg --configure -a
```
OR
```
sudo apt-get install -f
```
This should fix any broken packages (usually indicated by the "partial upgrade" message in update manager)
If this does not work it is not a problem relating to packages.

---

### Post by nothingspecial on 2011-11-16
As the OP has not returned since the beginning of August I'm locking this thread.

If the OP want's it reopened PM me.

---

