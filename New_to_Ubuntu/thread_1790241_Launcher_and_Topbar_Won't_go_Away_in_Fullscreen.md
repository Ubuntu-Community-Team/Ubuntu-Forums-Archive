---
title: "Launcher and Topbar Won't go Away in Fullscreen"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by roololing on 2011-06-24
Whenever I try to watch a movie full screen, or try to browse Firefox full screen, the launcher comes out and stays, along with the top bar. Is there a way to make these hide while I'm on full screen programs?

Any help would be appreciated.

---

### Post by roololing on 2011-06-27
Does anyone have any ideas?:-k

I think the launcher isn't thinking of the full screen program as a window, so it doesn't hide. And the topbar may just ride along with the launcher.

Also, I can't click or do anything with the launcher or topbar.

---

### Post by wildmanne39 on 2011-06-27
> **roololing said:**
> Does anyone have any ideas?:-k
Hi, install compiz configure settings manager from software center or synaptic package manager, then open it up and click on unity plugin and set launcher to auto hide, do not disable the unity plugin or change any other settings in there or you will break unity. As for the top bar there is nothing that you can do about it as far as I know, but when I watch movies in full screen I do not have that problem so I do not know what is causing yours.

---

### Post by roololing on 2011-06-27
> **wildmanne39 said:**
> Hi, install compiz configure settings manager from software center or synaptic package manager, then open it up and click on unity plugin and set launcher to auto hide, do not disable the unity plugin or change any other settings in there or you will break unity. As for the top bar there is nothing that you can do about it as far as I know, but when I watch movies in full screen I do not have that problem so I do not know what is causing yours.
Yeah, I think the top bar is just forced out by the launcher. I'll try this when I get home. Thank you, wildmanne39.

---

### Post by roololing on 2011-06-30
Well, the launcher does hide itself like it should. But I guess I was wrong about the top panel being dragged out, because it still stays there in full screen. Also, the top panel *overlaps *the screen as if it weren't there, as opposed to just pushing it and making the screen shorter. I don't know if that matters.

This isn't only on my home laptop. The laptop I use at work does exactly the same thing.

I don't want to boot windows every time I watch a movie![-X

Thanks for the help.

---

### Post by wildmanne39 on 2011-06-30
> **roololing said:**
> Well, the launcher does hide itself like it should. But I guess I was wrong about the top panel being dragged out, because it still stays there in full screen. Also, the top panel *overlaps *the screen as if it weren't there, as opposed to just pushing it and making the screen shorter. I don't know if that matters.

This isn't only on my home laptop. The laptop I use at work does exactly the same thing.

I don't want to boot windows every time I watch a movie![-X

Thanks for the help.Hi, can you post a screenshot of the desktop while in full screen mode?

---

### Post by dFlyer on 2011-06-30
> **roololing said:**
> Whenever I try to watch a movie full screen, or try to browse Firefox full screen, the launcher comes out and stays, along with the top bar. Is there a way to make these hide while I'm on full screen programs?

Any help would be appreciated.

Sounds like unity. You might want to install ccsm which will give you the ability to hide the launch bar. When I go full screen the top panel acts as the top bar on a windows with the drop down menu and the max,min and close icons. This is normal Unity behavior.

---

### Post by roololing on 2011-06-30
> **wildmanne39 said:**
> Hi, can you post a screenshot of the desktop while in full screen mode?

Here it is. I put my cursor where it brings down the search bar and everything from Firefox, so you can see how it overlaps.

I guess it's kinda hard to notice with this screenshot, but the tabs are covered.

---

### Post by wildmanne39 on 2011-06-30
Hi, that is normal in unity when you have programs maximized. But when you watch a video on the internet in full screen mode it should cover that up. You can change it, I am trying to find the link for it. 
[http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu](http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu)
Read this link it might be what you want, I think it is from what I saw.

---

### Post by roololing on 2011-07-01
Is it normal that I can't interact with the top panel at all? Double-clicking it doesn't resize, clicking the dash button or any of the other buttons doesn't do anything, either. It's there, but if I click it, it'll click whatever's behind it, usually the tabs I can't see or nothing. I couldn't do anything with the launcher either, when it was still out.

By the way, thanks for the link wildmanne39, I've been wondering how to do that. The problem remains, though.

---

### Post by wildmanne39 on 2011-07-01
> **roololing said:**
> Is it normal that I can't interact with the top panel at all? Double-clicking it doesn't resize, clicking the dash button or any of the other buttons doesn't do anything, either. It's there, but if I click it, it'll click whatever's behind it, usually the tabs I can't see or nothing. I couldn't do anything with the launcher either, when it was still out.

