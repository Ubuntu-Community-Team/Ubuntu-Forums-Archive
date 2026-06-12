---
title: "Unity -- where is the taskbar?"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by evouga on 2011-05-01
I just upgraded to 11.04 and am getting used to the new layout, but can't figure out where (or how to enable) the taskbar that shows the list of running programs and allows you to switch between them by clicking on them. I can use alt-tab to switch between windows but I usually have many (8+) windows open and this is not a usable long-term alternative.

Where is the taskbar in Unity? Or do I need to switch back to Classic?

---

### Post by dniMretsaM on 2011-05-01
There is no task bar in Unity. Just the launcher (the number of windows is indicated in the launcher by little triangular marks beside an application). I don't think so anyway, I don't have much experience with Unity. Please correct me if I'm wrong.

---

### Post by ravi_buz on 2011-05-01
> **evouga said:**
> I just upgraded to 11.04 and am getting used to the new layout, but can't figure out where (or how to enable) the taskbar that shows the list of running programs and allows you to switch between them by clicking on them. I can use alt-tab to switch between windows but I usually have many (8+) windows open and this is not a usable long-term alternative.

Where is the taskbar in Unity? Or do I need to switch back to Classic?

Well if u want the Ubuntu the old way, just log out and choose ubuntu classic and log in

---

### Post by Carborundum on 2011-05-01
I'm not sure what you mean by taskbar. I can't remember seeing anything like that in Maverick.

If you want to quickly switch between running programs, there are a number of different strategies. Running programs are marked in the Unity launcher with an arrow, allowing you to quickly identify which are currently open. You can also spread your windows across multiple workspaces for easier navigation of programs with similar functionality,

Are you aware that you can alt+tab backwards using alt+shift+tab?

---

### Post by dniMretsaM on 2011-05-01
There was a task bar in Maverick. It was at the bottom (by default).

---

### Post by Blasphemist on 2011-05-01
It's very helpful to look at Jorge's blog and see quickly some of how you can use unity. It saves a good bit of tracking down how to do things and how it's designed to work.

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

---

### Post by Carborundum on 2011-05-01
> **dniMretsaM said:**
> There was a task bar in Maverick. It was at the bottom (by default).
Odd. As I said, I can't remember it. I suppose I must have removed it a long time ago and then forgotten about it.

That said, surely it was just a plain old gnome panel? Another one can be created alongside Unity by entering the command "gnome-panel" in the terminal. The same command can also be added to Startup Applications.

---

### Post by teachop on 2011-05-01
Yes, the task bar was called "Windows List" in the panel I think.  Try using Super+w for switching between windows and see what you think of that.  I tried putting it on my 3rd mouse button to activate, and it works pretty conveniently.  Not a windows list, but faster than alt-tab, it looks cool, a different way of doing things.

---

### Post by rburkartjo on 2011-05-01
or you could try this

i missed a dock showing the open or min windows. being a power user and using more than one desktop it was a nightmare. the little white arrows on the unity toolbar just didnt cut it for me. so i went to /usr/share/applications and copied panel to the desktop then opened, deleted the top panel so i had just a bottom panel.then added windows list to the panel and added to the startup applications. a lot easier, using atl-tab all the time

---

### Post by akand074 on 2011-05-01
Press "Super + W" to show all applications in all workspaces. Press "Shift + Alt + Up" to show all applications from current workspace (likely able to change these hot keys from Compiz/System Settings if you like).

---

### Post by hektor_555 on 2011-05-02
What if I want to get the "Windows List" at first click? That will work better for me. For example: If I am at the desktop and click one time my firefox launcher, I would like to see the windows list in scaled preview (or listed as a menu maybe), instead of getting that function at second click after it opens all my firefox windows. Is it possible to configure that way?

---

### Post by cgarre on 2011-08-31
I dont think people are understanding the significance of system tray. Even gnome 3 has it ..  I dont have it in 11.10 maybe because it is in alpha now.  There are lot of applications that you can close and still they keep running in the background, for example gnome-do. If you want to see if it is running and access its menu, you can see it in gnome 3, by moving mouse to bottom right corner and a panel will appear. With unity there is nothing like that, and also unity-2d has it on top right, on the left of the icons which show network, volume, mail etc. This is not to know the current running applications, i can do that in n different ways, this is for applications that dont have visiblity in alt-tab, ctrl-w or even the taskbar.

---

