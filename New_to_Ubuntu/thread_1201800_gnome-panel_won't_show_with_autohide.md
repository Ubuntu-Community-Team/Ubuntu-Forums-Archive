---
title: "gnome-panel won't show with autohide"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by zorblek on 2009-07-01
I have my panels set to autohide. For some reason, they stopped showing when I move the mouse to the edge of the screen. It used to work, but since yesterday they just don't show. The only way I can get the top panel to display is by pressing Alt+F1, which brings up the menu and the panel with it. I can close the menu and the panel will stay as long as my mouse is over it, but as soon as I move the mouse away I can't get the panel to show again. I can't get the bottom panel to show at all. Disabling autohide with gconf-editor works, but I'd like to be able to use it, as my screen is very small.

One odd thing is that I only have this problem with Compiz. If I switch to Metacity, the panels show normally. But when I switch back to Compiz, the problem persists.

I've tried restarting the computer, which usually seems to fix panel problems, but with no luck. Any suggestions would be greatly appreciated!

---

### Post by QIII on 2009-07-01
A couple of possibilities:

1.  Check that the delay in your panel settings are not some terribly long time.

2.  Try clicking on the desktop somewhere and then hover over the panels.

---

### Post by zorblek on 2009-07-01
No luck with either of those, I'm afraid. But thanks!

---

### Post by zorblek on 2009-08-06
Does anyone else have a suggestion? I've switched to awn for the moment, but I would rather be using gnome-panel.

---

### Post by zorblek on 2009-08-11
After having some problems with AWN, I'm using Gnome-Do with the Docky theme, which is okay for application launching and switching, but I still need gnome-panel for the system tray and the Gnome menu. I still haven't figured out what's preventing it from showing.

---

### Post by VCoolio on 2009-08-11
I had a similar problem where gnome-panel would only show while hovering over certain pixels, which would be a separator or icon that covered the lowest pixel line of the panel. So the pixels of the panels itself would not bring up the panel, but icons or the separator would. No solution found though, but try adding a separator and go pixelhunting. Make sure to use a theme where the separator reaches the bottom of the panel. Or increase the visible lines of the panel while "hidden" to 2 or 3. Or use xfce4-panel.

---

### Post by zorblek on 2009-08-11
I didn't have any luck with your separator suggestion. I did, however, learn something interesting and probably important: I have the exact same problem with xfce4-panel! If I set it to autohide, it won't display at all. However, pressing Alt-F4 has no effect, presumably because there is no menu built into xfce4-panel (I don't know much about xfce).

I suspect that this means the problem is with something other than gnome-panel. Compiz, perhaps?

---

### Post by zorblek on 2009-08-11
After posting that last, I had a brainstorm and have solved the problem! The problem is caused by Compiz hijacking the edge detection. To fix it, I just had to disable "Edge Flip Pointer" and "Edge Flip DnD" for the Desktop Wall plugin in CompizConfig. Problem solved!

Thanks to everyone who offered suggestions!

---

### Post by gnuts on 2009-10-29
I have also had this, and have to keep edge flip pointer diabled to have autohide  on the panels. is there a aork around to have both?

---

### Post by Weazel on 2009-11-01
Bump !! 

I'm having the same problem, and I really like Desktop Wall Edge Flip Pointer enabled, while auto hiding the gnome-panel

can anyone find a workaround for having them both ?

thanks.

---

### Post by TheReverendFlea on 2009-11-03
I'm having the same problem here, except I have Desktop Cube activated.  The panel shows when Rotate Cube is not activated, but does not show when Rotate Cube is activated.  When the Desktop Cube is activated, it deactivates the desktop wall.  I would like to have the autohide function along with the Rotating Desktop Cube.  I have deactivated the 'Edge Flip Pointer', 'Edge Flip Move', and 'Edge Flip DnD' in the Rotate Cube settings to no avail.

*edit* After a little tinkering with the Compiz settings, I changed the 'Rotate Flip Left' and 'Rotate Flip Right' to rotate at all the corners rather than the side.  The hidden panels started appearing after resetting those values

---

### Post by vermeer on 2009-12-05
I have the same issue.

But I found a compromise which is ok for me: I just disabled Edge Flip Pointer + Edge Flip Dnd, while keeping Edge Flip Move. Gnome panel shows ok. And I still can move windows around desktops.

---

### Post by MincedFeet on 2010-03-30
Anyone find any way to keep Edge Flip Pointer" and "Edge Flip DnD
"? I like both features and the autohide.

---

### Post by raydar on 2010-05-01
I'm just now getting this after a fresh install of Ubuntu 10.04 and enabling Compiz.  My top panel behaves properly on auto-hide, but my auto-hidden bottom panel is hard to trigger and hard to keep from re-hiding right after it pops up.

None of my three Edge Flip checkboxes is checked in the CompizConfig Settings Manager. The Desktop Wall and Expo options were enabled, and I've unchecked them, but to no effect on my bottom panel. What other Compiz settings or display settings could be related?  (I'm running 2 monitors from one video card, Nvidia, set to Twinview.)

