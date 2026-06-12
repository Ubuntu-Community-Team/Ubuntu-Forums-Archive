---
title: "Weird display issue on IBM X31"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Sandwiched on 2010-10-16
Ok, first off, I know the X31 is not a netbook, but since it's an older computer, I thought trying Ubuntu Netbook Remix on it might be worth a shot.

I installed the latest version as of a few days ago, 10.10, and everything went fine as far as I could tell. Once the installation completed, it said I'd need to reboot to use Ubuntu, which I did. Once the OS loaded, the problem began appearing.

Ok, so on first load, the screen in UNR is divided into 3 (pardon me for not knowing any of the actual names): the top menu bar, the left side applications bar, and the desktop which fades in. If I move the cursor along the menubar up top, everything is fine. If the desktop doesn't have any windows or dialog boxes on it, such as wifi access code prompt, the cursor can move over that as well without any problems.

However, if I move the cursor over the side applications bar, or if there is a dialog box showing on the desktop and I move the mouse over the *desktop* (doesn't even have to be over the dialog box), or if I open a menu from the menubar and then move the mouse over the menu (away from the top bar), then the display "resets" - it flickers to black, quickly reinitializes, and the desktop fades in again. If the cursor is still over one of the areas that triggers this issue, this will happen over and over again.

The only way to stop it depends on the trigger: if it was a menu I opened, merely moving the mouse back up to the top of the screen, over the menu bar, will halt the cycle of display "resets". However, if there is a dialog box on the screen, the cycle will not halt until I manage to click the "Cancel" button in the split second it appears before the display resets again.

Finally, if I click on the Unity button on the far left side of the menu bar - the button that brings up the [Unity interface]("http://www.ubuntu.com/sites/default/files/active/maverick/U3.1_unity_medium.jpg"), then I can move the mouse over that screen without any problems.

I haven't had the courage to try launching any applications yet. ;) I did reboot into recovery mode, where I chose the failsafe graphic mode, which booted and ran just fine. It didn't load the whole Unity netbook environment, but I can't say I expected it to.

To top it all off, when I restarted from failsafe graphics mode and tried to load it normally, it loaded into the regular Ubuntu interface - Applications, Places, & System menus, etc - and the problem does not happen anymore. I suspect it's an issue with the Unity interface, since that's not loading, and the problem is not happening.

So, should I even bother trying to fix this display reset issue, or should I not expect UNR to be able to work on non-netbook chipsets?

---

### Post by schmmd on 2010-12-31
I have the same issue with my Thinkpad X31 and Ubuntu Netbook 10.10.

---

### Post by Sandwiched on 2010-12-31
FYI, I've been running the normal Ubuntu interface without any problems aside from odd coloring on the "Ubuntu" logo during boot (reminiscent of EGA color palette conversion). I had totally forgotten about this issue though (I barely use that laptop since the battery's dead), so perhaps one of the updates that have been applied in the meantime has fixed the issue. I'll have to give it a try.

---

