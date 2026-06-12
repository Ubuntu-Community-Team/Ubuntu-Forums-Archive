---
title: "[SOLVED] Question concerning Cairo-dock's autohide and custom icons"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-12-16
I tried looking for a solution to this but I'm either blind or there isn't one so I apologise in advance.  I just recently switched from AWN to Cairo-Dock and I'm very pleased with it except for 2 minor but annoying issues.

1. In AWN when a had a fullscreen application up, it would cover up the dock and then only reappears when I move my cursor to the bottom of the screen.  And when I didn't have a fullscreen application running the dock was visible.  I've tried playing around with the "Autohide" button in Cairo but it's always hiding even when there are no applications running.  Can I get this same setting as in AWN where the dock is always visible unless there is an application running in fullscreen?

2. I have a variety of icons that I would like to use to customize my Cairo-dock much like AWN.  I've successfully changed most of my icons to my liking by simply right-clicking on the desired icon---> Modify this launcher---> then opening the path of the desired icon.  Easy enough.  But for some reason there are some icons such as "calculator" that I cannot modify this way.  The calculator just stays the same boring icon as you can see from the screenshot. Is there an alternative?  

Thank you for your help!!

---

### Post by FAMUgolfer on 2008-12-16
Okay....well I just did it the hard way instead of the 'ol drag-and-drop method.  

**For custom icons** just right-click anywhere on the dock and select "add a manual launcher". Then type the path of the desired application under "command to launch on click" (ubuntu it is usually found within usr/bin/<your application>.....in my case it was usr/bin/gcalctool.  Then choose the desired icon by selecting the path of your icon.  Don't forget to type in the name of your new launcher!!! 


**For my autohide situation** I again right-clicked anywhere on the dock and selected "cairo--->configure".  Under the postion tab I deselected the "autohide" box and selected the two options below it.  In AWN all you had to do was move your cursor near or below the dock for it to appear.  In Cairo you need to go to the bottom edges of the screen (right or left) in order for the dock to appear.  A little annoying but hey it works!!

---

### Post by fabounet on 2008-12-17
you are probably using the LocalIcons theme (see in the Icons tab), it is located in ~/.config/cairo-dock/current_theme/icons
if it is on the top of the themes list, icons will be taken from it.
so just remove it from the list, or manually delete/replace icons you don't want.

---

