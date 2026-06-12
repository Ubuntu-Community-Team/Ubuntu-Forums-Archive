---
title: "Clipboard problems/questions reguarding firefox"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by ankspo71 on 2009-11-13
Hi Everyone,

For a long time now, I have been having trouble copying and pasting text, but only when it comes to using firefox. This applies to Ubuntu 9.10 and 9.04, and includes firefox 3.0 and greater. 

If I close firefox before I paste to a text file, the clipboard gets cleared, and I end up having nothing to paste. Copying and pasting to and from multiple tabs rarely works.
Refreshing the page I viewing clears my clipboard too. (example, if I were to copy this text, then refresh this page, and try to paste it back in, it won't work)

I think the default clipboard is xclipboard (from x11-apps). Is there a way to replace xclipboard with another clipboard? I found glipper and parcellite in synaptic but I think these only enhance xclipboard.... but I can't say for certain because xclipboard is not mentioned in their descriptions or dependency list.

Does anybody have any ideas on how I can fix the current clipboard or replace it with another? Or is their a setting in Firefox that I can change?
Thanks,
James

---

### Post by lovinglinux on 2009-11-14
As far as I know, that's the normal behavior of Firefox.

---

### Post by garvinrick4 on 2009-11-14
I just copy and paste to Tomboy notes in Ubuntu and then copy and paste when and where ever needs be. Know problems I know of.  Tomboy notes.  Applications to accessories.
If not there install.  Right click ubuntu avatar in upper left hand corner choose edit menu's
and find in accessories and check box is easy way. 

Lots of ways to keep notes for pasting, this is just mine.

---

### Post by nitstorm on 2009-11-14
Tomboy notes are the best!!! Tomboy notes rule :D

---

### Post by ankspo71 on 2009-11-14
Hi Again,

@lovinglinux,
 I was afraid that might be the case. Thanks for the reply.

@garvinrick4 and nitstorm,

Thanks for the Tomboy advice, I am working with it now. I never realised it could be as useful as a clipboard. Now I don't have to worry about losing my larger posts in forums. :D
Thanks,
James

---

### Post by WitchCraft on 2009-11-14
> **ankspo71 said:**
> Hi Everyone,

For a long time now, I have been having trouble copying and pasting text, but only when it comes to using firefox. This applies to Ubuntu 9.10 and 9.04, and includes firefox 3.0 and greater. 

If I close firefox before I paste to a text file, the clipboard gets cleared, and I end up having nothing to paste. Copying and pasting to and from multiple tabs rarely works.
Refreshing the page I viewing clears my clipboard too. (example, if I were to copy this text, then refresh this page, and try to paste it back in, it won't work)

I think the default clipboard is xclipboard (from x11-apps). Is there a way to replace xclipboard with another clipboard? I found glipper and parcellite in synaptic but I think these only enhance xclipboard.... but I can't say for certain because xclipboard is not mentioned in their descriptions or dependency list.

Does anybody have any ideas on how I can fix the current clipboard or replace it with another? Or is their a setting in Firefox that I can change?
Thanks,
James

Actually, this is a bug in GTK+. The clipboard always clears when you close the application you pasted from.
You'll have to wait until the next version of GNOME, or switch to KDE. Since KDE uses QT and not GTK, there you don't have that problem (but many others).

---

### Post by ankspo71 on 2009-11-14
> **WitchCraft said:**
> Actually, this is a bug in GTK+. The clipboard always clears when you close the application you pasted from.
You'll have to wait until the next version of GNOME, or switch to KDE. Since KDE uses QT and not GTK, there you don't have that problem (but many others).

Hi WitchCraft, 
after reading your reply, I went and tested other apps, and you're right... the clipboard does always clear when you close the application you pasted from. The problem is not just firefox. I'm marking this thread as solved now since it's something we can't fix on our own.
James

---

### Post by lovinglinux on 2009-11-14
> **WitchCraft said:**
> ...there you don't have that problem (but many others).

What other problems? I switched to KDE since Karmic Beta and it works great, better than Gnome.

---

### Post by WitchCraft on 2009-11-15
> **lovinglinux said:**
> What other problems? I switched to KDE since Karmic Beta and it works great, better than Gnome.

I find the network manager gruesome.
Automount doesn't work.
Starting takes very long.
No x-vnc, no "Connect to server" menu.
Kwrite takes long to start if I want to edit a textfile.
I can't copy/paste in the console using the convenient ctrl + shift +v/c, I have to use the horrible shift+insert.
I can't rearrange the running apps in the panel-bottom.
It shows all the gnome files with the tilde.
KDM modifies the default for gdm, too. 
I have to unlock root login in a config file, I have to search the internet for which config file that is, and root login is blocked by default.
KDE doesn't take the console default for the keyboard.
It lacks configurability.
I have to download 300 MB, for QT alone.
I haven't yet been able to figure out where to change the icons, although I'm sure it can be configured somewhere. I've to search google for THIS ?
The application's interface looks old-fashioned. Bad default theme, I assume.
You've to CLICK through the start menu, instead of mouseover.
That's very annoying.
They put so many applications in one cathegory, you've scroll through, again makes me slow and annoyed.

Though, I admit some of the KDE applications are damn good.
I assume that all I complained about could be configured, but I just don't want to waste time with that, since gnome has sensible defaults, at least mostly, and since KDE apps run under gnome, too, there's simply no point in wasting time with that bloated war-of-the-buttons-and-checkboxes-and-dropdowns interface.

---