By the way, thanks for the link wildmanne39, I've been wondering how to do that. The problem remains, though.
Hi, did you go into ccsm as stated in post #3 to set the launcher on the left to autohide? The top panel in natty can not be customized, it is locked that is why I gave you the link in my last post so you can change the way it works, it will no longer put open windows in the top panel they will be back on the program that is open, but I am not sure that will fix your full screen problem. Did you do a clean install or did you upgrade?

---

### Post by roololing on 2011-07-01
Yes, I set the launcher to auto-hide and it isn't a problem anymore. I followed the link you posted and changed the top panel so that menus are now on the windows, but that didn't fix my full-screen problem.

I did a clean install to 11.04 Unity on my **work** laptop. I did a clean install to 11.04 Gnome and then upgraded to 11.04 Unity on my **home** laptop (not sure if that counts as a clean install). The problem is the same on both laptops.

---

### Post by roololing on 2011-07-01
Also, when I say full-screen, I mean the full-screen you get when you press  F11, not just maximizing windows. Just to clarify.
> Originally Posted by **dFlyer**:
*Sounds like unity. You might want to install ccsm which will give you  the ability to hide the launch bar. When I go full screen the top panel  acts as the top bar on a windows with the drop down menu and the max,min  and close icons. This is normal Unity behavior.*When I'm in full-screen, there are no close, min, or max buttons. The menus never show up in full-screen either, even after I followed the instructions at the link [http://askubuntu.com/questions/10481...plication-menu]("http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu").

---

### Post by wildmanne39 on 2011-07-01
> When I'm in full-screen, there are no close, min, or max buttons. Hi, when firefox is open have you tried f11.

---

### Post by roololing on 2011-07-01
> **wildmanne39 said:**
> Hi, when Firefox is open have you tried f11.
Yes, I cant move, min, or max Firefox unless I press F11 to get out of full-screen.

---

### Post by wildmanne39 on 2011-07-01
> **roololing said:**
> Yes, I cant move, min, or max Firefox unless I press F11 to get out of full-screen.Hi, I just checked mine and when I hit f11 if I move my cursor all the way to the top of the screen I can watch it put my buttons back on firefox, if that does not work for you, I think I saw another method of getting the buttons back, I will see if I can find it.

---

### Post by roololing on 2011-07-01
No, that doesn't work for me. The top panel doesn't interact at all with the mouse. Moving the mouse there doesn't do anything, and the mouse clicks *under *it, as if it wasn't there.

Again, thanks for your help.

---

### Post by wildmanne39 on 2011-07-01
> **roololing said:**
> No, that doesn't work for me. The top panel doesn't interact at all with the mouse. Moving the mouse there doesn't do anything, and the mouse clicks *under *it, as if it wasn't there.

Again, thanks for your help.Hi, I have done some research, try this. Check the setting window decorations in compiz setting manager,type window decorations in the filter window and see if the window decorations plugin is checked if not check it. If you do not have compiz setting manager installed you can install it with the software center by typing ccsm and then click to install.

---

### Post by UmlautBanana on 2011-07-03
Not to hijack someone else's thread, but I have the exact same problem and it only started happening today. Window Decoration is checked (without it, I don't have bars on windows at all).

---

### Post by wildmanne39 on 2011-07-03
> **UmlautBanana said:**
> Not to hijack someone else's thread, but I have the exact same problem and it only started happening today. Window Decoration is checked (without it, I don't have bars on windows at all).
Hi, please start your own thread with a good title and include a screenshot, what version of ubuntu you are running and system specs, and any other relative information you have.

---

### Post by UmlautBanana on 2011-07-03
I was going to do that, but I have the exact same problem on the exact same version of the exact same distro, and I took the exact same steps as specified in this thread and still have the exact same problem. Another thread would clutter the forums and be redundant.

Anyway, I also tried configuring Window Decoration in CCSM so they would only show on non-fullscreen windows by changing "any" to !(state=fullscreen), but it didn't work.

---

### Post by roololing on 2011-07-06
I'm starting to think this problem is unfixable... maybe some update of compiz or ubuntu will solve the problem, but I don't understand why it wouldn't happen to everyone. Just my two laptops and UmlautBanana's computer.

Maybe I'm stuck with watching movies on Windows, at least for now. Thank you for your help, though.

---

