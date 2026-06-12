---
title: "Other than active toolbar, my display is negative!"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by vuarra on 2009-04-08
I know I pressed some key combination, I believe it included the <super> key.  The actual desktop is correct, and the active window border is correct, but everything is looks like a photographic negative.

Can anyone help me get things back to where they have been?

(and changing the color scheme does not help... all of them are negatives as well)

---

### Post by bumanie on 2009-04-08
Go to terminal and try > sudo apt-get --reinstall ubuntu-desktop
> sudo apt-get update
that should reinstall your desktop environment and hopefully you have everything returned to normal.

---

### Post by Hospadar on 2009-04-08
On the contrary "ubuntu-desktop" is just a package which includes as it's dependancies everything needed, so re-installing it won't really do anything.

You might try renaming your .compiz folder and restarting your desktop, that'll give you a clean slate of compiz settings. (if it doesn't work you can just name it back

From a command line:
mv ~/.compiz ~/compiz-temp

---

