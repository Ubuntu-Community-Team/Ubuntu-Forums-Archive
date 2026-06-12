---
title: "File Browser/Manager Freezes"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by bthomson100 on 2010-09-02
I'm having an intermittent problem with my file manager or file browser in Ubuntu 10.4.

Every once in a while the file browser window freezes. What happens is that the top line of the file browser window disappears, i.e. the line that contains (from the left) 3 circles with x, "down arrow" and "up arrow", the name of the folder currently being viewed and the words "File Browser". In addition, this line disappears from the windows of all open programmes.

I can access the File Edit View Go Bookmarks Help line commands in the File Browser window, but cannot switch from programme to programme using the tabs on the bottom of the screen that show the programmes that are open at that moment.

The only way out of this seems to be to restart Ubuntu.

Can anyone help me with this? I am a complete Linux newbie so extreme simplicity in tips, instructions, etc. would be appreciated.

Bob Thomson, Ottawa, Canada

---

### Post by Pollox on 2010-09-04
First off, your problem is a bit unclear.  You start by saying your file manager freezes, which would mean it stops responding.  (The default file browser is called "nautilus" by the way.)  You then go on to describe the title bar disappearing from all windows, which is a completely different problem, as it has nothing to do with nautilus nor freezing.  The title bar is controlled by a "window manager", usually either compiz or metacity, depending on whether you enabled desktop effects, respectively.  Lastly, you describe not being able to switch between windows using the gnome panel (the tabs at the bottom of the screen), which seems like a different issue but could be related.

Now that you have some terminology down, determine which of these problems actually affect you:
1) nautilus freezing/not responding
2) title bars disappear
3) gnome panel stops working
Then, determine if these all seem to happen at the same time, or if they are unrelated events.  If (1) is not actually your problem, you may be best off making a new thread with a more accurate title.

---

### Post by bthomson100 on 2010-09-04
> **Pollox said:**
> First off, your problem is a bit unclear. 

Thanks for your reply Pollox. It gets me started - I hope.

> **Pollox said:**
> Now that you have some terminology down, determine which of these problems actually affect you: 1) nautilus freezing/not responding; 2) title bars disappear; 3) gnome panel stops working

They all affect me and they all occur at the same time.

> **Pollox said:**
> The title bar is controlled by a "window manager", usually either compiz  or metacity, depending on whether you enabled desktop effects,  respectively
Where would I enable desktop effects? (I did say I'm a complete Linux/Ubuntu newbie didn't I?)

When this happens, if I close the "top" open window by clicking on "file" and then "quit", it closes. I can only do this however with the "top" open window since I can't switch between windows the regular way by clicking on a visible part of them. That includes open file browser windows which I guess means that "nautilus" is still working, even if the top line of its window (which I assumed was part and parcel of the program) is gone. However, its "gnome panel" tab at the bottom stays there. I can't however open it again by clicking on the gnome panel tab and I can't close the gnome panel tab by clicking on "close" when I right-click the tab.

Does this make any sense to you? Or enough to suggest more tips on how to track this down?

Bob

---

### Post by Pollox on 2010-09-04
> **bthomson100 said:**
> 
They all affect me and they all occur at the same time.


This indicates a fairly serious problem in my opinion.  Not sure I'll be able to help you with this, but I've got a few ideas if no one else has any.

> 
Where would I enable desktop effects? (I did say I'm a complete Linux/Ubuntu newbie didn't I?)


System (on the top panel), then Preferences >> Appearance, and click the Visual Effects tab.  Probably best to set it to "none" while you're trying to figure out this problem.  On the off-chance that compiz is the problem, this should fix that.  You can also switch between compiz and metacity by typing either "compiz --replace" or "metacity --replace" in the box that appears when you press "alt+F2" (which by the way is a handy way to launch programs), but upon rebooting it will revert to your default window manager.

One other idea I have: Next time this happens, press "ctrl + alt + F1".  This will bring you to a black screen with text.  When prompted, enter your username and password.  Then run the command "top" (it's a system monitor).  Look in the %CPU column to see if there's a program using a lot of cpu, which could indicate the culprit.

Anything else you can think of that you've done since installing that might be related to this would be helpful.  You can also consider reinstalling ubuntu as an option, but that might be a bit of a hassle.

---