---

### Post by KingJeremy on 2010-05-11
> **raydar said:**
> I'm just now getting this after a fresh install of Ubuntu 10.04 and enabling Compiz.  My top panel behaves properly on auto-hide, but my auto-hidden bottom panel is hard to trigger and hard to keep from re-hiding right after it pops up.

None of my three Edge Flip checkboxes is checked in the CompizConfig Settings Manager. The Desktop Wall and Expo options were enabled, and I've unchecked them, but to no effect on my bottom panel. What other Compiz settings or display settings could be related?  (I'm running 2 monitors from one video card, Nvidia, set to Twinview.)

I was just having this problem.  Turned out the Button Bindings I was using in CCSM with the bottom left, center, and right screen edges was preventing the panel from popping up when I'd move the pointer over it.

Check and see if you've got the bottom screen edges used in some bindings.

---

### Post by mathfeel on 2010-05-11
I was investigating this problem when I found this thread.

Seems to me edge-flip-pointer hijacks all four edges, but not the corners. So I can make my bottom panel show by using lower left/lower right corner. They are not assigned to anything.

The top edge is still hijacked by edge-flip-pointer, top-left hijacked by expose, top-right by scale.  So the hidden top panel still wouldn't show.  So I put the GNOME menu on top since it will show when I press alt-F1.

In the top panel I put soldemly used item like GNOME menu/notification area/volume control/login-out etc.  In the bottom panel I put more frequently used item like Show Desktop/Windows list/Workspace list. So this is a very nice compromise for me.

---

### Post by mrmoney on 2010-05-18
Hi,

I believe my problem is related, but I have no idea how to solve it.

With the default setup of top and bottom panels, I moved the top panel to the left and used auto-hide. From that panel I right clicked to add two new panels, neither of which displays but takes up space on my screen (when my browser is maximized, there is a gap above and below where the panels should be). Right clicking on the empty space brings up the desktop context menu though. What's more, I accidentally deleted my bottom panel.

Any idea how I can restore the default panels?

Thanks for any help

---

### Post by intosamadhi on 2010-12-27
had a similar problem. found a fix:

Under bindings in desktop wall, goto 'move within wall' and 'edge flipping' and disable Top and Bottom.

now I can have dnd and move enabled without any problem.

---

### Post by sanso on 2011-01-13
Is this a known bug? Or a feature?

Thanks for finding this out, I was very, very puzzled why suddenly I couldn't get my panel to drop down any more...

---

### Post by maytekir on 2011-02-11
Another way to show hidden panels again:
press alt+f2 and type gconf-editor and run. 
Configuration Editor will be opened; follow these directories: /apps/panel/toplevels/ click on bottom_panel_screen0 or top_panel_screen0(these are the panels, chose which is hidden)
At the right side, find the auto_hide key and change its value by unticking the value. Hidden panel will be seen now.
(sorry for bad English)

---

### Post by AmiNimA on 2011-08-04
> **TheReverendFlea said:**
> 
*edit* After a little tinkering with the Compiz settings, I changed the 'Rotate Flip Left' and 'Rotate Flip Right' to rotate at all the corners rather than the side.  The hidden panels started appearing after resetting those values

it does the trick. Thank you. disable this options in your compiz settings.

---

### Post by richardbrucebaxter on 2011-09-22
To use auto hide gnome-panels while Compiz desktop wall is activated;

CompizConfig Settings Manager - Desktop Wall - Bindings - Edge Flip
- change 'Flip up' binding from 'top' to 'none'
- change 'Flip down' binding from 'bottom' to 'none'

---

