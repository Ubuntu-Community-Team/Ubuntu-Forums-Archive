---
title: "Terminal Question"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Macnemarion on 2011-04-17
I am curious to if there is a way to open another terminal via terminal but have it open behind the terminal that I am working in.

Every time I do gnome-terminal it always opens right on top of where I was working.Usually It is not that big of a deal but I would like to know to use it in a script.

-Mac

---

### Post by scott-ian on 2011-04-17
I don't think that is possible.  You can open it in the background, but then it won't show up at all.

---

### Post by Macnemarion on 2011-04-17
mmm well that is disappointing it's not that big of a deal just wanted to know for the sake of ease of use. Even when I open it with a & it still opens on top of my current terminal. Oh well.

Thanks

-MAC

---

### Post by Dutch70 on 2011-04-17
When I click "File" & select "Open Terminal" it opens right beside of it on mine. 

You can right click anywhere in the terminal and select a "new tab" in the same window.

---

### Post by scott-ian on 2011-04-17
Perhaps there is a way.  If you can then run a command to bring the other terminal to the front.
See this: [http://superuser.com/questions/16647/custom-hotkey-shortcut-to-open-bring-to-front-an-app](http://superuser.com/questions/16647/custom-hotkey-shortcut-to-open-bring-to-front-an-app)

---

### Post by Macnemarion on 2011-04-17
yeah I knew about the tabs , what I am trying to do is write a script that allows you update and then upgrade all in one command which also gives you the option to open another terminal to allow you to continue to work while the upgrade process continues in the other terminal window. When updating you have to sudo and input your password and it is prompting me for my pass right after the other terminal opens right on top of the terminal I am running the script in which happens to be the one that is requesting the password. 

So what is happening is I run the script, if I choose yes that I want another terminal open then it opens and I have to move it select the old one enter the password and then reselect the new one to continue to work.

Granted this is only needed for long updates.

-MAC

---

### Post by DaithiF on 2011-04-19
Hi,
I didn't follow exactly which window you want focused, but in general if you want to create a new window but then give focus back to the one you started from, use xdotool.

```
# get the x-window id of the current window
window_id=$(xdotool getwindowfocus)

# doing other stuff here... maybe opening another terminal, etc...

# now switch focus back to this window
xdotool windowactivate $window_id

```
you may need to add a sleep statement before calling the windowactivate, to give whatever other process you have launched time to launch and get focus before switching focus back.

---

