---
title: "how to set keyboard shortcut for system monitor"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by hogarth on 2009-06-09
Hey everyone,

I looked around and couldn't find a specific answer to this problem, so i thought i'd just ask -- if it's already been answered, i apologize. So i'm new to Ubuntu (i'm using version 8.04 with gnome) and the first thing i looked for was a task manager like in Windows. I was thrilled to find the Gnome System Monitor, which i think is lightyears ahead of its microsoft counterpart. Anyway, i pinned it to the panel (or whatever the terminology is for that), but wasn't satisfied -- i guess you could say i'm addicted to the Control-Shift-Escape method of bringing up the task manager. After a google search and looking at some forum posts elsewhere, i came upon something that suggested using keybinding commands in the Configuration Editor. It provided a pretty straightforward example, and i tried it out (using the command and target app that i wanted).

Here's what i did:
  a) changed value of /apps/metacity/keybinding_commands/command_1 to 'gnome-system-monitor' (without the quotes)
  b) changed value of /apps/metacity/global_keybindings/run_command_1 to '<Ctrl><Shift>Escape' (again w/o the quotes)

Needless to say, it didn't work. I also tried using '/usr/bin/gnome-system-monitor' for the value of command_1 (thinking that maybe the config editor required an exact pathname for the target program), but that didn't work either. I've heard that i could use a different desktop environment (perhaps one that's works nicer with making quick shortcuts), but i'd rather stick with what i got (gnome) and just try and make it work.

Sorry that's kinda long. If you can let me know where i went wrong or what other options i have, that would be greatly appreciated.

Thanks

---

### Post by nandemonai on 2009-06-09
Ubuntu 9.04

System -> Preferences -> Keyboard Shortcuts

Hit the add button, name it System Monitor or some such and for the command use:

```
gnome-system-monitor
```

Once it's added, click the shortcut tab of the shortcut you just added where it says disabled and enter the key combo you want to use.

Viola! :)

---

### Post by hogarth on 2009-06-09
Hey sorry, i'm using 8.04. Thanks though.
Got any other suggestions?

---

### Post by nandemonai on 2009-06-09
> **hogarth said:**
> Hey sorry, i'm using 8.04. Thanks though.
Got any other suggestions?

Ah, I should have noticed that. I believe that the option is still there in 8.04 but 'think' it's just a different layout. I could be wrong but worth checking out.

---

### Post by hogarth on 2009-06-09
> **nandemonai said:**
> Ah, I should have noticed that. I believe that the option is still there in 8.04 but 'think' it's just a different layout. I could be wrong but worth checking out.

In 8.04 you can still access Keyboard Shortcuts via System > Preferences, but there is no "add" option; you can only edit the shortcuts for the existing commands.
Bummer.

---

### Post by Dadsgé on 2009-06-09
also using 8.04 here
if you have compiz, you can use the key-binding option in there
system>preferences>advanced desktop settings
then go to "general options" just at the top
2nd tab: commands

i tried it and it works ;)

---

### Post by Johan-Steyn on 2009-06-09
Hi,

Instead of a keyboard shortcut, you could also opt for a icon on the taskbar.

Just right click on the taskbar (top or bottom) and click on Add to Panel.

You will get a menu with icons. Double click Application Launcher...

Scroll down to the bottom and click on the expand arrow in front of the Administration button. Highlight System Monitor and click on add. A Green System Monitor icon will be on the taskbar. Just click to launch.

Regards,


JS

---

### Post by hogarth on 2009-06-09
> **Dadsgé said:**
> also using 8.04 here
if you have compiz, you can use the key-binding option in there
system>preferences>advanced desktop settings
then go to "general options" just at the top
2nd tab: commands

i tried it and it works ;)

I just installed compiz and gave it a try, but still no luck. Don't know what i'm doing wrong... Can you tell from the attached screenshot? Also, i've noticed that if i type "<Ctrl><Shift>Escape" it's automatically replaced with "<Shift><Control>Escape" (don't know if that makes a difference, cuz i've tried those three commands in all possible combinations).

[quote=Johan-Steyn]Instead of a keyboard shortcut, you could also opt for a icon on the taskbar.[/quote]
Yeah, i already have it on the taskbar; thanks though. I'm just addicted to using Ctrl-Shift-Esc (for windows task manager) and thought it'd be simple to bring up the gnome system monitor with that key-combo... but it turns out i'm too daft :)

---

### Post by ecmatter on 2009-06-09
1. Press **Alt-F2**
2. enter **gconf-editor**
3. go to **apps > metacity > global_keybindings > run_command_1**
4. right click **run_command_1**, choose **edit key** and edit the value to the desired shortcut
5. goto **apps > metacity > keybinding_commands > command_1**
6. right click **command_1**, choose **edit key** and edit the value to **gnome-system-monitor**

---

### Post by hogarth on 2009-06-09
> **ecmatter said:**
> 1. Press **Alt-F2**
2. enter **gconf-editor**
3. go to **apps > metacity > global_keybindings > run_command_1**
4. right click **run_command_1**, choose **edit key** and edit the value to the desired shortcut
5. goto **apps > metacity > keybinding_commands > command_1**
6. right click **command_1**, choose **edit key** and edit the value to **gnome-system-monitor**

That's what i initially tried. Still don't know why it's not working.

---

### Post by abhiroopb on 2009-06-09
try this...

set the run_command_1 to a shortcut like the letter: "A"

If it works then you know there may be a problem with the shift or control or escape keys, if it does not work then make sure that gnome-system-monitor is functioning (type it into a terminal and see if it opens up).

You can also try other keybindings and see if they work as well.

---

### Post by ecmatter on 2009-06-09
I changed mine to **<Control><Shift>Escape** and it still works.  Are you capitalizing Control, Shift, and Escape?

---

### Post by hogarth on 2009-06-09
> **abhiroopb said:**
> try this...

set the run_command_1 to a shortcut like the letter: "A"

If it works then you know there may be a problem with the shift or control or escape keys, if it does not work then make sure that gnome-system-monitor is functioning (type it into a terminal and see if it opens up).

You can also try other keybindings and see if they work as well.

Guess i should've thought of that. I set it to "<Ctrl><Shift>m" and then it works fine. Thanks for the help! :D

The escape key on the keyboard works, so i guess the keyboard shortcuts don't play nice with the escape key or something (i have no idea). I suppose i can put up with not having my Ctrl-Shift-Esc shortcut.

Thanks everyone

---

### Post by hogarth on 2009-06-09
> **ecmatter said:**
> I changed mine to **<Control><Shift>Escape** and it still works.  Are you capitalizing Control, Shift, and Escape?
Yeah i was. I spelled it out exactly like you have it and it simply didn't work.
Maybe my computer just hates me -- it wouldn't be the first :)

---

### Post by abhiroopb on 2009-06-09
Perhaps there is a special way your escape key is called (e.g. ESC). Not sure how to check this though.

I have mine set to Ctrl+alt+del (reminds me of windows!)

glad to have helped!

---

### Post by ecmatter on 2009-06-09
> **hogarth said:**
> Maybe my computer just hates me -- it wouldn't be the first :)

It's a bug.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/176195](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/176195)

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/158855](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/158855)

I'm not running compiz.  That's why it works on my system.

---

### Post by tojonukokhadush on 2012-12-24
i want the name of that font in the screenshot! please!!

---

